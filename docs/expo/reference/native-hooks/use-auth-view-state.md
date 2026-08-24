# useAuthViewState()

The `useAuthViewState()` hook reports when native authentication and Clerk-owned post-authentication steps are complete. Use it to determine when a non-dismissible root [<AuthView />](https://clerk.com/docs/expo/reference/native-components/auth-view.md) can be replaced with authenticated content.

The hook waits for both the native authentication flow and the JavaScript session state. This keeps `<AuthView />` mounted while it displays session tasks or biometric enrollment.

If native authentication-flow state isn't available, the hook falls back to the JavaScript authentication state. It considers the flow complete once authentication has loaded and the user is signed in.

> The native `<AuthView />` is available only on iOS and Android. It requires a [development build](https://docs.expo.dev/develop/development-builds/introduction/) that includes a compatible version of `@clerk/expo` and doesn't work in Expo Go.

## Returns

| Name               | Type    | Description                                                                                                                                                                                                                                         |
| ------------------ | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| isLoaded           | boolean | Whether the JavaScript authentication state and any available native authentication-flow state have loaded.                                                                                                                                         |
| isAuthFlowComplete | boolean | Whether authenticated content can replace the root <AuthView />. In a native build, this requires a signed-in JavaScript session and a native authentication flow that has completed authentication and any Clerk-owned post-authentication steps. |

## How to use the `useAuthViewState()` hook

The following example demonstrates how to keep a required root `<AuthView />` mounted until the native authentication flow is complete. If you render `<AuthView />` in a dismissible modal instead, use its `onDismiss` callback to control the modal.

filename: src/app/(auth)/sign-in.tsx
```tsx
import { AuthView, useAuthViewState } from '@clerk/expo/native'
import { Redirect } from 'expo-router'

export default function SignInScreen() {
  const { isLoaded, isAuthFlowComplete } = useAuthViewState()

  if (!isLoaded) {
    return null
  }

  if (isAuthFlowComplete) {
    return <Redirect href="/(home)" />
  }

  return <AuthView isDismissible={false} />
}
```

To learn how a prebuilt authentication flow can enroll a trusted device and sign in a returning user with biometrics, see the [biometric sign-in guide](https://clerk.com/docs/expo/guides/development/custom-flows/authentication/biometric-sign-in.md).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
