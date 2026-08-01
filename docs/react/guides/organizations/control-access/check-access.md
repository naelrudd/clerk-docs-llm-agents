# Check Roles and Permissions with Authorization Checks

Authorization checks are checks you perform in your code to determine the access rights and privileges of a user, ensuring they have the necessary Permissions to perform specific actions or access certain content. These checks are essential for protecting sensitive data, gating premium features, and ensuring users stay within their allowed scope of access.

Within Organizations, authorization checks can be performed by checking a user's Roles or Custom Permissions. Roles like `org:admin` determine a user's level of access within an Organization, while Custom Permissions like `org:invoices:create` provide fine-grained control over specific features and actions.

## Examples

You can protect content and even entire routes based on Organization membership, Roles, and Permissions by performing authorization checks.

In the following example, the page is restricted to authenticated users, users who have the `org:admin` Role, and users who belong to the `Acme Corp` Organization. It uses the [`has()`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=react#has) helper to perform the authorization check for the `org:admin` Role.

filename: src/Protected.tsx
```tsx
import { useAuth, useOrganization } from '@clerk/react'

export default function Protected() {
  // The `useAuth()` hook gives you access to properties like `isSignedIn` and `has()`
  const { isSignedIn, has } = useAuth()
  const { organization } = useOrganization()

  // Check if the user is authenticated
  if (!isSignedIn) return <p>You must be signed in to access this page.</p>

  // Check if there is an Active Organization
  if (!organization) return <p>Set an Active Organization to access this page.</p>

  // Check if the user has the `org:admin` Role
  if (!has({ role: 'org:admin' })) return <p>You must be an admin to access this page.</p>

  // Check if Organization name matches (e.g., 'Acme Corp')
  const requiredOrgName = 'Acme Corp'
  if (organization.name !== requiredOrgName) {
    return (
      <>
        <p>
          This page is only accessible in the <strong>{requiredOrgName}</strong> Organization.
          Switch to the <strong>{requiredOrgName}</strong> Organization to access this page.
        </p>
      </>
    )
  }

  return (
    <p>
      You are currently signed in as an <strong>admin</strong> in the{' '}
      <strong>{organization.name}</strong> Organization.
    </p>
  )
}
```

Update your main `<App />` component to show the `<Protected />` component when you navigate to `/protected`.

filename: src/App.tsx
```tsx
  import './App.css'
  import { Show, SignInButton, UserButton, OrganizationSwitcher, useOrganization } from '@clerk/react'
  import Protected from './Protected'

  function App() {
    const { organization, membership } = useOrganization()

    return (
      <>
        <header>
          <OrganizationSwitcher />
          <Show when="signed-out">
            <SignInButton />
          </Show>
          <Show when="signed-in">
            <UserButton />
          </Show>
        </header>
        <main className="p-8">
+         {window.location.pathname === '/protected' ? (
+           <Protected />
+         ) : (
            <Show when="signed-in">
              <div>
                <h1 className="text-2xl font-bold mb-4">
                  Welcome to the <strong>{organization?.name}</strong> Organization
                </h1>
                <p className="mb-6">
                  Your Role in this Organization: <strong>{membership?.role}</strong>
                </p>
              </div>
            </Show>
          )}
        </main>
      </>
    )
  }

  export default App
```

For more examples on how to perform authorization checks, see the [dedicated guide](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=react).

## Next steps

Now that you know how to check Roles and Permissions, you can:

- [Perform authorization checks](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=react): Learn how to perform authorization checks to limit access to content or entire routes based on a user's Role or Permissions.
- [Features and Plans](https://clerk.com/docs/guides/billing/for-b2b.md?sdk=react#control-access-with-features-plans-and-permissions): Learn how to check Features and Plans for Subscription-based applications.
- [Set up Roles and Permissions](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react): Learn how to set up Roles and Permissions to control what invited users can access.
- [Configure default Roles](https://clerk.com/docs/guides/organizations/configure.md?sdk=react#default-roles): Learn how to configure default Roles for new Organization members.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
