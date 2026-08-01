# UserProfileView

![The UserProfileView renders a comprehensive user profile interface that displays user information and provides account management options.](https://clerk.com/docs/raw/_public/images/ui-components/android-user-profile-view.png){{ style: { maxWidth: '460px' } }}

The `UserProfileView` renders a comprehensive user profile interface that displays user information and provides account management options. It includes personal information, security settings, account switching, and sign-out functionality.

> The `UserProfileView` only appears when there is a current user.

## Parameters

| Name              | Type                            | Description                                                                                                                                                     |
| ----------------- | ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| clerkTheme        | ClerkTheme?                     | The theme to apply to the UserProfileView. This will override any theme applied to the UserProfileView's parent view, or configured in the Clerk global object. |
| customRows        | List<UserProfileCustomRow>     | Custom rows to display on the profile account screen.                                                                                                           |
| customDestination | (@Composable (String) -> Unit)? | Destination builder for custom rows. The destination receives the tapped row's routeKey. Custom rows are ignored when this is null.                             |
| onAddAccount      | (() -> Unit)?                   | Called when the user selects the add account action. Use this to host the add account auth flow outside the profile view.                                       |
| onDismiss         | (() -> Unit)?                   | Called when the user profile view is dismissed. When omitted, dismissal falls back to the system back dispatcher.                                               |
| isDismissible     | Boolean                         | Whether the view shows a top-right close affordance that dismisses the profile. Defaults to true.                                                               |

## Usage

The following example shows how to use the `UserProfileView` in your Android app.

### Fullscreen profile view

Use `UserProfileView` as a fullscreen view when you want to dedicate the entire screen to profile management.

```kotlin
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.lifecycle.compose.collectAsStateWithLifecycle
import com.clerk.api.Clerk
import com.clerk.ui.userprofile.UserProfileView

@Composable
fun ProfileView() {
  val user by Clerk.userFlow.collectAsStateWithLifecycle()
  if (user != null) {
    UserProfileView()
  }
}
```

### Non-dismissible profile view

Use `isDismissible = false` when the profile view is the required fullscreen experience for the current route.

```kotlin
import com.clerk.ui.userprofile.UserProfileView

UserProfileView(isDismissible = false)
```

## Customization

To learn how to customize Clerk views, see the [dedicated guide](https://clerk.com/docs/android/guides/customizing-clerk/clerk-theme.md).

If Clerk's prebuilt views don't meet your specific needs or if you require more control over the logic, you can rebuild the existing Clerk flows using the Clerk API. For more information, see the [custom flow guides](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=android).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
