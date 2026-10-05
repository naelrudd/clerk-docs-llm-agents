# <UserButton /> component

The `<UserButton />` component renders the familiar user button UI popularized by Google. When selected, it opens a dropdown menu with options to manage account settings and sign out. The "Manage account" option launches the [<UserProfile />](https://clerk.com/docs/electron/reference/components/user/user-profile.md) component, providing access to profile and security settings.

For users that have [multi-session](https://clerk.com/docs/guides/secure/session-options.md?sdk=electron#multi-session-applications) enabled, the `<UserButton />` also allows users to sign into multiple accounts at once and instantly switch between them without the need for a full page reload. Learn more about [multi-session applications](https://clerk.com/docs/guides/secure/session-options.md?sdk=electron#multi-session-applications).

## Example

The following example includes a basic implementation of the `<UserButton />` component mounted in a header. When the user is signed in, they will see their avatar and be able to open the popup menu. You can use this as a starting point for your own implementation.

filename: src/App.tsx
```tsx
import { Show, UserButton, SignInButton } from '@clerk/electron/react'

function App() {
  return (
    <header>
      <Show when="signed-in">
        <UserButton />
      </Show>
      <Show when="signed-out">
        <SignInButton />
      </Show>
    </header>
  )
}

export default App
```

## Pass props to `<UserProfile />`

The `<UserButton />` opens the [<UserProfile />](https://clerk.com/docs/electron/reference/components/user/user-profile.md) when a user selects **Manage account**. To configure it, use the [userProfileProps](https://clerk.com/docs/electron/reference/components/user/user-button.md#properties) prop.

The following example requests additional OAuth scopes when the user connects their Google account through `<UserProfile />`.

```tsx
<UserButton
  userProfileProps={{
    additionalOAuthScopes: {
      google: ['https://www.googleapis.com/auth/calendar.readonly'],
    },
  }}
/>
```

## Properties

The `<UserButton />` component accepts the following properties, all of which are **optional**:

| Name                                                                                                                    | Type                                               | Description                                                                                                                                                                                                                                      |
| ----------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| afterMultiSessionSingleSignOutUrl?                                                                                      | string                                             | Deprecated. Move afterMultiSessionSingleSignOutUrl to <ClerkProvider />. The full URL or path to navigate to after signing out from a currently active account in a multi-session app.                                                          |
| afterSignOutUrl?                                                                                                        | string                                             | Deprecated. Move afterSignOutUrl to <ClerkProvider />. The full URL or path to navigate to after a successful sign-out.                                                                                                                         |
| afterSwitchSessionUrl?                                                                                                  | string                                             | The full URL or path to navigate to after a successful account change in a multi-session app.                                                                                                                                                    |
| appearance?                                                                                                             | Appearance | undefined                            | An object to style your components. Will only affect Clerk components and not Account Portal pages.                                                                                                                                              |
| defaultOpen?                                                                                                            | boolean                                            | Controls whether the <UserButton /> should open by default during the first render.                                                                                                                                                             |
| fallback?                                                                                                               | ReactNode                                          | An element to be rendered while the component is mounting.                                                                                                                                                                                       |
| showName?                                                                                                               | boolean                                            | Controls if the user name is displayed next to the user image button.                                                                                                                                                                            |
| signInUrl?                                                                                                              | string                                             | The full URL or path to navigate to when the Add another account button is clicked. It's recommended to use the environment variable instead.                                                                                                    |
| userProfileMode?                                                                                                        | 'modal' | 'navigation'                            | Controls whether selecting the Manage your account button will cause the <UserProfile /> component to open as a modal, or if the browser will navigate to the userProfileUrl where <UserProfile /> is mounted as a page. Defaults to: 'modal'. |
| additionalOAuthScopes: Specifies additional scopes per OAuth provider to request if they haven't already been approved. | appearance: An object used to style the component. | See Pass props to <UserProfile /> for an example.                                                                                                                                                                                               |
| userProfileUrl?                                                                                                         | string                                             | The full URL or path leading to the user management interface.                                                                                                                                                                                   |

## Customization

To learn how to customize Clerk components, see the [customization documentation](https://clerk.com/docs/electron/guides/customizing-clerk/appearance-prop/overview.md).

You can also [add custom actions and links to the <UserButton /> menu](https://clerk.com/docs/electron/guides/customizing-clerk/adding-items/user-button.md).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
