# OrganizationSwitcher

![The OrganizationSwitcher renders an account switcher interface that lets signed-in users switch between their Personal and Organization accounts.](https://clerk.com/docs/raw/_public/images/ui-components/ios-organization-switcher-v2.png){{ style: { maxWidth: '425px' } }}

The `OrganizationSwitcher` renders an account switcher interface that lets signed-in users switch between their Personal and Organization accounts. It displays the Active Organization, or the user's Personal Account when no Organization is selected, and provides built-in native controls for managing the Active Organization, switching accounts, accepting Organization invitations and suggestions, and creating an Organization when permitted.

`OrganizationSwitcher` only renders when a user is signed in and Organizations are enabled for the instance. When Organization selection is required, the Personal Account option is hidden automatically.

`OrganizationSwitcher` renders the Organization or account trigger only. Render [UserButton](https://clerk.com/docs/ios/reference/views/user/user-button.md) separately when your layout also needs a profile control.

> When Organization selection is required, [AuthView](https://clerk.com/docs/ios/reference/views/authentication/auth-view.md) automatically handles the `choose_organization` session task. Continue rendering `AuthView` while the session has a pending task, then render your signed-in UI once the task is complete.

## Parameters

| Name                 | Type               | Description                                                                                                                                                                                                                                                             |
| -------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| hidePersonal         | Bool               | Whether the Personal AccountPersonal Accounts are individual workspaces that allow users to operate independently without belonging to an Organization. Learn more about Personal Accounts. option should be hidden even when the option is allowed. Defaults to false. |
| .normal              | .compact           | .normal shows the active account avatar, account name, and disclosure chevron. .compact shows only the avatar-sized account trigger. The default base avatar size is 36 points.                                                                                         |
| skipInvitationScreen | Bool               | Whether creating an Organization should skip the post-create invitation step. Defaults to false.                                                                                                                                                                        |
| label                | () -> LabelContent | Custom content shown inside the switcher button.                                                                                                                                                                                                                        |

## Usage

The following examples show how to use the `OrganizationSwitcher` in your app.

### Basic usage

```swift
import ClerkKit
import ClerkKitUI
import SwiftUI

struct HomeView: View {
  @Environment(Clerk.self) private var clerk

  var body: some View {
    if clerk.user != nil {
      HStack(spacing: 16) {
        OrganizationSwitcher()
        UserButton()
      }
    } else {
      AuthView()
    }
  }
}
```

### Compact switcher

```swift
OrganizationSwitcher(
  hidePersonal: false,
  displayMode: .compact(size: 40)
)
```

### Custom switcher label

The following example demonstrates how to render a custom switcher label.

```swift
import ClerkKitUI
import SwiftUI

OrganizationSwitcher {
  Text("Switch account")
}
```

### Customize the default Organization profile

Custom rows are shown in the switcher's default [OrganizationProfileView](https://clerk.com/docs/ios/reference/views/organization/organization-profile-view.md) only when you provide both `.organizationProfileRows()` and `.organizationProfileDestination()`.

```swift
import ClerkKitUI
import SwiftUI

enum OrganizationRoute: Hashable {
  case settings
}

OrganizationSwitcher()
  .organizationProfileRows([
    .init(
      route: .settings,
      title: "Settings",
      icon: .system(name: "gear"),
      placement: .after(.members)
    ),
  ])
  .organizationProfileDestination { (route: OrganizationRoute) in
    switch route {
    case .settings:
      // Replace this placeholder with the custom view for your Settings row.
      OrganizationSettingsContent()
    }
  }
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
