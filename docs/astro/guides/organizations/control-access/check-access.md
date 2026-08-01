# Check Roles and Permissions with Authorization Checks

Authorization checks are checks you perform in your code to determine the access rights and privileges of a user, ensuring they have the necessary Permissions to perform specific actions or access certain content. These checks are essential for protecting sensitive data, gating premium features, and ensuring users stay within their allowed scope of access.

Within Organizations, authorization checks can be performed by checking a user's Roles or Custom Permissions. Roles like `org:admin` determine a user's level of access within an Organization, while Custom Permissions like `org:invoices:create` provide fine-grained control over specific features and actions.

## Examples

You can protect content and even entire routes based on Organization membership, Roles, and Permissions by performing authorization checks.

In the following example, the page is restricted to authenticated users, users who have the `org:admin` Role, and users who belong to the `Acme Corp` Organization. It uses the [`has()`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=astro#has) helper to perform the authorization check for the `org:admin` Role.

**Server-side**

filename: src/pages/protected.astro
```astro
---
import Layout from '../layouts/Layout.astro'
import { clerkClient } from '@clerk/astro/server'

// Use the `locals.auth()` local to access the `Auth` object
// https://clerk.com/docs/reference/backend/types/auth-object
const { isAuthenticated, has, orgId } = Astro.locals.auth()

const requiredOrgName = 'Acme Corp'

// Check if the user has the `org:admin` Role
const isAdmin = has({ role: 'org:admin' })

// Use the `getOrganization()` method to get the Backend `Organization` object,
// but only once every access check has passed
let organization = null
if (isAuthenticated && orgId && isAdmin) {
  organization = await clerkClient(Astro).organizations.getOrganization({ organizationId: orgId })
}
---

<Layout title="Protected Page">
  {
    /* Show the appropriate message based on the user's authentication, Active Organization, and Role */
    !isAuthenticated ? (
      <p>You must be signed in to access this page.</p>
    ) : !orgId ? (
      <p>Set an Active Organization to access this page.</p>
    ) : !isAdmin ? (
      <p>You must be an admin to access this page.</p>
    ) : organization.name !== requiredOrgName ? (
      <p>
        This page is only accessible in the <strong>{requiredOrgName}</strong> Organization. Switch
        to the <strong>{requiredOrgName}</strong> Organization to access this page.
      </p>
    ) : (
      <p>
        You are currently signed in as an <strong>admin</strong> in the{' '}
        <strong>{organization.name}</strong> Organization.
      </p>
    )
  }
</Layout>
```

**Client-side**

filename: components/Home.tsx
```tsx
import { useStore } from '@nanostores/react'
import { $organizationStore } from '@clerk/astro/client'
import { useAuth } from '@clerk/astro/react'

export default function Home() {
  const organization = useStore($organizationStore)
  // The `useAuth()` hook gives you access to properties like `isSignedIn` and `has()`
  const { has, isSignedIn } = useAuth()
  const requiredOrgName = 'Acme Corp'

  // Check if the user is authenticated
  if (!isSignedIn) return <p>You must be signed in to access this page.</p>

  // Handle loading state
  if (organization === undefined) return <p>Loading...</p>

  // Check if there is an Active Organization
  if (organization === null) return <p>Set an Active Organization to access this page.</p>

  // Check if the user has the `org:admin` Role
  if (!has({ role: 'org:admin' })) {
    return <p>You must be an admin to access this page.</p>
  }

  // Check if Organization name matches (e.g., 'Acme Corp')
  if (organization.name !== requiredOrgName) {
    return (
      <p>
        This page is only accessible in the <strong>{requiredOrgName}</strong> Organization. Switch
        to the <strong>{requiredOrgName}</strong> Organization to access this page.
      </p>
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

When a user isn't in the required Organization, render an [<OrganizationSwitcher />](https://clerk.com/docs/astro/reference/components/organization/organization-switcher.md) alongside the message to let them switch to the required Organization.

For more examples on how to perform authorization checks, see the [dedicated guide](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=astro).

## Next steps

Now that you know how to check Roles and Permissions, you can:

- [Perform authorization checks](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=astro): Learn how to perform authorization checks to limit access to content or entire routes based on a user's Role or Permissions.
- [Features and Plans](https://clerk.com/docs/guides/billing/for-b2b.md?sdk=astro#control-access-with-features-plans-and-permissions): Learn how to check Features and Plans for Subscription-based applications.
- [Set up Roles and Permissions](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=astro): Learn how to set up Roles and Permissions to control what invited users can access.
- [Configure default Roles](https://clerk.com/docs/guides/organizations/configure.md?sdk=astro#default-roles): Learn how to configure default Roles for new Organization members.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
