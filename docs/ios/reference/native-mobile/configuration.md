# Configure the SDK

Call `Clerk.configure(publishableKey:options:)` once at app launch before accessing `Clerk.shared` or `@Environment(Clerk.self)`.

## Basic configuration

```swift
import ClerkKit
import SwiftUI

@main
struct MyApp: App {
  init() {
    Clerk.configure(publishableKey: "{{pub_key}}")
  }

  var body: some Scene {
    WindowGroup {
      ContentView()
        .environment(Clerk.shared)
    }
  }
}
```

## Configuration options

Use `Clerk.Options` to customize logging, telemetry, redirects, and more.

```swift
let options = Clerk.Options(
  logLevel: .debug,
  telemetryEnabled: true,
  keychainConfig: .init(
    service: "com.example.shared-auth",
    accessGroup: "ABCDE12345.com.example.shared-auth"
  ),
  proxyUrl: "https://proxy.example.com/__clerk",
  redirectConfig: .init(
    redirectUrl: "myapp://callback",
    callbackUrlScheme: "myapp"
  ),
  watchConnectivityEnabled: true,
  sharedSessionSync: .enabled,
  loggerHandler: { logEntry in
    print("[Clerk] \(logEntry.message)")
  },
  middleware: .init(
    request: [
      CustomHeaderMiddleware()
    ],
    response: [
      ResponseDiagnosticsMiddleware()
    ]
  )
)

Clerk.configure(publishableKey: "{{pub_key}}", options: options)
```

### `Clerk.Options`

| Name                     | Type                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------ | -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| logLevel                 | LogLevel                               | Minimum SDK log level. Defaults to .error.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| telemetryEnabled         | Bool                                   | Enables development telemetry collection. Defaults to true.                                                                                                                                                                                                                                                                                                                                                                                                                |
| keychainConfig           | Clerk.Options.KeychainConfig           | Controls Keychain storage behavior.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| proxyUrl                 | URL?                                   | Proxy URL for apps behind a reverse proxy, e.g., https://proxy.example.com/__clerk.                                                                                                                                                                                                                                                                                                                                                                                     |
| redirectConfig           | Clerk.Options.RedirectConfig           | OAuth redirect URLs and callback handling.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| watchConnectivityEnabled | Bool                                   | Sync auth state to a watchOS companion app. Defaults to false.                                                                                                                                                                                                                                                                                                                                                                                                             |
| sharedSessionSync        | Clerk.Options.SharedSessionSyncConfig? | Enables shared session sync between sibling apps on the same Apple Developer Team that share the same Keychain service and access group. All participating apps must also use the same Clerk Publishable KeyYour Clerk Publishable Key tells your app what your FAPI URL is, enabling your app to locate and communicate with your dedicated FAPI instance. You can find it on the API keys page in the Clerk Dashboard.. Defaults to nil. See Share sessions across apps. |
| loggerHandler            | (@Sendable (LogEntry) -> Void)?        | Callback for error-level SDK logs.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| middleware               | Clerk.Options.MiddlewareConfig         | Configuration for request/response middleware.                                                                                                                                                                                                                                                                                                                                                                                                                             |

### `KeychainConfig`

| Name        | Type    | Description                                                   |
| ----------- | ------- | ------------------------------------------------------------- |
| service     | String  | Keychain service name. Defaults to the app bundle identifier. |
| accessGroup | String? | Access group for Keychain item sharing.                       |

### `RedirectConfig`

| Name              | Type   | Description                                                     |
| ----------------- | ------ | --------------------------------------------------------------- |
| redirectUrl       | String | OAuth redirect URL. Defaults to {bundleIdentifier}://callback. |
| callbackUrlScheme | String | Callback URL scheme. Defaults to the app bundle identifier.     |

### `SharedSessionSyncConfig`

| Name     | Type                                  | Description                                                                                                                      |
| -------- | ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| .enabled | Clerk.Options.SharedSessionSyncConfig | Turns on shared session sync between sibling apps. Requires a Keychain service and access group. See Share sessions across apps. |

### `MiddlewareConfig`

| Name     | Type                       | Description                                                                                                                                          |
| -------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| request  | [ClerkRequestMiddleware]  | Final-step request middleware for custom headers or diagnostics.                                                                                     |
| response | [ClerkResponseMiddleware] | Response middleware that runs immediately after a response is received. Custom response middleware runs before Clerk's built-in response middleware. |

## Next steps

- [Clerk](https://clerk.com/docs/ios/reference/native-mobile/clerk.md): Learn how to access Clerk in your app.
- [iOS Quickstart](https://clerk.com/docs/ios/getting-started/quickstart.md): Follow the end-to-end setup guide for a Clerk-powered iOS app.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
