# Electron Quickstart (Beta)

**Example Repository**

- [Electron Quickstart Repo](https://github.com/clerk/clerk-electron-quickstart)

**Before you start**

- [Set up a Clerk application](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md?sdk=electron)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

This quickstart creates a new Electron app with [Electron Forge](https://www.electronforge.io/), adds React to the renderer, and adds Clerk authentication to it. The Clerk Electron SDK needs Electron 28 or later, Node.js 20.9 or later, and `contextIsolation` enabled (Electron's default); the [SDK reference](https://clerk.com/docs/electron/reference/overview.md#requirements) lists every requirement.

1. ## Enable Native API

   In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page and enable the Native API. This is required to integrate Clerk in your native application or browser extension.

   > Enabling the Native API opens a public request pathway that bypasses browser-based CAPTCHA challenges. Learn more about [how the Native API affects bot protection](https://clerk.com/docs/guides/secure/bot-protection.md?sdk=electron#native-api-and-captcha).
2. ## Allow your app's origin

   The renderer sends every Clerk request with an `Authorization` header and, because it's a browser, an `Origin` header. Clerk's Frontend API only accepts that combination from origins you allowlist on your instance. Add the origin your renderer runs on; in development that's Electron Forge's Vite dev server. You'll add your packaged app's custom scheme when you [configure OAuth deep links](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron). OAuth and SSO sign-in need a packaged app on macOS and Linux, because those platforms only deliver custom-scheme deep links to packaged apps; the guide covers that.

   In your terminal, run the following command; it uses your instance's Secret Key.

   1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page and copy your Secret Key.
   2. In your terminal, run the following command, replacing `YOUR_SECRET_KEY` with it.

   filename: terminal

   ```bash
   curl -X PATCH https://api.clerk.com/v1/instance \
     -H "Authorization: Bearer {{secret}}" \
     -H "Content-type: application/json" \
     -d '{"allowed_origins": ["http://localhost:5173"]}'
   ```

   The command sets the whole list. The [OAuth deep links guide](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron) adds your packaged app's scheme origin alongside the dev server for development, and the [deployment guide](https://clerk.com/docs/electron/guides/development/deployment/electron.md#allow-your-production-origin) allowlists only the scheme origin on your production instance.
3. ## Create a new Electron app

   If you don't already have an Electron app, run the following commands to create one with Electron Forge's Vite + TypeScript template. The template doesn't include React, so the last two commands add it. `@vitejs/plugin-react` is pinned to v4 because the template loads its Vite config as CommonJS, which newer plugin versions no longer support, and `typescript@5` replaces the template's 2021 pin so the `tsconfig.json` settings below are accepted.

   ```npm
   npm --allow-git=all init electron-app@latest clerk-electron-quickstart -- --template=vite-typescript
   cd clerk-electron-quickstart
   npm install react react-dom
   npm install -D @vitejs/plugin-react@4 typescript@5 @types/react @types/react-dom
   ```

   The `--allow-git=all` flag is for npm 12 and later, which block git-hosted dependencies by default; Electron Forge's template installs `@electron/node-gyp` from GitHub. Earlier npm versions ignore the flag.

   > Electron Forge needs extra configuration under `pnpm` (a hoisted node linker and, on `pnpm` 11, allowing Forge's git-hosted dependency and build scripts). This guide uses `npm`; see [Electron Forge's requirements](https://www.electronforge.io/) if you use `pnpm`.

   Then replace the renderer entry with a React root. Rename `src/renderer.ts` to `src/renderer.tsx`, and replace `index.html` with:

   filename: index.html

   ```html
   <!doctype html>
   <html>
     <head>
       <meta charset="UTF-8" />
       <title>Clerk + Electron</title>
     </head>
     <body>
       <div id="root"></div>
       <script type="module" src="/src/renderer.tsx"></script>
     </body>
   </html>
   ```

   Enable JSX in the renderer build by adding the React plugin to `vite.renderer.config.ts`:

   filename: vite.renderer.config.ts

   ```ts
   import react from '@vitejs/plugin-react'
   import { defineConfig } from 'vite'

   export default defineConfig({
     plugins: [react()],
   })
   ```
4. ## Install `@clerk/electron`

   The [Clerk Electron SDK](https://clerk.com/docs/electron/reference/overview.md) gives you access to prebuilt components, hooks, and helpers to make user authentication easier. It stores the session token with [`electron-store`](https://github.com/sindresorhus/electron-store), which is an optional peer dependency. The SDK currently supports `electron-store@8`, so the command pins that version.

   ```npm
   npm install @clerk/electron electron-store@8
   ```

   The SDK publishes its entrypoints through the package `exports` map, which the Forge template's TypeScript settings predate. In `tsconfig.json`, change `module` and `moduleResolution` (the template sets them to `commonjs` and `node`) and add `jsx`; keep the template's other options:

   filename: tsconfig.json

   ```json
   {
     "compilerOptions": {
       "module": "ESNext",
       "moduleResolution": "bundler",
       "jsx": "react-jsx"
     }
   }
   ```
5. ## Set your Clerk API keys

   If you haven't already, create a new Clerk application in the [Clerk Dashboard](https://dashboard.clerk.com/). For more information, see the [setup guide](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md?sdk=electron).

   Add your Clerk Publishable Key to your `.env` file. This key can always be retrieved from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

   1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page.
   2. In the **Quick Copy** section, copy your Clerk Publishable Key.
   3. Paste your key into your `.env` file.

   The final result should resemble the following:

   filename: .env

   ```env
   VITE_CLERK_PUBLISHABLE_KEY={{pub_key}}
   VITE_CLERK_FRONTEND_API_HOST={{fapi_url}}
   ```

   The second value is your instance's Frontend API hostname without `https://`. The Content Security Policy step below adds the protocol automatically.
6. ## Set up the main process

   `createClerkBridge()` registers the inter-process communication (IPC) handlers and token storage that the renderer relies on. Call it before `app.whenReady()` and pass it a storage adapter. When you later configure a `renderer` scheme for OAuth, the bridge also takes Electron's single-instance lock on Windows and Linux, so gate the rest of your bootstrap on `isPrimaryInstance` from the start. See the [createClerkBridge() reference](https://clerk.com/docs/electron/reference/create-clerk-bridge.md) for all options.

   The guard keeps navigation and server-side redirects on your renderer's origin (the Vite dev server here; the [OAuth deep links guide](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron) adds your packaged app's scheme) because a page from another origin would inherit the preload script and Clerk's token cache; external links open in the system browser.

   filename: src/main.ts

   ```ts
   import { createClerkBridge } from '@clerk/electron'
   import { storage } from '@clerk/electron/storage'
   import { app, BrowserWindow, shell } from 'electron'
   import started from 'electron-squirrel-startup'
   import path from 'node:path'

   // Handle creating/removing shortcuts on Windows when installing/uninstalling.
   if (started) {
     app.quit()
   }

   // `new URL(...).origin` is the string 'null' for a non-special scheme like
   // my-app://, so compare on the scheme and host instead.
   const originOf = (url: string) => {
     const parsed = new URL(url)
     return `${parsed.protocol}//${parsed.host}`
   }

   // Registers Clerk's IPC handlers and token storage. Call it before app.whenReady().
   const clerk = createClerkBridge({
     storage: storage(),
   })

   const createWindow = () => {
     const mainWindow = new BrowserWindow({
       width: 1024,
       height: 768,
       webPreferences: {
         preload: path.join(__dirname, 'preload.js'),
       },
     })

     // Keep the Clerk bridge inside this app: navigation to another origin, including a
     // server-side redirect to one, would carry the preload (and the token cache) to a
     // page you do not control.
     const allowedOrigins = new Set(
       [MAIN_WINDOW_VITE_DEV_SERVER_URL]
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
       mainWindow.loadFile(path.join(__dirname, `../renderer/${MAIN_WINDOW_VITE_NAME}/index.html`))
     }
   }

   // On Windows and Linux, Clerk forwards OAuth deep links through Electron's
   // single-instance lock. Skip the bootstrap in the process that is quitting.
   if (clerk.isPrimaryInstance) {
     app.on('ready', createWindow)
   }

   app.on('window-all-closed', () => {
     if (process.platform !== 'darwin') {
       app.quit()
     }
   })

   app.on('activate', () => {
     if (BrowserWindow.getAllWindows().length === 0) {
       createWindow()
     }
   })

   app.on('before-quit', () => {
     clerk.cleanup()
   })
   ```
7. ## Expose the bridge from the preload script

   The preload script publishes a narrow bridge that `@clerk/electron/react` uses for token storage and OAuth transport. It works with `contextIsolation` enabled, which is Electron's default.

   filename: src/preload.ts

   ```ts
   import { exposeClerkBridge } from '@clerk/electron/preload'

   exposeClerkBridge()
   ```
8. ## Add a Content Security Policy

   Clerk loads its prebuilt UI from your instance's Frontend API at runtime, so the renderer's Content Security Policy (CSP) must allow that host. Without it, Clerk's components never render. Replace `index.html` with the following; Vite fills in `%VITE_CLERK_FRONTEND_API_HOST%` from your `.env` file. The `'unsafe-eval'` and `localhost` entries are only needed for Vite's dev server; see the [deployment guide](https://clerk.com/docs/electron/guides/development/deployment/electron.md) for the packaged-build policy.

   filename: index.html

   ```html
   <!doctype html>
   <html>
     <head>
       <meta charset="UTF-8" />
       <meta
         http-equiv="Content-Security-Policy"
         content="default-src 'self'; script-src 'self' 'unsafe-inline' 'unsafe-eval' https://%VITE_CLERK_FRONTEND_API_HOST% https://challenges.cloudflare.com https://*.protect.clerk.com; connect-src 'self' https://%VITE_CLERK_FRONTEND_API_HOST% https://*.protect.clerk.com:* https://clerk-telemetry.com https://*.clerk-telemetry.com ws://localhost:5173 http://localhost:5173; img-src 'self' https://img.clerk.com data:; style-src 'self' 'unsafe-inline'; worker-src 'self' blob:; frame-src 'self' https://challenges.cloudflare.com https://*.protect.clerk.com; form-action 'self';"
       />
       <title>Clerk + Electron</title>
     </head>
     <body>
       <div id="root"></div>
       <script type="module" src="/src/renderer.tsx"></script>
     </body>
   </html>
   ```

   Electron logs a security warning in development because the dev-server policy allows `'unsafe-eval'`; the packaged build's header policy in the deployment guide doesn't.
9. ## Add `<ClerkProvider>` to your app

   The [<ClerkProvider>](https://clerk.com/docs/electron/reference/components/clerk-provider.md) component provides session and user context to Clerk's hooks and components. It's recommended to wrap your entire app at the entry point with `<ClerkProvider>` to make authentication globally accessible. See the [reference docs](https://clerk.com/docs/electron/reference/components/clerk-provider.md) for other configuration options.

   TypeScript needs Vite's client types for `import.meta.env`; add this line to `forge.env.d.ts`:

   filename: forge.env.d.ts

   ```ts
   /// <reference types="@electron-forge/plugin-vite/forge-vite-env" />
   /// <reference types="vite/client" />
   ```

   Render your app inside `<ClerkProvider>`. Import it from `@clerk/electron/react`; it configures Clerk for Electron and re-exports everything from `@clerk/react`.

   filename: src/renderer.tsx

   ```tsx
   import { ClerkProvider } from '@clerk/electron/react'
   import { StrictMode } from 'react'
   import { createRoot } from 'react-dom/client'
   import App from './App'
   import './index.css'

   const PUBLISHABLE_KEY = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

   if (!PUBLISHABLE_KEY) {
     throw new Error('Add your Clerk Publishable Key to the .env file')
   }

   createRoot(document.getElementById('root')!).render(
     <StrictMode>
       <ClerkProvider publishableKey={PUBLISHABLE_KEY}>
         <App />
       </ClerkProvider>
     </StrictMode>,
   )
   ```
10. ## Create a header with Clerk components

    You can control which content signed-in and signed-out users can see with the [prebuilt control components](https://clerk.com/docs/electron/reference/components/overview.md#control-components). The following example creates a header using the following components:

    - [<Show when="signed-out">](https://clerk.com/docs/electron/reference/components/control/show.md): Children of this component can only be seen while **signed out**.
    - [<Show when="signed-in">](https://clerk.com/docs/electron/reference/components/control/show.md): Children of this component can only be seen while **signed in**.
    - [<SignInButton mode="modal" />](https://clerk.com/docs/electron/reference/components/unstyled/sign-in-button.md) and [<SignUpButton mode="modal" />](https://clerk.com/docs/electron/reference/components/unstyled/sign-up-button.md): Unstyled components that open Clerk's sign-in and sign-up flows in a modal inside your window.
    - [<UserButton />](https://clerk.com/docs/electron/reference/components/user/user-button.md): Shows the signed-in user's avatar. Selecting it opens a dropdown menu with account management options.

    Without `mode="modal"`, the buttons link to the [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md?sdk=electron), which would navigate the renderer away from your app.

    filename: src/App.tsx

    ```tsx
    import { Show, SignInButton, SignUpButton, UserButton } from '@clerk/electron/react'

    export default function App() {
      return (
        <>
          <header>
            <Show when="signed-out">
              <SignInButton mode="modal" />
              <SignUpButton mode="modal" />
            </Show>
            <Show when="signed-in">
              <UserButton />
            </Show>
          </header>
          <main>
            <h1>Clerk + Electron</h1>
          </main>
        </>
      )
    }
    ```
11. ## Run your project

    ```npm
    npm start
    ```
12. ## Create your first user

    Select **Sign up** in the window that opens and create an account with a non-OAuth method, such as an email code or password. Social and SSO options require a packaged app and the additional setup in [Configure OAuth and SSO deep links](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron).

    Quit and start the app again to confirm the session persists: the token is encrypted with Electron's `safeStorage` and restored on launch. Packaged macOS builds need a code-signing identity for that persistence to work; see the [deployment guide](https://clerk.com/docs/electron/guides/development/deployment/electron.md#package-and-sign).

## Next steps

Explore the most relevant next steps for your SDK using the following guides.

- [Configure OAuth deep links](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron): Learn how OAuth and SSO return to your packaged app through a custom scheme.
- [Configure passkeys](https://clerk.com/docs/electron/reference/passkeys.md): Learn how passkeys work in the renderer and natively on macOS and Windows.
- [Deploy an Electron app to production](https://clerk.com/docs/guides/development/deployment/electron.md?sdk=electron): Learn how to package your app with production keys and a Content Security Policy.
- [Clerk Electron SDK reference](https://clerk.com/docs/electron/reference/overview.md): Learn what the SDK supports and how its main, preload, and renderer pieces fit together.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
