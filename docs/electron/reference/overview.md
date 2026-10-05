# Clerk Electron SDK (Beta)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

The Clerk Electron SDK gives you access to Clerk's [prebuilt components](https://clerk.com/docs/electron/reference/components/overview.md), [React hooks](https://clerk.com/docs/electron/reference/hooks/overview.md), and helpers inside an Electron app. Refer to the [quickstart](https://clerk.com/docs/electron/getting-started/quickstart.md) to get started.

Patch releases can still change behavior; check the [changelog](https://github.com/clerk/javascript/blob/main/packages/electron/CHANGELOG.md) when you upgrade.

## How the SDK fits Electron's process model

Electron runs your app in separate processes, and the SDK ships one entrypoint for each. Install `@clerk/electron` and the `electron-store@8` peer dependency used by the default storage adapter, then import from the entrypoint that matches the process.

```npm
npm install @clerk/electron electron-store@8
```

| Process  | Entrypoint                 | What you use                                                                                                                                                                                    |
| -------- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Main     | `@clerk/electron`          | [createClerkBridge()](https://clerk.com/docs/electron/reference/create-clerk-bridge.md) registers inter-process communication (IPC) handlers, token storage, and the OAuth deep-link transport. |
| Main     | `@clerk/electron/storage`  | [storage()](https://clerk.com/docs/electron/reference/storage.md) persists the session token, encrypted with Electron's `safeStorage`.                                                          |
| Preload  | `@clerk/electron/preload`  | [exposeClerkBridge()](https://clerk.com/docs/electron/reference/expose-clerk-bridge.md) publishes the bridge to the renderer.                                                                   |
| Renderer | `@clerk/electron/react`    | [<ClerkProvider>](https://clerk.com/docs/electron/reference/components/clerk-provider.md) plus everything `@clerk/react` exports.                                                              |
| Renderer | `@clerk/electron/passkeys` | [Passkey support](https://clerk.com/docs/electron/reference/passkeys.md) for the `passkeys` prop.                                                                                               |

Clerk loads its prebuilt UI from your instance's Frontend API at runtime rather than from your app's bundle, so the renderer's Content Security Policy (CSP) must allow that host, and the components don't render while the app is offline.

## Authentication options

Some sign-in methods depend on how the app is running. In development, Electron Forge serves the renderer from Vite's dev server. In a packaged app, the renderer is served from your custom scheme (for example, `my-app://renderer`), which is what OAuth and SSO callbacks return to. See [Configure OAuth deep links](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron).

|                     | Development                                                                                                            | Packaged app              |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| Email + OTP         | Supported                                                                                                              | Supported                 |
| Email + Password    | Supported                                                                                                              | Supported                 |
| Username + Password | Supported                                                                                                              | Supported                 |
| SMS + OTP           | Not verified                                                                                                           | Not verified              |
| Passkeys            | Renderer mode not supported (needs an `https://` origin matching your relying party (RP) ID); native mode not verified | Native mode, not verified |
| OAuth               | Not supported                                                                                                          | Supported                 |
| SAML                | Not supported                                                                                                          | Not verified              |
| Email links         | Not supported                                                                                                          | Not supported             |
| Google One Tap      | Not supported                                                                                                          | Not supported             |
| Web3                | Not supported                                                                                                          | Not supported             |

"Not verified" means the method hasn't been exercised with the Electron SDK yet. SMS + OTP and SAML use the same transports as Email + OTP and OAuth respectively. If you rely on one of these, test it in your app and [contact support](https://clerk.com/contact/support) with feedback.

Passkeys in a local bundle or on the dev server need native mode, a separate implementation (an IPC bridge to the OS through the optional native module) with its own requirements. The renderer's built-in WebAuthn only works when the window loads `https://` content on an origin that matches your instance's RP ID. See [Configure passkeys](https://clerk.com/docs/electron/reference/passkeys.md).

Email links open in the user's browser, not in your app, so they can't complete a sign-in that started in Electron. Google One Tap requires a web origin that Google recognizes, and Web3 requires a wallet injected into the page; neither exists in an Electron renderer.

## What the SDK doesn't include

- **Server-side helpers.** There's no `auth()`, `clerkMiddleware()`, or Backend API client. The main process stores tokens and talks to the OS; it isn't a server. Call your own backend, and verify Clerk session tokens there with the [Backend SDK](https://clerk.com/docs/reference/backend/overview.md?sdk=electron).
- **Non-React renderers.** The only renderer integration is `@clerk/electron/react`. A plain `@clerk/clerk-js` instance works for [passkeys](https://clerk.com/docs/electron/reference/passkeys.md#use-passkeys-without-clerkprovider), but is otherwise undocumented.
- **Bundled UI.** The `ui` prop isn't accepted; the UI always loads from your Frontend API host.

## Requirements

- Electron 28 or later and Node.js 20.9 or later.
- `contextIsolation` enabled (Electron's default). `nodeIntegration` is never required in the renderer.
- Clerk's IPC only answers a `BrowserWindow`'s main frame. `<webview>` tags, `BrowserView`s, and iframes can't use Clerk even if they load the preload script.
- The Native API enabled on your instance. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page. Every origin your renderer runs on (the dev server, your custom scheme) must also be in the instance's `allowed_origins`. Requests that carry both an `Origin` and an `Authorization` header are rejected from other origins.

## Frequently asked questions (FAQ)

### Why does OAuth open the system browser?

The renderer runs on a custom scheme rather than a web origin, so a same-window redirect can't complete the provider's flow. The SDK opens the provider in the system browser and receives the callback through a deep link, the same pattern Clerk's mobile SDKs use. This is why OAuth needs a [packaged app](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron) on macOS and Linux.

### Why did my app become single-instance on Windows and Linux?

On those platforms a deep link starts a second copy of the app. `createClerkBridge()` takes Electron's single-instance lock so the callback reaches the copy that's already running, then quits the new one. Pass `manageSingleInstanceLock: false` if your app already holds the lock; see [createClerkBridge()](https://clerk.com/docs/electron/reference/create-clerk-bridge.md).

### Why does every request fail with "Setting both the 'Origin' and 'Authorization' headers is forbidden"?

Your renderer's origin isn't in the instance's `allowed_origins`. Add the dev-server origin (`http://localhost:5173` with Electron Forge) and your packaged app's scheme origin (`my-app://renderer`) with the Backend API as shown in the [quickstart](https://clerk.com/docs/electron/getting-started/quickstart.md#allow-your-apps-origin) and the [OAuth deep links guide](https://clerk.com/docs/guides/configure/auth-strategies/oauth-deep-links.md?sdk=electron).

### Why does my packaged app start signed out after every relaunch?

Electron's `safeStorage` couldn't use OS-level encryption, so the SDK kept the session token in memory only. On macOS, a common cause is an unsigned or ad-hoc-signed packaged app; on Linux, the machine might not have a keyring. See the [storage() behavior](https://clerk.com/docs/electron/reference/storage.md#behavior), and [package and sign your app](https://clerk.com/docs/electron/guides/development/deployment/electron.md#package-and-sign) on macOS.

### Why do Clerk's components fail to load?

Almost always a CSP that doesn't allow your Frontend API host in `script-src`. The renderer console shows:

```text
Clerk: Failed to load Clerk UI from the CDN. Ensure your Content Security Policy allows the Clerk Frontend API host in `script-src`. Contact support@clerk.com.
```

See the [quickstart's CSP step](https://clerk.com/docs/electron/getting-started/quickstart.md#add-a-content-security-policy).

### Is my Secret Key bundled into the app?

No. The app ships only your Publishable Key and Frontend API host, and both are public by design. Your Secret Key is used once, from your own machine, to allowlist the renderer's origin, and it never belongs in the renderer or the main process. Anything that needs the Secret Key, such as calling the Backend API, belongs on a server your app talks to.

### Can a page loaded in my window reach the Clerk bridge?

Only if you let it. The preload script runs in every document the window loads, so a page from another origin would inherit the bridge and Clerk's token cache. The quickstart's [navigation guard](https://clerk.com/docs/electron/getting-started/quickstart.md#set-up-the-main-process) keeps the window on your renderer's origin and opens every other link in the system browser. Keep it in place.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
