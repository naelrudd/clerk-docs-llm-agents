# Use hosted authentication in native apps

Hosted authentication opens Clerk's [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md?sdk=android) in a browser authentication session. Your users can complete any sign-in or sign-up method enabled for your Clerk application, and the Clerk SDK activates the resulting session in your native app.

The browser doesn't retain a separate active session after Clerk transfers the session to your app.

## When to use hosted authentication

Hosted authentication is the fastest way to add sign-in and sign-up to a native app. The browser session opens over your app, so users stay in your app for the whole flow. Choose it when you want Clerk to host and maintain the authentication UI and you don't need that UI built from native components.

For authentication that renders with native components instead of a browser session, use Clerk's [Expo native components](https://clerk.com/docs/reference/expo/native-components/overview.md) or [iOS and Android views](https://clerk.com/docs/android/reference/views/overview.md). To control every step of the UI and authentication flow, build a [custom flow](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=android).

## Before you start

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page, enable the Native API, and add your app. Production instances validate the callback against the registered bundle identifier or package name, so add your app before you create a production build.
2. Install and configure the Clerk SDK for [Expo](https://clerk.com/docs/expo/getting-started/quickstart.md), [iOS](https://clerk.com/docs/ios/getting-started/quickstart.md), or [Android](https://clerk.com/docs/android/getting-started/quickstart.md).

> Account Portal runs in a browser, so social sign-in uses each provider's web OAuth flow rather than the native one. On production instances, [Sign in with Apple](https://clerk.com/docs/guides/configure/auth-strategies/sign-in-with-apple.md) needs an **Apple Services ID** and key set up through the [Apple social connection](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/apple.md?sdk=android#configure-for-your-production-instance).

## Add hosted authentication

**Android**

Call `startHostedAuth()` from a coroutine. The following example opens Account Portal when a user selects **Sign in**:

```kotlin
import androidx.compose.material3.Button
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.rememberCoroutineScope
import com.clerk.api.Clerk
import kotlinx.coroutines.launch

@Composable
fun SignInButton() {
    val scope = rememberCoroutineScope()

    Button(
        onClick = {
            scope.launch {
                Clerk.auth.startHostedAuth()
            }
        },
    ) {
        Text("Sign in")
    }
}
```

The Android SDK registers the default `clerk://<package-name>.callback` callback for your app.

After authentication completes, the SDK closes the browser session, activates the new session, and updates its authentication state.

## Open the sign-up page first

Account Portal opens the sign-in page by default. Pass the sign-up mode to open the sign-up page instead:

**Android**

```kotlin
import com.clerk.api.auth.HostedAuthMode

Clerk.auth.startHostedAuth(mode = HostedAuthMode.SIGN_UP)
```

Users can still switch between sign-in and sign-up from Account Portal regardless of the initial page.

## Handle cancellation and errors

Users can dismiss the browser authentication session before they finish. Each SDK reports cancellation differently:

**Android**

`startHostedAuth()` returns a failure when the user dismisses the browser or authentication fails:

```kotlin
import com.clerk.api.network.serialization.ClerkResult

when (val result = Clerk.auth.startHostedAuth()) {
    is ClerkResult.Success -> {
        // The session is active.
    }
    is ClerkResult.Failure -> {
        // The user dismissed the browser, or authentication failed.
    }
}
```

For details about platform-specific options and errors, see the [useHostedAuth() reference](https://clerk.com/docs/reference/expo/native-hooks/use-hosted-auth.md) for Expo or the [native authentication reference](https://clerk.com/docs/android/reference/native-mobile/auth.md) for iOS and Android.

## Troubleshooting

### The browser doesn't close after authentication

Check that the bundle identifier or package name in your app matches the entry on the Clerk Dashboard's [**Native applications**](https://dashboard.clerk.com/~/native-applications) page.

For Expo apps on Android, also confirm that `@clerk/expo` is present in the `plugins` array in `app.json`. Rebuild the native project after you add the plugin or change the Android package name.

### Signing in with a social provider fails

The provider's screen appears and accepts the user, then sign-in stops without an error.

The provider is missing its credentials. Production instances require you to supply your own for each social provider. Check the provider's custom credentials on the Clerk Dashboard's [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page. For Apple, that's an **Apple Services ID** and key, set up through the [Apple social connection](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/apple.md?sdk=android#configure-for-your-production-instance).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
