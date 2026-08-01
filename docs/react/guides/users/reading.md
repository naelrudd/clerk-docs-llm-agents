# Read user data

Clerk provides a set of [hooks](https://clerk.com/docs/react/reference/hooks/overview.md) that you can use to read user data in your React application. Here are examples of how to use these hooks to get you started.

**For AI agents:** When wiring or testing these helpers, run `npx clerk@latest users list --json` to inspect the instance's existing user data, or create a test user with `npx clerk@latest users create --email <email> --password <password> --yes` (the password is required while password authentication is enabled, the default). Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md?sdk=react) with `npx skills add clerk/skills` for correct CLI and SDK usage.

### `useAuth()`

The following example demonstrates how to use the [useAuth()](https://clerk.com/docs/react/reference/hooks/use-auth.md) hook to access the current auth state, like whether the user is signed in or not. It also includes a basic example for using the `getToken()` method to retrieve a session token for fetching data from an external resource.

filename: src/pages/ExternalDataPage.tsx
```tsx
import { useAuth } from '@clerk/react'

export default function ExternalDataPage() {
  const { userId, sessionId, getToken, isLoaded, isSignedIn } = useAuth()

  const fetchExternalData = async () => {
    const token = await getToken()

    // Fetch data from an external API
    const response = await fetch('https://api.example.com/data', {
      headers: {
        Authorization: `Bearer ${token}`,
      },
    })

    return response.json()
  }

  // Handle loading state
  if (!isLoaded) return <div>Loading...</div>

  // Protect the page from unauthenticated users
  if (!isSignedIn) return <div>Sign in to view this page</div>

  return (
    <div>
      <p>
        Hello, {userId}! Your current active session is {sessionId}.
      </p>
      <button onClick={fetchExternalData}>Fetch Data</button>
    </div>
  )
}
```

### `useUser()`

The following example demonstrates how to use the [useUser()](https://clerk.com/docs/react/reference/hooks/use-user.md) hook to access the [User](https://clerk.com/docs/react/reference/objects/user.md) object, which contains the current user's data such as their ID.

filename: src/pages/Example.tsx
```tsx
import { useUser } from '@clerk/react'

export default function Example() {
  const { isSignedIn, user, isLoaded } = useUser()

  // Handle loading state
  if (!isLoaded) return <div>Loading...</div>

  // Protect the page from unauthenticated users
  if (!isSignedIn) return <div>Sign in to view this page</div>

  return <div>Hello {user.id}!</div>
}
```

## Next steps

- [Create a custom sign-in-or-up page](https://clerk.com/docs/guides/development/custom-sign-in-or-up-page.md?sdk=react): Learn how to add a custom sign-in-or-up page to your React app with Clerk's prebuilt components.
- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=react): Learn how to quickly add authentication to your app using Clerk's suite of components.
- [Customization & localization](https://clerk.com/docs/guides/customizing-clerk/appearance-prop/overview.md?sdk=react): Learn how to customize and localize the Clerk components.
- [Clerk React SDK Reference](https://clerk.com/docs/reference/react/overview.md?sdk=react): Learn about the Clerk React SDK and how to integrate it into your app.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
