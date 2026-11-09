# Require a minimum app version

You can set a minimum version for each native app in the Clerk Dashboard, for example, when you release a security fix or change an API that older builds depend on. When a user opens a build below that minimum, Clerk rejects most of the app's requests and the SDK covers it with an update screen. The screen has a button that opens your app's page on the App Store or Google Play, depending on the platform. The user stays signed in and can continue where they left off after updating.

## Install `expo-application`

The update screen requires `@clerk/expo` 4.15.0 or later and [`expo-application`](https://docs.expo.dev/versions/latest/sdk/application/), which Clerk uses to read your app's version and its iOS bundle ID or Android package name. Install the package:

filename: terminal
```sh
npx expo install expo-application
```

> Without `expo-application`, Clerk doesn't block your app's JavaScript requests and `<ClerkProvider>` shows no update screen. If your app uses `@clerk/expo-native-components`, the native SDKs still identify your app, block its requests, and show their own update screen. Apps running in Expo Go and web apps are never blocked.

## How minimum versions work

In development and release builds with `expo-application` installed, the Clerk SDK sends your app's version and bundle ID or package name with each request. Clerk compares that version with the minimum set for the app.

**iOS**

The installed build's version is `CFBundleShortVersionString`, such as `4.2.1`. Expo sets it from `expo.version` in your app config, or from your native project if you maintain the `ios` folder yourself.

For iOS minimums, Clerk treats missing numbers as zero, so `4.2` is equivalent to `4.2.0`. The minimum applies to every iOS application with the same bundle ID.

**Android**

The installed build's version is `versionCode`, such as `42`. Expo sets it from `expo.android.versionCode` in your app config, or from your native project if you maintain the `android` folder yourself.

If EAS manages build versions remotely (`"appVersionSource": "remote"` in `eas.json`), the `versionCode` comes from EAS instead. Check the value of the build you shipped. The minimum applies to the app's package name.

> Clerk returns `unsupported_app_version` for most requests from builds below the minimum until users update. The SDK can still load the environment to show the update screen, and users can still sign out or delete their account. If Clerk can't read the app's version, it allows the request.

## Set a minimum version

> Minimum app versions are free in development instances. In production, they require the Pro or Business plan. See [pricing](https://clerk.com/pricing). If a production instance's plan stops including them, Clerk removes that instance's minimum versions.

Minimum versions are set per [instance](https://clerk.com/docs/guides/development/managing-environments.md?sdk=expo), so set them separately for your development and production instances.

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page.
2. Select the **iOS** or **Android** tab.
3. To add an app, select **Add iOS app** or **Add Android app**. To change an existing app, on the right side of the app's row, select the menu icon (**...**) and select **Edit**.
4. Enable **Minimum app version**.
5. Enter the oldest version that users can keep. For iOS, enter up to three dot-separated numbers, such as `4.2.1`. For Android, enter a `versionCode`, such as `42`.
6. Enter the **App Store URL** or **Play Store URL** that users open to update the app.
7. Select **Add application** or **Update application**.

When the app returns to the foreground, the SDK checks whether its version still meets the minimum, at most once every 30 seconds. If the version is too old, the update screen appears.

To remove a minimum, edit the app, disable **Minimum app version**, and select **Update application**. Lowering or removing a minimum lets users on newly allowed versions continue once the SDK checks the change.

## What users see

[<ClerkProvider>](https://clerk.com/docs/expo/reference/components/clerk-provider.md) shows an update screen over your app automatically on iOS and Android, in a modal that users can't dismiss until they update.

The update screen shows your app's name and installed version. On iOS, it also shows the minimum version and a **Go to App Store** button. On Android, the button says **Go to Google Play**, or **Update app** if the URL isn't a Google Play link. It uses the logo from your application's [**Settings**](https://dashboard.clerk.com/~/settings) and includes an email link if you've set a **Support email** there.

## Show your own update screen

To show your own screen instead of Clerk's update screen, read the app's status with the [useAppVersionSupport()](https://clerk.com/docs/expo/reference/native-hooks/use-app-version-support.md) hook, which updates when the status changes. The following example defines a custom `<UpdateGate>` component that shows an update screen while the app's version is unsupported:

filename: src/components/update-gate.tsx
```tsx
import { useAppVersionSupport } from '@clerk/expo'
import type { ReactNode } from 'react'
import { Button, Linking, Text, View } from 'react-native'

export function UpdateGate({ children }: { children: ReactNode }) {
  const { isSupported, updateUrl } = useAppVersionSupport()

  if (isSupported) {
    return children
  }

  return (
    <View>
      <Text>Update required</Text>
      {updateUrl && <Button title="Update" onPress={() => Linking.openURL(updateUrl)} />}
    </View>
  )
}
```

In your root layout, set `updateRequiredViewEnabled={false}` on `<ClerkProvider>` and wrap `<Slot />` in `<UpdateGate>`:

filename: src/app/\_layout.tsx
```tsx
import { ClerkProvider } from '@clerk/expo'
import { tokenCache } from '@clerk/expo/token-cache'
import { Slot } from 'expo-router'
import { UpdateGate } from '../components/update-gate'

const publishableKey = process.env.EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY!

if (!publishableKey) {
  throw new Error('Add your Clerk Publishable Key to the .env file')
}

export default function RootLayout() {
  return (
    <ClerkProvider
      publishableKey={publishableKey}
      tokenCache={tokenCache}
      updateRequiredViewEnabled={false}
    >
      <UpdateGate>
        <Slot />
      </UpdateGate>
    </ClerkProvider>
  )
}
```

> When Clerk rejects your app's version at launch, Clerk can't finish loading, so `isLoaded` from hooks like [useAuth()](https://clerk.com/docs/expo/reference/hooks/use-auth.md) stays `false`. Keep the component outside anything that waits for Clerk to load, so that your update screen still shows. When the block lifts, Clerk finishes loading and restores the user's session.

## Test a minimum version

Test the update screen on a development instance before you set a minimum on your production instance:

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page and set a minimum version higher than your app's current version.
2. Close and reopen your app. The update screen opens.
3. Lower the minimum to your app's current version or older, or disable **Minimum app version**.
4. Bring your app to the foreground. Once the SDK rechecks the minimum, the update screen closes and the user remains signed in.

## Troubleshooting

### The update screen doesn't appear

Verify that:

- [ ] Your app's bundle ID or package name matches an application on the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page of the instance your app uses.
- [ ] Your app's version is older than the minimum.
- [ ] Your app uses `@clerk/expo` 4.15.0 or later, with `expo-application` installed. Earlier versions don't send the app's version from JavaScript, so Clerk doesn't block those JavaScript requests.
- [ ] Your app runs in a [development build](https://docs.expo.dev/develop/development-builds/introduction/) or a release build, not in Expo Go.
- [ ] If you use Clerk's update screen, `<ClerkProvider>` doesn't have `updateRequiredViewEnabled={false}`.

### Users see an error message instead of the update screen

On iOS, Clerk iOS SDK versions 1.0.0 through 1.6.x send the app's version but don't show an update screen. These versions come with earlier releases of `@clerk/expo` and `@clerk/expo-native-components`. When the app is below the minimum, their requests fail with the message "This version of the app is no longer supported. Update the app to continue."

Release a version of your app that uses `@clerk/expo` 4.15.0 or later, and the latest `@clerk/expo-native-components` if you use [native components](https://clerk.com/docs/expo/reference/native-components/overview.md), so that users who later fall below a minimum see the update screen.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
