# useSessionList()

The `useSessionList()` hook returns an array of [Session](https://clerk.com/docs/electron/reference/objects/session.md) objects that have been registered on the client device.

## Returns

There are multiple variants of this type available which you can select by clicking on one of the tabs.

**Initialization**

| Name        | Type        | Description                                                                                                                                                                                                                                                                                                   |
| ----------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `isLoaded`  | `false`     | Indicates whether Clerk has loaded the current authentication state. Initially `false`, becomes `true` once Clerk loads, and can revert to `false` while auth state is updating (e.g., when switching organizations via [setActive()](https://clerk.com/docs/electron/reference/objects/clerk.md#setactive)). |
| `sessions`  | `undefined` | A list of sessions that have been registered on the client device.                                                                                                                                                                                                                                            |
| `setActive` | `undefined` | A function that sets the active session and/or Organization. See the [reference doc](https://clerk.com/docs/electron/reference/objects/clerk.md#setactive).                                                                                                                                                   |

**Loaded**

| Name          | Type                                                                                                                                                | Description                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `isLoaded`    | `true`                                                                                                                                              | Indicates whether Clerk has loaded the current authentication state. Initially `false`, becomes `true` once Clerk loads, and can revert to `false` while auth state is updating (e.g., when switching organizations via [setActive()](https://clerk.com/docs/electron/reference/objects/clerk.md#setactive)). |
| `sessions`    | <code><a href="https://clerk.com/docs/electron/reference/objects/session.md">SessionResource</a>[]</code>                                           | A list of sessions that have been registered on the client device.                                                                                                                                                                                                                                            |
| `setActive()` | <code>(setActiveParams: <a href="https://clerk.com/docs/electron/reference/types/set-active-params.md">SetActiveParams</a>) => Promise<void></code> | A function that sets the active session and/or Organization. See the [reference doc](https://clerk.com/docs/electron/reference/objects/clerk.md#setactive).                                                                                                                                                   |

## Example

### Get a list of sessions

The following example uses `useSessionList()` to get a list of sessions that have been registered on the client device. The `sessions` property is used to show the number of times the user has visited the page.

filename: src/App.tsx
```tsx
import { useSessionList } from '@clerk/electron/react'

export default function Home() {
  const { isLoaded, sessions } = useSessionList()

  // Handle loading state
  if (!isLoaded) return <div>Loading...</div>

  return (
    <div>
      <p>Welcome back. You've been here {sessions.length} times before.</p>
    </div>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
