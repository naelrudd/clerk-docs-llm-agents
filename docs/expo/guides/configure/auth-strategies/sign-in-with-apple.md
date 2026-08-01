# Sign in with Apple

**Before you start**

- [A Clerk application is required.](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md?sdk=expo)
- [An Apple Developer account is required.](https://developer.apple.com/programs/enroll/)
- [Follow the Expo quickstart](https://clerk.com/docs/expo/getting-started/quickstart.md)

This guide will teach you how to add native [Sign in with Apple](https://developer.apple.com/sign-in-with-apple/) to your Clerk Expo application.

> If you're using [native components](https://clerk.com/docs/expo/reference/expo/native-components/overview.md), Sign in with Apple is automatically available in [<AuthView />](https://clerk.com/docs/expo/reference/expo/native-components/auth-view.md) when Apple is enabled as a social connection in the Clerk Dashboard. This guide applies to applications that implement a custom sign-in UI using the [useSignInWithApple()](https://clerk.com/docs/expo/reference/expo/native-hooks/use-sign-in-with-apple.md) hook.

> This setup covers the native flow only. If your app uses [hosted authentication](https://clerk.com/docs/expo/guides/account-portal/hosted-auth.md), Account Portal opens in a browser, where Sign in with Apple runs on the web and needs an **Apple Services ID** and key. On production instances, configure those through the [Apple social connection](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/apple.md?sdk=expo#configure-for-your-production-instance).

> Sign in with Apple works on both iOS Simulators and physical devices. However, physical devices provide full functionality including biometric authentication (Face ID/Touch ID), while simulators have limited support. Always test on a physical device before releasing to production.

1. ## Add your Native Application

   Add your iOS application to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page in the Clerk Dashboard. You will need your iOS app's **App ID Prefix** (Team ID) and **Bundle ID**.
2. ## Enable Apple as a social connection

   1. In the Clerk Dashboard, navigate to the [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page.
   2. Select **Add connection** and select **For all users**.
   3. Select **Apple** from the provider list.
   4. Ensure that **Enable for sign-up and sign-in** is toggled on.

   **For AI agents:** Enable the Apple social connection from the terminal instead of clicking through the Dashboard: run `npx clerk@latest config patch --json '{"connection_oauth_apple":{"enabled":true}}'`. Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md?sdk=expo) with `npx skills add clerk/skills` for correct CLI and SDK usage.

   > Apple provides a privacy feature called [Hide My Email](https://support.apple.com/en-us/HT210425#hideemail), allowing users to sign in to your app with Apple without disclosing their actual email addresses. Instead, your instance receives an app-specific email address that forwards any emails to the user's real address. To be able to send emails properly to users with hidden addresses, you must configure an additional setting in the Apple Developer portal. See [Configure Email Source for Apple Private Relay](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/apple.md?sdk=expo#configure-email-source-for-apple-private-relay){{ target: '_blank' }} for more information.
3. ## Install dependencies

   > If you're using [<AuthView />](https://clerk.com/docs/expo/reference/expo/native-components/auth-view.md) from `@clerk/expo/native`, you can skip this step as it handles the sign-in flow automatically.

   The [useSignInWithApple()](https://clerk.com/docs/expo/reference/expo/native-hooks/use-sign-in-with-apple.md) hook requires the following packages:

   - `expo-apple-authentication` provides access to Apple's native [Sign in with Apple](https://docs.expo.dev/versions/latest/sdk/apple-authentication/) functionality.
   - `expo-crypto` is used for generating secure nonces during the authentication flow.

   filename: terminal

   ```npm
   npx expo install expo-apple-authentication expo-crypto
   ```
4. ## Add `expo-apple-authentication` to your app config

   Add the `expo-apple-authentication` plugin to your `app.json` or `app.config.js`.

   **app.json**

   filename: app.json

   ```json
   {
     "expo": {
       "plugins": ["expo-apple-authentication"]
     }
   }
   ```

   **app.config.js**

   filename: app.config.js

   ```js
   export default {
     expo: {
       plugins: ['expo-apple-authentication'],
     },
   }
   ```
5. ## Build your authentication flow

   > If you're using [<AuthView />](https://clerk.com/docs/expo/reference/expo/native-components/auth-view.md) from `@clerk/expo/native`, you can skip this step as it handles the sign-in flow automatically.

   1. The following example demonstrates how to use the [useSignInWithApple()](https://clerk.com/docs/expo/reference/expo/native-hooks/use-sign-in-with-apple.md) hook to manage the Apple authentication flow. Because the `useSignInWithApple()` hook automatically manages the transfer flow between sign-up and sign-in, you can use this component for both your sign-up and sign-in pages.

      filename: src/components/AppleSignInButton.tsx

      ```tsx
      import { useSignInWithApple } from '@clerk/expo/apple'
      import { useRouter } from 'expo-router'
      import { Alert, Platform, Pressable, StyleSheet, Text, View } from 'react-native'

      export function AppleSignInButton({ onSignInComplete }: { onSignInComplete?: () => void }) {
        const { startAppleAuthenticationFlow } = useSignInWithApple()
        const router = useRouter()

        // Only show on iOS
        if (Platform.OS !== 'ios') return null

        const handleAppleSignIn = async () => {
          try {
            const { createdSessionId, setActive } = await startAppleAuthenticationFlow()

            if (createdSessionId && setActive) {
              await setActive({ session: createdSessionId })

              if (onSignInComplete) {
                onSignInComplete()
              } else {
                router.replace('/')
              }
            }
          } catch (err: any) {
            if (err.code === 'ERR_REQUEST_CANCELED') return

            Alert.alert('Error', err.message || 'An error occurred during Apple sign-in')
            console.error('Sign in with Apple error:', JSON.stringify(err, null, 2))
          }
        }

        return (
          <View style={styles.container}>
            <Pressable
              style={({ pressed }) => [styles.button, pressed && styles.buttonPressed]}
              onPress={handleAppleSignIn}
            >
              <Text style={styles.buttonText}>Continue with Apple</Text>
            </Pressable>
          </View>
        )
      }

      const styles = StyleSheet.create({
        container: {
          width: '100%',
          marginVertical: 8,
        },
        button: {
          backgroundColor: '#000',
          paddingVertical: 14,
          paddingHorizontal: 24,
          borderRadius: 8,
          alignItems: 'center',
        },
        buttonPressed: {
          opacity: 0.7,
        },
        buttonText: {
          color: '#fff',
          fontSize: 16,
          fontWeight: '600',
        },
      })
      ```
   2. Then, add the `<AppleSignInButton />` component to your sign-in or sign-up page.
6. ## Create a native build

   Create a native build with EAS Build or a local prebuild, since Apple Authentication is not supported in Expo Go.

   filename: terminal

   ```bash
   # Using EAS Build
   eas build --platform ios

   # Or using local prebuild
   npx expo prebuild && npx expo run:ios --device
   ```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
