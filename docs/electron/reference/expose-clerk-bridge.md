# exposeClerkBridge() (Beta)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

`exposeClerkBridge()` exposes the Clerk bridge from the preload script to the renderer. It publishes a narrow bridge that `@clerk/electron/react` uses for token storage and OAuth transport. Call it once, at the top level of your preload script.

## Usage

filename: src/preload.ts
```ts
import { exposeClerkBridge } from '@clerk/electron/preload'

exposeClerkBridge()
```

## Options

| Name      | Type    | Description                                                                                                                           |
| --------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| passkeys? | boolean | Exposes the native passkey bridge to the renderer. Requires createClerkBridge({ passkeys: true }) in the main process. See Passkeys. |

## `webPreferences`

- **`contextIsolation: true`** (Electron's default) is supported and recommended. The bridge is published with `contextBridge.exposeInMainWorld()`. When you turn off `contextIsolation`, Clerk assigns the bridge to `window` instead.
- **`nodeIntegration`** is never required. The renderer only reads the bridge the preload script publishes.
- **`sandbox: true`** works when the preload script is bundled to CommonJS, which Electron Forge's Vite plugin does. The preload only uses `contextBridge`, `ipcRenderer`, and `process.versions`, all of which are available in a sandboxed preload.

## Security

Clerk's main-process IPC handlers only answer requests from a `BrowserWindow`'s main frame. Requests from `<webview>` tags, `BrowserView`s, and iframes are rejected with `Clerk: token-cache request did not originate from a window's main frame.` (or the OAuth and passkey equivalents), even when those contexts load the same preload script. Render Clerk in the top-level document of a `BrowserWindow`.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
