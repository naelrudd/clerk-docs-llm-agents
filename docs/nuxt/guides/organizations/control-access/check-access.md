# Check Roles and Permissions with Authorization Checks

Authorization checks are checks you perform in your code to determine the access rights and privileges of a user, ensuring they have the necessary Permissions to perform specific actions or access certain content. These checks are essential for protecting sensitive data, gating premium features, and ensuring users stay within their allowed scope of access.

Within Organizations, authorization checks can be performed by checking a user's Roles or Custom Permissions. Roles like `org:admin` determine a user's level of access within an Organization, while Custom Permissions like `org:invoices:create` provide fine-grained control over specific features and actions.

## Examples

You can protect content and even entire routes based on Organization membership, Roles, and Permissions by performing authorization checks.

In the following example, the page is restricted to authenticated users, users who have the `org:admin` Role, and users who belong to the `Acme Corp` Organization. It uses the [`has()`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=nuxt#has) helper to perform the authorization check for the `org:admin` Role.

**Server-side**

filename: server/api/organization.ts
```ts
import { clerkClient } from '@clerk/nuxt/server'

export default defineEventHandler(async (event) => {
  // Use `event.context.auth()` to access the `Auth` object
  // https://clerk.com/docs/reference/backend/types/auth-object
  const { isAuthenticated, orgId, has } = event.context.auth()
  const requiredOrgName = 'Acme Corp'

  // Check if the user is authenticated
  if (!isAuthenticated) {
    throw createError({
      statusCode: 401,
      statusMessage: 'Unauthorized: No user ID provided',
    })
  }

  // Check if there is an Active Organization
  if (!orgId) {
    throw createError({
      statusCode: 404,
      statusMessage: 'Set an Active Organization to access this page.',
    })
  }

  // Check if the user has the `org:admin` Role
  if (!has({ role: 'org:admin' })) {
    throw createError({
      statusCode: 403,
      statusMessage: 'You must be an admin to access this page.',
    })
  }

  // Use the `getOrganization()` method to get the Backend `Organization` object
  const organization = await clerkClient(event).organizations.getOrganization({
    organizationId: orgId,
  })

  // Check if Organization name matches (e.g., 'Acme Corp')
  if (organization.name !== requiredOrgName) {
    throw createError({
      statusCode: 403,
      statusMessage: `This route is only accessible in the ${requiredOrgName} Organization.`,
    })
  }

  return {
    organization,
  }
})
```

**Client-side**

filename: app/pages/index.vue
```vue
<script setup lang="ts">
// Composables are auto-imported from @clerk/nuxt
// The `useAuth()` hook gives you access to properties like `isSignedIn` and `has()`
const { isSignedIn, has } = useAuth()
const { organization } = useOrganization()

const requiredOrgName = 'Acme Corp'
</script>

<template>
  <!-- Check if the user is authenticated -->
  <div v-if="!isSignedIn">
    <p>You must be signed in to access this page.</p>
  </div>

  <!-- Check if there is an Active Organization -->
  <div v-else-if="!organization">
    <p>Set an Active Organization to access this page.</p>
  </div>

  <!-- Check if the user has the `org:admin` Role -->
  <div v-else-if="!has?.({ role: 'org:admin' })">
    <p>You must be an admin to access this page.</p>
  </div>

  <!-- Check if Organization name matches (e.g., 'Acme Corp') -->
  <div v-else-if="organization.name !== requiredOrgName">
    <p>
      This page is only accessible in the <strong>{{ requiredOrgName }}</strong> Organization.
      Switch to the <strong>{{ requiredOrgName }}</strong> Organization to access this page.
    </p>
  </div>

  <div v-else>
    <p>
      You are currently signed in as an <strong>admin</strong> in the
      <strong>{{ organization.name }}</strong> Organization.
    </p>
  </div>
</template>
```

In the client-side example, when a user isn't in the required Organization, render an [<OrganizationSwitcher />](https://clerk.com/docs/nuxt/reference/components/organization/organization-switcher.md) alongside the message to let them switch to the required Organization. The server-side example is an API route that throws an HTTP error instead of rendering a message, so render the `<OrganizationSwitcher />` in the client UI that consumes the route.

For more examples on how to perform authorization checks, see the [dedicated guide](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=nuxt).

## Next steps

Now that you know how to check Roles and Permissions, you can:

- [Perform authorization checks](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=nuxt): Learn how to perform authorization checks to limit access to content or entire routes based on a user's Role or Permissions.
- [Features and Plans](https://clerk.com/docs/guides/billing/for-b2b.md?sdk=nuxt#control-access-with-features-plans-and-permissions): Learn how to check Features and Plans for Subscription-based applications.
- [Set up Roles and Permissions](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=nuxt): Learn how to set up Roles and Permissions to control what invited users can access.
- [Configure default Roles](https://clerk.com/docs/guides/organizations/configure.md?sdk=nuxt#default-roles): Learn how to configure default Roles for new Organization members.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
