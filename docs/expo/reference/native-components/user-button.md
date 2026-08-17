# <UserButton />

> This documents the native `<UserButton />` from `@clerk/expo/native`. For web projects, use the [web <UserButton /> component](https://clerk.com/docs/expo/reference/components/user/user-button.md).

| iOS                                                                                                                                                                                                                                       | Android                                                                                                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![The UserButton is a circular button that displays the signed-in user's profile image on iOS.](https://clerk.com/docs/raw/_public/images/ui-components/ios-user-button.png){{ width: 320, height: 98, style: { objectFit: 'contain' } }} | ![The UserButton is a circular button that displays the signed-in user's profile image on Android.](https://clerk.com/docs/raw/_public/images/ui-components/android-user-button.png){{ width: 320, height: 98, style: { objectFit: 'contain' } }} |

The `<UserButton />` component renders the platform-native Clerk user button. It displays the user's profile image or initials, and when tapped, it opens [<UserProfileView />](https://clerk.com/docs/expo/reference/native-components/user-profile-view.md).

## Requirements

> Before using this component, ensure you meet the [Expo requirements](https://clerk.com/docs/expo/reference/native-components/overview.md#requirements).

In addition to these requirements, this component requires the user to be signed in. The following example demonstrates how to use the [<Show>](https://clerk.com/docs/expo/reference/components/control/show.md) component to check if the user is signed in and render the `<UserButton />` or a **Sign in** button accordingly.

> Keep the React Native `<Modal>` that contains `<AuthView />` mounted at the same level as your signed-in and signed-out content. Don't render the modal only inside signed-out content, because auth state can change before required session tasks are finished and unmount the modal too early.

filename: src/app/(home)/index.tsx
```tsx
import { Show } from '@clerk/expo'
import { AuthView, UserButton } from '@clerk/expo/native'
import { useState } from 'react'
import { Button, Modal, StyleSheet, View } from 'react-native'

export default function Screen() {
  const [isAuthOpen, setIsAuthOpen] = useState(false)

  return (
    <View style={styles.container}>
      <Show when="signed-in">
        <UserButton />
      </Show>
      <Show when="signed-out">
        <Button title="Sign in" onPress={() => setIsAuthOpen(true)} />
      </Show>
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

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
})
```

## Usage

The following examples show how to use the `<UserButton />` in your Expo app.

### Basic usage

filename: src/app/(home)/index.tsx
```tsx
import { View, Text } from 'react-native'
import { UserButton } from '@clerk/expo/native'
import { useUser } from '@clerk/expo'

export default function HomeScreen() {
  const { user } = useUser()

  return (
    <View style={{ flex: 1, padding: 20 }}>
      <View style={{ flexDirection: 'row', justifyContent: 'space-between', alignItems: 'center' }}>
        <Text style={{ fontSize: 24 }}>User ID: {user?.id}</Text>
        <UserButton />
      </View>
    </View>
  )
}
```

### In a header

The following example configures the header for screens in the `(home)` route group. Make sure the route group contains an `index.tsx` route.

filename: src/app/(home)/\_layout.tsx
```tsx
import { View } from 'react-native'
import { Stack } from 'expo-router'
import { UserButton } from '@clerk/expo/native'

export default function HomeLayout() {
  return (
    <Stack
      screenOptions={{
        headerRight: () => (
          <View style={{ marginRight: 16 }}>
            <UserButton />
          </View>
        ),
      }}
    >
      <Stack.Screen name="index" options={{ title: 'Home' }} />
    </Stack>
  )
}
```

## Properties

The `<UserButton />` component does not accept any props. It renders the avatar and opens [<UserProfileView />](https://clerk.com/docs/expo/reference/native-components/user-profile-view.md).

## Platform support

| Platform | Status                                                                                                             |
| -------- | ------------------------------------------------------------------------------------------------------------------ |
| iOS      | Supported (SwiftUI)                                                                                                |
| Android  | Supported (Jetpack Compose)                                                                                        |
| Web      | Use [<UserButton />](https://clerk.com/docs/expo/reference/components/user/user-button.md) from `@clerk/expo/web` |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
