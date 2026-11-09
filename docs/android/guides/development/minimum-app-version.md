# Require a minimum app version

You can set a minimum version for each native app in the Clerk Dashboard, for example, when you release a security fix or change an API that older builds depend on. When a user opens a build below that minimum, Clerk rejects most of the app's requests and the SDK covers it with an update screen. The screen has a button that opens your app's page on Google Play. The user stays signed in and can continue where they left off after updating.

## Requirements

The update screen requires Clerk Android SDK `1.4.0` or later and the `com.clerk:clerk-android-ui` package. For more information, see [Installation](https://clerk.com/docs/android/reference/views/overview.md#installation).

## How minimum versions work

The Clerk SDK sends your app's version and package name with each request. Clerk compares that version with the minimum set for the app.

The version is the app's `versionCode`, the whole number Google Play uses to order releases, such as `42`. A minimum applies to the app's package name.

> Clerk returns `unsupported_app_version` for most requests from builds below the minimum until users update. The SDK can still load the environment to show the update screen, and users can still sign out or delete their account. If Clerk can't read the app's version, it allows the request.

## Set a minimum version

> Minimum app versions are free in development instances. In production, they require the Pro or Business plan. See [pricing](https://clerk.com/pricing). If a production instance's plan stops including them, Clerk removes that instance's minimum versions.

Minimum versions are set per [instance](https://clerk.com/docs/guides/development/managing-environments.md?sdk=android), so set them separately for your development and production instances.

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page.
2. Select the **Android** tab.
3. To add an app, select **Add Android app**. To change an existing app, on the right side of the app's row, select the menu icon (**...**) and select **Edit**.
4. Enable **Minimum app version**.
5. Enter the oldest `versionCode` that users can keep, such as `42`.
6. Enter the **Play Store URL** that users open to update the app.
7. Select **Add application** or **Update application**.

When the app returns to the foreground, the SDK checks whether its version still meets the minimum. If the version is too old, the update screen appears.

To remove a minimum, edit the app, disable **Minimum app version**, and select **Update application**. Lowering or removing a minimum lets users on newly allowed versions continue once the SDK checks the change.

## What users see

The Clerk UI library shows an update screen over your app automatically, in its own activity. Users can't dismiss it until they update. Using Android's Back navigation sends the app to the background. The update screen appears again when the user returns.

The update screen shows your app's name and installed version name, such as `4.8.4`. The button says **Go to Google Play**, or **Update app** if the update URL isn't a Google Play link. It uses the logo from your application's [**Settings**](https://dashboard.clerk.com/~/settings) and the theme set for Clerk views. If you've set a **Support email** there, it includes a **Can't update? Get help** email link.

The SDK applies the minimum it saved from the last environment it loaded, so an outdated app shows the update screen at launch, even when it's offline.

## Show your own update screen

To show your own screen instead of Clerk's update screen, call [withUpdateRequiredViewDisabled()](https://clerk.com/docs/android/reference/native-mobile/configuration.md#clerkconfigurationoptions) on the options you pass when you initialize Clerk:

filename: app/src/main/java/com/example/myclerkapp/MyClerkApp.kt
```kotlin
package com.example.myclerkapp

import android.app.Application
import com.clerk.api.Clerk
import com.clerk.api.ClerkConfigurationOptions

class MyClerkApp : Application() {
  override fun onCreate() {
    super.onCreate()

    Clerk.initialize(
      context = this,
      publishableKey = "{{pub_key}}",
      options = ClerkConfigurationOptions().withUpdateRequiredViewDisabled(),
    )
  }
}
```

Then collect `Clerk.appVersionSupportStatus`. The following example shows an update screen while the app's version is unsupported:

```kotlin
import androidx.compose.foundation.layout.Column
import androidx.compose.material3.Button
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.compose.ui.platform.LocalUriHandler
import androidx.lifecycle.compose.collectAsStateWithLifecycle
import com.clerk.api.Clerk

@Composable
fun AppRoot() {
    val status by Clerk.appVersionSupportStatus.collectAsStateWithLifecycle()
    val uriHandler = LocalUriHandler.current

    if (status.isSupported) {
        HomeScreen()
    } else {
        Column {
            Text("Update required")
            status.updateUrl?.let { updateUrl ->
                Button(onClick = { uriHandler.openUri(updateUrl) }) {
                    Text("Update")
                }
            }
        }
    }
}
```

> When Clerk rejects your app's version at launch, `Clerk.initializationError` stays `null`, and `Clerk.isInitialized` stays `false` unless the app has saved state from an earlier launch. Check `Clerk.appVersionSupportStatus` before you wait on either.

### `AppVersionSupportStatus`

| Name           | Type    | Description                                                           |
| -------------- | ------- | --------------------------------------------------------------------- |
| currentVersion | Long?   | This build's versionCode, or null before Clerk.initialize() reads it. |
| isSupported    | Boolean | Whether this version of the app is supported.                         |
| minimumVersion | Long?   | The oldest supported versionCode, when a minimum is set for this app. |
| updateUrl      | String? | The store page that users open to update the app.                     |

## Test a minimum version

Test the update screen on a development instance before you set a minimum on your production instance:

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page and set a minimum version higher than your app's current version.
2. Close and reopen your app. The update screen opens.
3. Lower the minimum to your app's current version or older, or disable **Minimum app version**.
4. Bring your app to the foreground. Once the SDK rechecks the minimum, the update screen closes and the user remains signed in.

## Troubleshooting

### The update screen doesn't appear

Verify that:

- [ ] Your app's package name matches an Android application on the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page of the instance your app uses.
- [ ] Your app's `versionCode` is older than the minimum, and is `1` or greater. Clerk doesn't check builds without a `versionCode`.
- [ ] Your app uses Clerk Android SDK `1.4.0` or later and includes `com.clerk:clerk-android-ui`. Earlier SDK versions don't send the app's package name or version, so Clerk doesn't block their requests or show an update screen.
- [ ] If you use Clerk's update screen, your app doesn't call `withUpdateRequiredViewDisabled()`.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
