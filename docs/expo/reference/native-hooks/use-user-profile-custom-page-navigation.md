# useUserProfileCustomPageNavigation()

Use `useUserProfileCustomPageNavigation()` within custom page content rendered by [<UserProfileView />](https://clerk.com/docs/expo/reference/native-components/user-profile-view.md#add-custom-pages) or the profile opened by [<UserButton />](https://clerk.com/docs/expo/reference/native-components/user-button.md#add-custom-profile-pages). You can navigate back, return to the root profile screen, or open another custom page.

Call this hook only from a component passed to a custom page's `content` property.

## Returns

| Name           | Type                             | Description                                                                          |
| -------------- | -------------------------------- | ------------------------------------------------------------------------------------ |
| navigateBack() | () => Promise<void>             | Navigates back one screen in the native user profile.                                |
| popToRoot()    | () => Promise<void>             | Returns to the root user profile screen.                                             |
| push()         | (path: string) => Promise<void> | Opens another custom page. The path must match a page in the same customPages array. |

## Example

The following example adds two custom pages. The first page uses `push()` to open the second page and `popToRoot()` to return to the profile screen. The second page uses `navigateBack()` to return to the first page.

```tsx
import { UserProfileView, useUserProfileCustomPageNavigation } from '@clerk/expo/native'
import { Button, Text, View } from 'react-native'

function APIKeysPage() {
  const { popToRoot, push } = useUserProfileCustomPageNavigation()

  return (
    <View style={{ flex: 1, justifyContent: 'center', padding: 24 }}>
      <Text style={{ fontSize: 24, marginBottom: 16 }}>API keys</Text>
      <Button title="Open API key help" onPress={() => void push('api-key-help')} />
      <Button title="Back to profile" onPress={() => void popToRoot()} />
    </View>
  )
}

function APIKeyHelpPage() {
  const { navigateBack } = useUserProfileCustomPageNavigation()

  return (
    <View style={{ flex: 1, justifyContent: 'center', padding: 24 }}>
      <Text style={{ fontSize: 24, marginBottom: 16 }}>API key help</Text>
      <Button title="Back to API keys" onPress={() => void navigateBack()} />
    </View>
  )
}

export default function ProfileScreen() {
  return (
    <UserProfileView
      customPages={[
        {
          path: 'api-keys',
          label: 'API keys',
          icon: 'key',
          content: <APIKeysPage />,
        },
        {
          path: 'api-key-help',
          label: 'API key help',
          icon: 'info',
          content: <APIKeyHelpPage />,
        },
      ]}
    />
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
