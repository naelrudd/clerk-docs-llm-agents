# useSignUp()

> This hook uses our legacy API, which will be removed in a future release. We recommend migrating to the new [useSignUp()](https://clerk.com/docs/react/reference/hooks/use-sign-up.md) hook instead.

The `useSignUp()` hook provides access to the [SignUp](https://clerk.com/docs/react/reference/objects/sign-up.md) object, which allows you to check the current state of a sign-up attempt and manage the sign-up flow. You can use this to create a custom sign-up flow.

## Returns

There are multiple variants of this type available which you can select by clicking on one of the tabs.

**Initialization**

| Name        | Type        | Description                                                                                                                                                                                                                                                                                                 |
| ----------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `isLoaded`  | `false`     | Indicates whether Clerk has loaded the current authentication state. Initially `false`, becomes `true` once Clerk loads, and can revert to `false` while auth state is updating (e.g., when switching organizations via [setActive()](https://clerk.com/docs/react/reference/objects/clerk.md#set-active)). |
| `setActive` | `undefined` | A function that sets the active session. See the [reference doc](https://clerk.com/docs/react/reference/objects/clerk.md#set-active).                                                                                                                                                                       |
| `signUp`    | `undefined` | An object that contains the current sign-up attempt status and methods to create a new sign-up attempt.                                                                                                                                                                                                     |

**Loaded**

| Name          | Type                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                 |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `isLoaded`    | `true`                                                                                                                                           | Indicates whether Clerk has loaded the current authentication state. Initially `false`, becomes `true` once Clerk loads, and can revert to `false` while auth state is updating (e.g., when switching organizations via [setActive()](https://clerk.com/docs/react/reference/objects/clerk.md#set-active)). |
| `setActive()` | <code>(setActiveParams: <a href="https://clerk.com/docs/react/reference/types/set-active-params.md">SetActiveParams</a>) => Promise<void></code> | A function that sets the active session. See the [reference doc](https://clerk.com/docs/react/reference/objects/clerk.md#set-active).                                                                                                                                                                       |
| `signUp`      | [SignUpResource](https://clerk.com/docs/react/reference/objects/sign-up.md)                                                                      | An object that contains the current sign-up attempt status and methods to create a new sign-up attempt.                                                                                                                                                                                                     |

## Examples

### Check the current state of a sign-up

The following example uses the `useSignUp()` hook to access the [SignUp](https://clerk.com/docs/react/reference/objects/sign-up.md) object, which contains the current sign-up attempt status and methods to create a new sign-up attempt. The `isLoaded` property is used to handle the loading state.

filename: src/pages/SignUpPage.tsx
```tsx
import { useSignUp } from '@clerk/react/legacy'

export default function SignUpPage() {
  const { isLoaded, signUp } = useSignUp()

  // Handle loading state
  if (!isLoaded) return <div>Loading...</div>

  return <div>The current sign-up attempt status is {signUp?.status}.</div>
}
```

### Create a custom sign-up flow with `useSignUp()`

The `useSignUp()` hook can also be used to build fully custom sign-up flows, if Clerk's prebuilt components don't meet your specific needs or if you require more control over the authentication flow. Different sign-up flows include email and password, email and phone codes, email links, and multifactor (MFA). To learn more about using the `useSignUp()` hook to create custom flows, see the [custom flow guides](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=react).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
