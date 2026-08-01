# Read user data

Clerk provides [composables](https://clerk.com/docs/nuxt/reference/nuxt/overview.md#client-side-helpers) to read user data in your Nuxt application.

**For AI agents:** When wiring or testing these helpers, run `npx clerk@latest users list --json` to inspect the instance's existing user data, or create a test user with `npx clerk@latest users create --email <email> --password <password> --yes` (the password is required while password authentication is enabled, the default). Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md?sdk=nuxt) with `npx skills add clerk/skills` for correct CLI and SDK usage.

## Client-side

### `useAuth()`

The [useAuth()](https://clerk.com/docs/nuxt/reference/composables/use-auth.md) composable provides access to the current user's authentication state. It includes the `isSignedIn` property to check if the active user is signed in, which is helpful for protecting a page.

filename: app/pages/protected-page.vue
```vue
<script setup>
const { isSignedIn, isLoaded, userId } = useAuth()
</script>

<template>
  <!-- Use `isLoaded` to check if Clerk is loaded -->
  <div v-if="!isLoaded">Loading...</div>
  <!-- Use `isSignedIn` to check if the user is signed in -->
  <div v-else-if="!isSignedIn">Sign in to access this page</div>
  <!-- Use `userId` to access the current user's ID -->
  <div v-else>Hello, {{ userId }}!</div>
</template>
```

### `useUser()`

The [useUser()](https://clerk.com/docs/nuxt/reference/composables/use-user.md) composable provides access to the current user's [User](https://clerk.com/docs/nuxt/reference/objects/user.md) object, which contains the current user's data such as their ID. It also includes the `isSignedIn` property to check if the active user is signed in, which is helpful for protecting a page.

filename: GetCurrentUser.vue
```vue
<script setup>
import { useUser } from '@clerk/vue'

const { isSignedIn, user, isLoaded } = useUser()
</script>

<template>
  <!-- Use `isLoaded` to check if Clerk is loaded -->
  <div v-if="!isLoaded">Loading...</div>

  <!-- Use `isSignedIn` to check if the user is signed in -->
  <div v-else-if="!isSignedIn">Sign in to view this page</div>

  <div v-else>Hello {{ user?.id }}!</div>
</template>
```

## Server-side

The `Auth` object is available at `event.context.auth()` in your [event handlers](https://h3.unjs.io/guide/event-handler). This JavaScript object contains important authentication information like the current user's session ID, user ID, and Organization ID, and an `isAuthenticated` property to protect your API routes from unauthenticated users.

In some cases, you may need the full [`Backend User`](https://clerk.com/docs/reference/backend/types/backend-user.md?sdk=nuxt){{ target: '_blank' }} object of the currently active user. This is helpful if you want to render information, like their first and last name, directly from the server. The `clerkClient()` helper returns an instance of [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md?sdk=nuxt), which exposes Clerk's Backend API resources through methods such as the [`getUser()`](https://clerk.com/docs/reference/backend/user/get-user.md?sdk=nuxt){{ target: '_blank' }} method. This method returns the full `Backend User` object.

The following example uses the `Auth` object to access the `userId` and `isAuthenticated` properties. The `userId` is passed to the `getUser()` method to get the user's full `Backend User` object. The `isAuthenticated` property is used to protect the API route from unauthenticated users.

filename: server/api/auth/index.ts
```ts
import { clerkClient } from '@clerk/nuxt/server'

export default defineEventHandler(async (event) => {
  // Use `auth` to access the `isAuthenticated` and `userId` properties
  const { isAuthenticated, userId } = event.context.auth()

  // Protect the API route by checking if the user is signed in
  if (!isAuthenticated) {
    // Add logic to handle unauthenticated users:
    throw createError({
      statusCode: 401,
      statusMessage: 'Unauthorized: No user ID provided',
    })
  }

  // Get the user's full `Backend User` object
  const user = await clerkClient(event).users.getUser(userId)

  return user
})
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
