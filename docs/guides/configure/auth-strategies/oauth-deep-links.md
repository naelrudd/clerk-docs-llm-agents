# Configure OAuth and SSO deep links for Electron (Beta)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

In an Electron app, Clerk completes OAuth and SSO sign-in by opening the provider in the user's system browser and receiving the callback through a deep link on a custom scheme that your app registers. In this guide, you'll configure that round trip.

> On macOS and Linux, custom-scheme deep links only reach a **packaged** app. They don't work when you start the app with `npm start`. Test OAuth with `npm run package`.

1. ## Register a custom scheme with the bridge

   Pass `renderer` to [createClerkBridge()](https://clerk.com/docs/electron/reference/create-clerk-bridge.md). `scheme` is a bare scheme name and `host` is a bare host name; together they form the scheme origin your renderer is served from, and `scheme://host/` is the redirect URL Clerk sends to the provider.

   filename: src/main.ts

   ```ts
   import { createClerkBridge } from '@clerk/electron'
   import { storage } from '@clerk/electron/storage'

   const RENDERER_SCHEME = 'my-app'
   const RENDERER_HOST = 'renderer'

   const clerk = createClerkBridge({
     storage: storage(),
     renderer: { scheme: RENDERER_SCHEME, host: RENDERER_HOST },
   })
   ```
2. ## Serve the packaged renderer from the scheme

   Electron Forge's template loads the packaged renderer with `loadFile()`, which gives it a `file://` origin. Clerk doesn't treat `file://` as a valid redirect origin, so serve the built renderer from your scheme with `protocol.handle()` instead, and keep using Vite's dev server during development.

   The window also refuses to navigate or follow a redirect away from your renderer's origin: a page from another origin would inherit the preload script and, with it, Clerk's token cache. External links open in the system browser instead.

   filename: src/main.ts

   ```ts
   import { app, BrowserWindow, net, protocol, shell } from 'electron'
   import path from 'node:path'
   import { pathToFileURL } from 'node:url'

   // `new URL(...).origin` is the string 'null' for a non-special scheme like
   // my-app://, so compare on the scheme and host instead.
   const originOf = (url: string) => {
     const parsed = new URL(url)
     return `${parsed.protocol}//${parsed.host}`
   }

   const rendererRoot = path.join(__dirname, `../renderer/${MAIN_WINDOW_VITE_NAME}`)

   // Packaged builds: serve the Vite output from the custom scheme instead of file://.
   const registerRendererProtocol = () => {
     protocol.handle(RENDERER_SCHEME, async (request) => {
       const url = new URL(request.url)
       if (url.host !== RENDERER_HOST) {
         return new Response('Not found', { status: 404 })
       }
       let requestedPath: string
       try {
         requestedPath = decodeURIComponent(url.pathname)
       } catch {
         return new Response('Bad request', { status: 400 })
       }
       const resolvedPath = path.resolve(rendererRoot, `.${requestedPath}`)
       const relativePath = path.relative(rendererRoot, resolvedPath)
       if (relativePath.startsWith('..') || path.isAbsolute(relativePath)) {
         return new Response('Forbidden', { status: 403 })
       }
       const hasExtension = /\.[^/]+$/.test(url.pathname)
       const filePath = hasExtension ? resolvedPath : path.join(rendererRoot, 'index.html')
       return net.fetch(pathToFileURL(filePath).toString())
     })
   }

   const createWindow = () => {
     const mainWindow = new BrowserWindow({
       width: 800,
       height: 600,
       webPreferences: {
         preload: path.join(__dirname, 'preload.js'),
       },
     })

     // Keep the Clerk bridge inside this app: navigation to another origin, including a
     // server-side redirect to one, would carry the preload (and the token cache) to a
     // page you do not control.
     const allowedOrigins = new Set(
       [MAIN_WINDOW_VITE_DEV_SERVER_URL, `${RENDERER_SCHEME}://${RENDERER_HOST}`]
         .filter((value): value is string => Boolean(value))
         .map(originOf),
     )

     mainWindow.webContents.on('will-navigate', (event, url) => {
       if (!allowedOrigins.has(originOf(url))) {
         event.preventDefault()
         if (url.startsWith('https://') || url.startsWith('http://')) {
           void shell.openExternal(url)
         }
       }
     })

     mainWindow.webContents.on('will-redirect', (event, url) => {
       if (event.isMainFrame && !allowedOrigins.has(originOf(url))) {
         event.preventDefault()
       }
     })

     mainWindow.webContents.setWindowOpenHandler(({ url }) => {
       if (url.startsWith('https://') || url.startsWith('http://')) {
         void shell.openExternal(url)
       }
       return { action: 'deny' }
     })

     if (MAIN_WINDOW_VITE_DEV_SERVER_URL) {
       mainWindow.loadURL(MAIN_WINDOW_VITE_DEV_SERVER_URL)
     } else {
       mainWindow.loadURL(`${RENDERER_SCHEME}://${RENDERER_HOST}/`)
     }
   }

   if (clerk.isPrimaryInstance) {
     app.on('ready', () => {
       if (!MAIN_WINDOW_VITE_DEV_SERVER_URL) {
         registerRendererProtocol()
       }
       createWindow()
     })
   }
   ```

   The handler rejects paths outside the renderer directory and falls back to `index.html` for extensionless paths, so client-side routing keeps working.
3. ## Register the scheme with the operating system

   Windows registers the scheme at runtime. macOS reads it from the app's `Info.plist` and Linux from the `.desktop` entry, both of which Electron Forge writes when you package. Add the scheme to `forge.config.ts`:

   filename: forge.config.ts

   ```ts
   const config: ForgeConfig = {
     packagerConfig: {
       asar: true,
       protocols: [{ name: 'My App', schemes: ['my-app'] }],
     },
     makers: [
       new MakerSquirrel({}),
       new MakerZIP({}, ['darwin']),
       new MakerRpm({ options: { mimeType: ['x-scheme-handler/my-app'] } }),
       new MakerDeb({ options: { mimeType: ['x-scheme-handler/my-app'] } }),
     ],
     // ...
   }
   ```

   If you package with another tool, register `my-app` in `Info.plist` under `CFBundleURLTypes`, and in the Linux `.desktop` file with `Exec=/path/to/my-app %U` and `MimeType=x-scheme-handler/my-app;`.
4. ## Allow the scheme origin and allowlist the redirect URL

   The packaged renderer runs on `my-app://renderer`, so add that origin to your instance's `allowed_origins` (the quickstart added the dev-server origin the same way):

   filename: terminal

   ```bash
   curl -X PATCH https://api.clerk.com/v1/instance \
     -H "Authorization: Bearer {{secret}}" \
     -H "Content-type: application/json" \
     -d '{"allowed_origins": ["http://localhost:5173", "my-app://renderer"]}'
   ```

   Clerk ensures that security critical nonces are passed only to allowlisted URLs when the SSO flow is completed in native browsers or webviews. For maximum security in your **production** instances, you need to allowlist your custom redirect URLs via the [Clerk Dashboard](https://dashboard.clerk.com/) or the [Clerk Backend API](https://clerk.com/docs/reference/backend/redirect-urls/create-redirect-url.md).

   To allowlist a redirect URL via the Clerk Dashboard:

   1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page.
   2. Scroll down to the **Allowlist for mobile SSO redirect** section and add your redirect URLs.

   For an Electron app, the redirect URL is your scheme origin with a trailing slash, for example `my-app://renderer/`.
5. ## Test the flow

   ```npm
   npm run package
   ```

   Launch the packaged app from the `out/` directory, select a social provider in the sign-in modal, and complete sign-in in the browser. The operating system switches back to your app, which finishes the sign-in and focuses its window.

## How it works

1. When the user selects a provider, Clerk asks the main process for the redirect URL (`scheme://host/`) and opens the provider's page with `shell.openExternal()`.
2. The provider redirects to Clerk, and Clerk redirects to the deep link.
3. On macOS, the running app receives it through `open-url`. On Windows and Linux, the deep link starts a second copy of the app; Clerk forwards its arguments to the running copy through Electron's single-instance lock and quits the new one. See [single-instance behavior](https://clerk.com/docs/electron/reference/create-clerk-bridge.md#single-instance-behavior-on-windows-and-linux).
4. The main process resolves the pending sign-in, and Clerk reloads the client in the renderer. Your app is signed in without a page navigation.

## Limits

- One OAuth flow can be pending at a time. Starting another rejects with `Clerk: an OAuth flow is already pending.`
- A flow that receives no callback within three minutes rejects with `Clerk: OAuth callback timed out.`
- The callback always lands on `scheme://host/`. Navigate the user to their destination in the renderer after sign-in.
- Without `renderer`, OAuth sign-in fails at runtime because the main process has no transport to answer the renderer's request.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
