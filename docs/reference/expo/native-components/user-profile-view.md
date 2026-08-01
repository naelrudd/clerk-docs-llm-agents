# <UserProfileView /> component

> This documents the native `<UserProfileView />` from `@clerk/expo/native`. For web projects, use the [web <UserProfile /> component](https://clerk.com/docs/reference/components/user/user-profile.md).

| iOS                                                                                                                                                                                                                                                                                                   | Android                                                                                                                                                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![The UserProfileView renders a comprehensive user profile interface that displays user information and provides account management options on iOS.](https://clerk.com/docs/raw/_public/images/ui-components/ios-user-profile-view.png){{ width: 303, height: 590, style: { objectFit: 'contain' } }} | ![The UserProfileView renders a comprehensive user profile interface that displays user information and provides account management options on Android.](https://clerk.com/docs/raw/_public/images/ui-components/android-user-profile-view.png){{ width: 303, height: 590, style: { objectFit: 'contain' } }} |

The `<UserProfileView />` component renders a fully native profile management interface using SwiftUI on iOS and Jetpack Compose on Android. It allows users to manage:

- Profile details
- Email addresses
- Phone numbers
- Multi-factor authentication (MFA)
- Passkeys
- Connected accounts
- Active sessions

> Before using this component, ensure you meet the [Expo requirements](https://clerk.com/docs/reference/expo/native-components/overview.md#requirements).

## Usage

The `<UserProfileView />` renders inline in your React Native view hierarchy, so you can place it in a modal, sheet, route, full-screen view, or any other layout that fits your app.

**Modal**

The following example demonstrates one way to render `<UserProfileView />` inside a React Native `<Modal>`. The native dismiss button is shown by default. Use `onDismiss` to close the modal in React Native state.

filename: src/app/(home)/index.tsx
```tsx
import { UserProfileView } from '@clerk/expo/native'
import { useState } from 'react'
import { Button, Modal, StyleSheet, View } from 'react-native'

export default function HomeScreen() {
  const [isAuthOpen, setIsAuthOpen] = useState(false)

  return (
    <View style={styles.container}>
      <Button title="Account" onPress={() => setIsAuthOpen(true)} />
      <Modal
        animationType="slide"
        visible={isAuthOpen}
        presentationStyle="pageSheet"
        onRequestClose={() => setIsAuthOpen(false)}
      >
        <UserProfileView onDismiss={() => setIsAuthOpen(false)} />
      </Modal>
    </View>
  )
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
})
```

**Full-screen view**

When rendering `<UserProfileView />` directly in a full-screen view, pass `isDismissible={false}` if users shouldn't be able to dismiss the view.

> When using native components, pass `{ treatPendingAsSignedOut: false }` to [useAuth()](https://clerk.com/docs/reference/hooks/use-auth.md) so pending session tasks are not treated as signed out.

filename: src/app/(home)/profile.tsx
```tsx
import { UserProfileView } from '@clerk/expo/native'
import { useAuth } from '@clerk/expo'
import { useRouter } from 'expo-router'
import { useEffect } from 'react'

export default function ProfileScreen() {
  const { isLoaded, isSignedIn } = useAuth({ treatPendingAsSignedOut: false })
  const router = useRouter()

  useEffect(() => {
    if (isLoaded && !isSignedIn) {
      router.replace('/(auth)/sign-in')
    }
  }, [isLoaded, isSignedIn, router])

  return <UserProfileView isDismissible={false} style={{ flex: 1 }} />
}
```

**Navigation stack**

To push `<UserProfileView />` onto your app's navigation stack, hide the route's header and pass `onHostBack`. The component keeps its native header, so its screen titles, back buttons, swipe-back gestures, and transitions remain native.

Passing `onHostBack` shows a back button on the component's first screen, where it has no screen of its own to return to. The callback runs when the button is tapped. Pop your route in response.

filename: src/app/(home)/profile.tsx
```tsx
import { UserProfileView } from '@clerk/expo/native'
import { Stack, useRouter } from 'expo-router'

export default function ProfileScreen() {
  const router = useRouter()

  return (
    <>
      <Stack.Screen options={{ headerShown: false }} />
      <UserProfileView isDismissible={false} onHostBack={() => router.back()} style={{ flex: 1 }} />
    </>
  )
}
```

The component never leaves the route on its own, so use [useAuth()](https://clerk.com/docs/reference/hooks/use-auth.md), [useUser()](https://clerk.com/docs/reference/hooks/use-user.md), or [useSession()](https://clerk.com/docs/reference/hooks/use-session.md) to react when the user signs out.

> When using native components, pass `{ treatPendingAsSignedOut: false }` to [useAuth()](https://clerk.com/docs/reference/hooks/use-auth.md) so pending session tasks are not treated as signed out.

## Properties

| Name          | Type                  | Description                                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isDismissible | boolean               | Whether the profile view can be dismissed by the user. When true, a dismiss button appears in the native navigation bar. When false, no dismiss button is shown. Defaults to true.                                                                                                                                            |
| onDismiss     | () => void            | A callback that runs when the user dismisses the native profile view. Use this to update your app's presentation state, such as closing a React Native <Modal>.                                                                                                                                                              |
| onHostBack    | () => void            | A callback that runs when the user taps the back button on the profile view's first screen. Passing the callback adds this button. Use it when the component fills a route whose header is hidden, and pop your route in response. The component keeps its native header, so navigation inside the profile view stays native. |
| style         | StyleProp<ViewStyle> | Style applied to the container view.                                                                                                                                                                                                                                                                                          |

## Platform support

| Platform | Status                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------- |
| iOS      | Supported (SwiftUI)                                                                                             |
| Android  | Supported (Jetpack Compose)                                                                                     |
| Web      | Use [<UserProfile />](https://clerk.com/docs/reference/components/user/user-profile.md) from `@clerk/expo/web` |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
