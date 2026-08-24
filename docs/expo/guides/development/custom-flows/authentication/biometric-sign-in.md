# Build a custom authentication flow using biometric sign-in

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md?sdk=expo) or [prebuilt components](https://clerk.com/docs/expo/reference/components/overview.md).

Biometric sign-in lets returning users sign in with their device's biometrics. After a normal sign-in or sign-up, your app can enroll the current installation as a trusted device. When the session expires, the user can sign in again with biometrics instead of their original sign-in method.

This is different from using biometrics only to unlock local app content. Biometric trusted-device sign-in authenticates with Clerk and creates a Clerk session. It is also different from a [passkey](https://clerk.com/docs/guides/development/custom-flows/authentication/passkeys.md?sdk=expo): trusted-device credentials are scoped to the native app installation and don't use [WebAuthn](https://www.w3.org/TR/webauthn-2/).

During enrollment, the SDK generates a device-bound key pair and registers the public key with Clerk. The private key never leaves the device. To sign in, the device signs a one-time Clerk challenge after the user approves the system authentication prompt. Clerk verifies the signature before creating a session.

> For a custom Expo flow, use the [useTrustedDevices()](https://clerk.com/docs/expo/reference/native-hooks/use-trusted-devices.md) hook to enroll trusted devices and sign in returning users. The hook uses native code, so it requires a [development build](https://docs.expo.dev/develop/development-builds/introduction/) and doesn't work in Expo Go. Don't use [`expo-local-authentication`](https://docs.expo.dev/versions/latest/sdk/local-authentication/) in its place; that package only verifies biometrics locally and cannot create a Clerk session.

## Enable biometric sign-in

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page and enable the Native API. This is required to integrate Clerk in your native application or browser extension.
   > Enabling the Native API opens a public request pathway that bypasses browser-based CAPTCHA challenges. Learn more about [how the Native API affects bot protection](https://clerk.com/docs/guides/secure/bot-protection.md?sdk=expo#native-api-and-captcha).
2. Navigate to the [**User & Authentication**](https://dashboard.clerk.com/~/user-authentication/user-and-authentication) page and select the **Biometric** tab.
3. Enable **Sign-in with mobile biometrics**.

If you use Clerk's prebuilt authentication views, you can also enable **Prompt after sign-in** or **Prompt after sign-up**. The prebuilt views will then offer enrollment after authentication and display biometric sign-in when a signed-out user has an enrolled credential. For a custom flow, use the APIs demonstrated in this guide.

> If the native [<AuthView />](https://clerk.com/docs/expo/reference/native-components/auth-view.md) is your app's non-dismissible root authentication view, use [useAuthViewState()](https://clerk.com/docs/expo/reference/native-hooks/use-auth-view-state.md) before replacing it with authenticated content so biometric enrollment can finish.

## Configure your platform

**iOS**

To support Face ID, add `NSFaceIDUsageDescription` to the `infoPlist` configuration in your Expo app config. The value must explain why your app uses Face ID.

filename: app.json
```json
{
  "expo": {
    "ios": {
      "infoPlist": {
        "NSFaceIDUsageDescription": "Use Face ID to sign in to this app."
      }
    }
  }
}
```

**Android**

Biometric trusted-device sign-in is supported on Android 9 (API level 28) and later. The device must have a Class 3 biometric enrolled. Clerk automatically adds the `USE_BIOMETRIC` permission to your app's merged manifest.

> Enrollment requires biometrics to be available on the device. With the default policy, authentication can fall back to the device passcode on iOS and to the device PIN, pattern, or password on Android 11 (API level 30) and later. On Android 9 and 10, authentication remains biometric-only. Pass `'biometry_current_set'` as the `policy` when biometric enrollment changes should invalidate the key and every use must require the currently enrolled biometrics.

## Enroll a trusted device

Enroll the current app installation only after the user completes a normal sign-in or sign-up and Clerk has a session with a status of `active` or `pending`.

The following example demonstrates how to enroll the current Expo app installation. The `reason` is displayed in the system authentication prompt.

filename: components/enroll-trusted-device.tsx
```tsx
import { useTrustedDevices } from '@clerk/expo'
import { Button } from 'react-native'

export function EnrollTrustedDevice() {
  const { enroll } = useTrustedDevices()

  const enrollCurrentDevice = async () => {
    try {
      await enroll({ reason: 'Use biometrics to sign in.' })
    } catch (err) {
      // See https://clerk.com/docs/guides/development/custom-flows/error-handling
      // for more info on error handling.
      console.error(JSON.stringify(err, null, 2))
    }
  }

  return <Button title="Enable biometric sign-in" onPress={enrollCurrentDevice} />
}
```

## Sign a returning user in

When the user no longer has an active session, check whether a local trusted-device credential is available before displaying biometric sign-in. While signed out, this availability check only inspects local state and can't confirm that the credential still exists in Clerk. If the subsequent sign-in reports that the credential no longer exists, the SDK removes the stale local state.

The following example checks availability, signs the user in, and sets the created session as active.

filename: components/sign-in-with-biometrics.tsx
```tsx
import { useEffect, useState } from 'react'
import { useSignIn, useTrustedDevices } from '@clerk/expo'
import { Button } from 'react-native'

export function SignInWithBiometrics() {
  const { isLoaded, setActive } = useSignIn()
  const { getAvailability, signIn } = useTrustedDevices()
  const [isAvailable, setIsAvailable] = useState(false)

  const refreshAvailability = async () => {
    try {
      const availability = await getAvailability()
      setIsAvailable(availability.isAvailable)
    } catch {
      setIsAvailable(false)
    }
  }

  useEffect(() => {
    void refreshAvailability()
  }, [])

  const handleSignIn = async () => {
    if (!isLoaded) return

    try {
      const result = await signIn()
      if (result.status === 'complete' && result.createdSessionId) {
        await setActive({ session: result.createdSessionId })
      }
    } catch (err) {
      // Keep another sign-in method available when biometric sign-in fails.
      console.error(JSON.stringify(err, null, 2))
      await refreshAvailability()
    }
  }

  if (!isLoaded || !isAvailable) return null

  return <Button title="Sign in with biometrics" onPress={handleSignIn} />
}
```

## Revoke a trusted device

While the user is signed in, list their active trusted devices and let them choose which credential to revoke. Revoking a credential prevents Clerk from accepting it again. When the matching credential belongs to the current app installation, the SDK also deletes its local private key and credential metadata.

> Don't delete only the local key as a replacement for revocation. Local deletion doesn't invalidate the credential stored by Clerk.

The following example lists trusted devices and revokes the selected credential.

filename: components/revoke-trusted-device.tsx
```tsx
import { useEffect, useState } from 'react'
import { type TrustedDevice, useTrustedDevices } from '@clerk/expo'
import { Button, Text, View } from 'react-native'

export function RevokeTrustedDevice() {
  const { list, revoke } = useTrustedDevices()
  const [devices, setDevices] = useState<TrustedDevice[]>([])

  const loadTrustedDevices = async () => {
    try {
      setDevices(await list())
    } catch (err) {
      // See https://clerk.com/docs/guides/development/custom-flows/error-handling
      // for more info on error handling.
      console.error(JSON.stringify(err, null, 2))
    }
  }

  const handleRevoke = async (id: string) => {
    try {
      await revoke(id)
      setDevices((currentDevices) => currentDevices.filter((device) => device.id !== id))
    } catch (err) {
      // See https://clerk.com/docs/guides/development/custom-flows/error-handling
      // for more info on error handling.
      console.error(JSON.stringify(err, null, 2))
    }
  }

  useEffect(() => {
    void loadTrustedDevices()
  }, [])

  return (
    <View>
      {devices.map((device) => (
        <View key={device.id}>
          <Text>{device.name ?? 'Trusted device'}</Text>
          <Button title="Revoke" onPress={() => handleRevoke(device.id)} />
        </View>
      ))}
    </View>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
