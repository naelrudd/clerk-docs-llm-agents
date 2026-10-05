# Deploy an Electron app to production (Beta)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

This guide is written for Electron Forge, but the steps apply to any packaging tool. Adapt the file names and configuration to yours.

## Create a production instance

In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page and enable the Native API. This is required to integrate Clerk in your native application or browser extension.

> Enabling the Native API opens a public request pathway that bypasses browser-based CAPTCHA challenges. Learn more about [how the Native API affects bot protection](https://clerk.com/docs/guides/secure/bot-protection.md#native-api-and-captcha).

A Clerk production instance needs a domain even when your Electron app has no website: the production Frontend API is served from `clerk.<your-domain>`, and that is the host your app talks to. Follow the [guide on deploying your Clerk app to production](https://clerk.com/docs/guides/development/deployment/production.md).

## Set your production Publishable Key

In the Clerk Dashboard, select your production instance from the instance dropdown at the top of the page. Then:

Add your Clerk Publishable Key to your `.env` file. This key can always be retrieved from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page.
2. In the **Quick Copy** section, copy your Clerk Publishable Key.
3. Paste your key into your `.env` file.

The final result should resemble the following:

filename: .env.production
```env
VITE_CLERK_PUBLISHABLE_KEY={{pub_key}}
VITE_CLERK_FRONTEND_API_HOST={{fapi_url}}
```

Use `.env.production` rather than `.env`: Vite reads it for packaged builds, so your development key stays in `.env`. Vite inlines `VITE_`-prefixed variables at build time, so both values are baked into the packaged app. Never add `CLERK_SECRET_KEY` to an Electron project.

## Allow your production origin

Repeat the `allowed_origins` step from the [OAuth deep links guide](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md) against your **production** instance with its production Secret Key. List your scheme origin (for example, `my-app://renderer`), and leave the dev-server origin out of production.

## Serve the renderer from a custom scheme

OAuth and SSO callbacks return to a custom scheme, and Clerk doesn't treat `file://` as a valid redirect origin. Follow [Configure OAuth deep links](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md) to register the scheme with `createClerkBridge()`, serve the packaged renderer with `protocol.handle()`, and declare the scheme in `forge.config.ts`.

## Set a production Content Security Policy

The [quickstart's](https://clerk.com/docs/electron/getting-started/quickstart.md#add-a-content-security-policy) `<meta>` policy includes `'unsafe-eval'` and the Vite dev server for hot reloading. For packaged builds, set the policy as a response header from the main process, without those entries. The policy is built from your production instance's Frontend API host.

filename: src/main.ts
```ts
import { app, session } from 'electron'

const FAPI_HOST = import.meta.env.VITE_CLERK_FRONTEND_API_HOST

if (!FAPI_HOST) {
  throw new Error('Add VITE_CLERK_FRONTEND_API_HOST to the .env file')
}

// Packaged builds: the CSP comes from a response header on the renderer's own origin,
// without the dev-server allowances the index.html meta tag carries.
const applyContentSecurityPolicy = () => {
  session.defaultSession.webRequest.onHeadersReceived(
    { urls: [`${RENDERER_SCHEME}://${RENDERER_HOST}/*`] },
    (details, callback) => {
      if (details.resourceType !== 'mainFrame') {
        callback({ responseHeaders: details.responseHeaders })
        return
      }
      callback({
        responseHeaders: {
          ...details.responseHeaders,
          'Content-Security-Policy': [
            [
              "default-src 'self'",
              `script-src 'self' 'unsafe-inline' https://${FAPI_HOST} https://challenges.cloudflare.com https://*.protect.clerk.com`,
              `connect-src 'self' https://${FAPI_HOST} https://*.protect.clerk.com:* https://clerk-telemetry.com https://*.clerk-telemetry.com`,
              "img-src 'self' https://img.clerk.com data:",
              "style-src 'self' 'unsafe-inline'",
              "worker-src 'self' blob:",
              "frame-src 'self' https://challenges.cloudflare.com https://*.protect.clerk.com",
              "form-action 'self'",
            ].join('; '),
          ],
        },
      })
    },
  )
}

if (clerk.isPrimaryInstance) {
  app.on('ready', () => {
    if (!MAIN_WINDOW_VITE_DEV_SERVER_URL) {
      registerRendererProtocol()
      applyContentSecurityPolicy()
    }
    createWindow()
  })
}
```

Set `VITE_CLERK_FRONTEND_API_HOST` in `.env.production` to your production instance's hostname without `https://`. Register the listener in the same `ready` handler that registers the scheme and creates the window, before `createWindow()`, so the first navigation already carries the header. The `urls` filter limits it to your renderer's origin, and the `resourceType` check applies it to the main document only. Electron keeps only the last listener attached to a `webRequest` event, so if your app already calls `onHeadersReceived()`, merge this header into that listener instead of registering a second one.

If you use Clerk Billing or other features that load additional origins, add them per the [CSP guide](https://clerk.com/docs/guides/secure/best-practices/csp-headers.md).

## Package and sign

```npm
npm run make
```

The Electron Forge template's Fuses configuration needs no Clerk-specific changes. Sign and notarize the macOS build for distribution.

Signing is also what keeps users signed in across launches. `@clerk/electron/storage` encrypts the session token with Electron's `safeStorage`, which on macOS needs a Keychain entry tied to the app's signing identity. An unsigned or ad-hoc-signed package (what `npm run package` produces by default) logs `Keychain lookup failed` followed by `Clerk: failed to securely persist a token; it will only be available until the app exits.`, and the app starts signed out after every relaunch even though sign-in worked.

Configure `osxSign` (and `osxNotarize` for distribution) in `forge.config.ts` with your Developer ID; [native passkeys](https://clerk.com/docs/electron/reference/passkeys.md) require the same identity. Windows and Linux builds need no Clerk-specific signing steps.

## Identify your app in session activity

Pass `userAgent` to `createClerkBridge()` so sessions created by your app show its name and version on the user's [session activity](https://clerk.com/docs/reference/components/user/user-profile.md) list:

filename: src/main.ts
```ts
createClerkBridge({
  storage: storage(),
  renderer: { scheme: 'my-app', host: 'renderer' },
  userAgent: `My App/${app.getVersion()}`,
})
```

## Handle single-instance behavior on Windows and Linux

When `renderer` is set, Clerk takes Electron's single-instance lock on Windows and Linux so OAuth callbacks reach the running app. If your app relies on multiple instances, see [single-instance behavior](https://clerk.com/docs/electron/reference/create-clerk-bridge.md#single-instance-behavior-on-windows-and-linux) before shipping.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
