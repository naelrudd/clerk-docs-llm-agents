# Build a custom authentication flow using biometric sign-in

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md?sdk=android) or [prebuilt views](https://clerk.com/docs/android/reference/views/overview.md).

Biometric sign-in lets returning users sign in with their device's biometrics. After a normal sign-in or sign-up, your app can enroll the current installation as a trusted device. When the session expires, the user can sign in again with biometrics instead of their original sign-in method.

This is different from using biometrics only to unlock local app content. Biometric trusted-device sign-in authenticates with Clerk and creates a Clerk session. It is also different from a [passkey](https://clerk.com/docs/guides/development/custom-flows/authentication/passkeys.md?sdk=android): trusted-device credentials are scoped to the native app installation and don't use [WebAuthn](https://www.w3.org/TR/webauthn-2/).

During enrollment, the SDK generates a device-bound key pair and registers the public key with Clerk. The private key never leaves the device. To sign in, the device signs a one-time Clerk challenge after the user approves the system authentication prompt. Clerk verifies the signature before creating a session.

## Enable biometric sign-in

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page and enable the Native API. This is required to integrate Clerk in your native application or browser extension.
   > Enabling the Native API opens a public request pathway that bypasses browser-based CAPTCHA challenges. Learn more about [how the Native API affects bot protection](https://clerk.com/docs/guides/secure/bot-protection.md?sdk=android#native-api-and-captcha).
2. Navigate to the [**User & Authentication**](https://dashboard.clerk.com/~/user-authentication/user-and-authentication) page and select the **Biometric** tab.
3. Enable **Sign-in with mobile biometrics**.

If you use Clerk's prebuilt authentication views, you can also enable **Prompt after sign-in** or **Prompt after sign-up**. The prebuilt views will then offer enrollment after authentication and display biometric sign-in when a signed-out user has an enrolled credential. For a custom flow, use the APIs demonstrated in this guide.

> If [AuthView(isDismissible = false)](https://clerk.com/docs/android/reference/views/authentication/auth-view.md) is your app's root authentication view, use `Clerk.isAuthFlowCompleteFlow` before replacing it with authenticated content so biometric enrollment can finish.

## Configure your platform

Biometric trusted-device sign-in is supported on Android 9 (API level 28) and later. The device must have a Class 3 biometric enrolled. Clerk automatically adds the `USE_BIOMETRIC` permission to your app's merged manifest.

> Enrollment requires biometrics to be available on the device. With the default policy, authentication can fall back to the device PIN, pattern, or password on Android 11 (API level 30) and later. On Android 9 and 10, authentication remains biometric-only. Pass `BIOMETRY_CURRENT_SET` as the `policy` when biometric enrollment changes should invalidate the key and every use must require the currently enrolled biometrics.

## Enroll a trusted device

Enroll the current app installation only after the user completes a normal sign-in or sign-up and Clerk has a session with a status of `active` or `pending`.

The following example demonstrates how to enroll the current Android app installation. The `promptTitle` is displayed in the system authentication prompt.

filename: EnrollTrustedDevice.kt
```kotlin
import com.clerk.api.Clerk
import com.clerk.api.network.serialization.onFailure
import com.clerk.api.network.serialization.onSuccess

suspend fun enrollCurrentDevice() {
  Clerk.trustedDevices
    .enroll(promptTitle = "Use biometrics to sign in")
    .onSuccess {
      // The current app installation is enrolled.
    }
    .onFailure {
      // See https://clerk.com/docs/guides/development/custom-flows/error-handling
      // for more info on error handling.
    }
}
```

## Sign a returning user in

When the user no longer has an active session, check whether a local trusted-device credential is available before displaying biometric sign-in. While signed out, this availability check only inspects local state and can't confirm that the credential still exists in Clerk. If the subsequent sign-in reports that the credential no longer exists, the SDK removes the stale local state.

The following example checks availability, signs the user in, and sets the created session as active.

filename: SignInWithBiometrics.kt
```kotlin
import com.clerk.api.Clerk
import com.clerk.api.network.serialization.onFailure
import com.clerk.api.network.serialization.onSuccess
import com.clerk.api.signin.SignIn

suspend fun signInWithBiometrics() {
  val availability = Clerk.trustedDevices.availability()
  if (!availability.isAvailable) return

  Clerk.auth
    .signInWithTrustedDevice()
    .onSuccess { signIn ->
      if (signIn.status == SignIn.Status.COMPLETE && signIn.createdSessionId != null) {
        Clerk.auth
          .setActive(sessionId = signIn.createdSessionId)
          .onFailure {
            // See https://clerk.com/docs/guides/development/custom-flows/error-handling
            // for more info on error handling.
          }
      }
    }
    .onFailure {
      // Keep another sign-in method available when biometric sign-in fails.
    }
}
```

## Revoke a trusted device

While the user is signed in, list their active trusted devices and let them choose which credential to revoke. Revoking a credential prevents Clerk from accepting it again. When the matching credential belongs to the current app installation, the SDK also deletes its local private key and credential metadata.

> Don't delete only the local key as a replacement for revocation. Local deletion doesn't invalidate the credential stored by Clerk.

The following example lists trusted devices and revokes the selected credential.

filename: RevokeTrustedDevice.kt
```kotlin
import com.clerk.api.Clerk
import com.clerk.api.network.serialization.onFailure
import com.clerk.api.network.serialization.onSuccess
import com.clerk.api.trusteddevice.TrustedDevice

suspend fun listTrustedDevices(onLoaded: (List<TrustedDevice>) -> Unit) {
  Clerk.trustedDevices
    .list()
    .onSuccess { devices ->
      // Render these devices and pass the selected device's ID to revokeTrustedDevice().
      onLoaded(devices)
    }
    .onFailure {
      // See https://clerk.com/docs/guides/development/custom-flows/error-handling
      // for more info on error handling.
    }
}

suspend fun revokeTrustedDevice(id: String) {
  Clerk.trustedDevices
    .revoke(id)
    .onSuccess {
      // The trusted device is revoked.
    }
    .onFailure {
      // See https://clerk.com/docs/guides/development/custom-flows/error-handling
      // for more info on error handling.
    }
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
