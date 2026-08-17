# Expo Native Components (Beta)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

The Clerk Expo SDK provides prebuilt native UI components rendered with **SwiftUI** on iOS and **Jetpack Compose** on Android. These components provide a fully native authentication experience for Expo apps.

> These native components are for the iOS and Android surfaces. If you're building for **Expo web**, use Clerk's [UI components](https://clerk.com/docs/expo/reference/components/overview.md#authentication-components) instead.

`<AuthView />` and `<UserProfileView />` render inline in your React Native view hierarchy, so you can place them in a modal, route, full-screen view, or any other layout that fits your app. `<UserButton />` renders the platform-native Clerk button and opens `<UserProfileView />` when tapped.

## Available components

| Component                                                                                            | Description                                        |
| ---------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| [<AuthView />](https://clerk.com/docs/expo/reference/native-components/auth-view.md)                | Full sign-in and sign-up authentication UI         |
| [<UserButton />](https://clerk.com/docs/expo/reference/native-components/user-button.md)            | Circular avatar button that opens the user profile |
| [<UserProfileView />](https://clerk.com/docs/expo/reference/native-components/user-profile-view.md) | Complete profile management interface              |

## Requirements

Native components require:

- Expo SDK 53 or later. See the [quickstart](https://clerk.com/docs/expo/getting-started/quickstart.md) guide.

- A [development build](https://docs.expo.dev/develop/development-builds/introduction/) (`npx expo run:ios` or `npx expo run:android`), as these components are not available in Expo Go.

- The `@clerk/expo` plugin configured in your `app.json` file. See the [available plugin options](https://clerk.com/docs/expo/reference/native-components/overview.md#expo-plugin-options).

  filename: app.json

  ```json
  {
    "expo": {
      "plugins": ["@clerk/expo"]
    }
  }
  ```

- If using social connections, you must register your native application credentials in the Clerk Dashboard. See the [Sign in with Google](https://clerk.com/docs/expo/guides/configure/auth-strategies/sign-in-with-google.md) and [Sign in with Apple](https://clerk.com/docs/expo/guides/configure/auth-strategies/sign-in-with-apple.md) guides for setup steps.

### Expo plugin options

The plugin accepts the following options:

| Name            | Type    | Description                                                                                                                                                                                                                      |
| --------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| appleSignIn     | boolean | Whether to add the com.apple.developer.applesignin entitlement. Set to false if your app does not use Apple Sign In. Defaults to true.                                                                                           |
| keychainService | string  | Custom keychain service identifier. Required if you need extension targets (widgets, App Clips, Watch) to share the keychain with the main app.                                                                                  |
| theme           | string  | Path to a JSON file that customizes the appearance of the native components on iOS and Android (colors, dark mode, border radius, and font family). See the Theming reference for platform-specific details and the full schema. |

#### Example

filename: app.json
```json
{
  "expo": {
    "plugins": [
      [
        "@clerk/expo",
        {
          "appleSignIn": false,
          "keychainService": "com.example.myapp"
        }
      ]
    ]
  }
}
```

## Respond to auth changes

Use hooks like [useAuth()](https://clerk.com/docs/expo/reference/hooks/use-auth.md), [useUser()](https://clerk.com/docs/expo/reference/hooks/use-user.md), or [useSession()](https://clerk.com/docs/expo/reference/hooks/use-session.md) to read authentication state and update your UI after auth changes.

> When using native components, pass `{ treatPendingAsSignedOut: false }` to [useAuth()](https://clerk.com/docs/expo/reference/hooks/use-auth.md) so pending session tasks are not treated as signed out.

The following example demonstrates one way to open [<AuthView />](https://clerk.com/docs/expo/reference/native-components/auth-view.md) from a sign-in button.

> Keep the React Native `<Modal>` that contains `<AuthView />` mounted at the same level as your signed-in and signed-out content. Don't render the modal only inside signed-out content, because auth state can change before required session tasks are finished and unmount the modal too early.

filename: src/app/index.tsx
```tsx
import { AuthView } from '@clerk/expo/native'
import { useAuth, useUser } from '@clerk/expo'
import { useState } from 'react'
import { Button, Modal, Text, View } from 'react-native'

export default function HomeScreen() {
  const { isSignedIn } = useAuth({ treatPendingAsSignedOut: false })
  const { user } = useUser()
  const [isAuthOpen, setIsAuthOpen] = useState(false)

  return (
    <View>
      {isSignedIn ? (
        <Text>User ID: {user?.id}</Text>
      ) : (
        <Button title="Sign in" onPress={() => setIsAuthOpen(true)} />
      )}
      <Modal
        animationType="slide"
        visible={isAuthOpen}
        presentationStyle="pageSheet"
        onRequestClose={() => setIsAuthOpen(false)}
      >
        <AuthView onDismiss={() => setIsAuthOpen(false)} />
      </Modal>
    </View>
  )
}
```

When rendering [<AuthView />](https://clerk.com/docs/expo/reference/native-components/auth-view.md) or [<UserProfileView />](https://clerk.com/docs/expo/reference/native-components/user-profile-view.md) directly in a route or full-screen view, pass `isDismissible={false}` if users must complete the flow to continue.

```tsx
<AuthView isDismissible={false} />
```

```tsx
<UserProfileView isDismissible={false} style={{ flex: 1 }} />
```

## Web compatibility

For Expo web projects, use the web-specific components from `@clerk/expo/web`. Expo Router requires a non-platform route alongside a platform-specific route, so this example includes both files:

```text
src/
└── app/
    ├── sign-in.tsx
    └── sign-in.web.tsx
```

filename: src/app/sign-in.tsx
```tsx
import { AuthView } from '@clerk/expo/native'

export default function Page() {
  return <AuthView isDismissible={false} />
}
```

filename: src/app/sign-in.web.tsx
```tsx
import { SignIn } from '@clerk/expo/web'

export default function Page() {
  return <SignIn />
}
```

`<AuthView />` doesn't navigate on its own — see the [full-screen example](https://clerk.com/docs/expo/reference/native-components/auth-view.md#render-as-a-required-full-screen-view) for redirecting once authentication completes. See the [web component reference](https://clerk.com/docs/expo/reference/components/overview.md#authentication-components) for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
