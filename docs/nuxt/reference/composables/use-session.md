# useSession() | Vue

The `useSession()` composable provides access to the current user's [Session](https://clerk.com/docs/nuxt/reference/objects/session.md) object, as well as helpers for setting the active session.

## Returns

| Name       | Type          | Description                                                                                                        |
| ---------- | ------------- | ------------------------------------------------------------------------------------------------------------------ |
| isLoaded   | Ref<boolean> | A boolean that indicates whether Clerk has finished loading and initializing. Returns false during initialization. |
| isSignedIn | Ref<boolean> | A boolean that indicates whether a user is currently signed in.                                                    |
| session    | Ref<Session> | The current session for the user.                                                                                  |

## How to use the `useSession()` composable

### Access the `Session` object

The following example uses the [useSession()](https://clerk.com/docs/nuxt/reference/composables/use-session.md) composable to access the [Session](https://clerk.com/docs/nuxt/reference/objects/session.md) object. The `Session` object is used to access the `lastActiveAt` property, which is a `Date` object used to show the time the session was last active.

filename: SessionStatus.vue
```vue
<script setup>
import { useSession } from '@clerk/vue'

const { isLoaded, session, isSignedIn } = useSession()
</script>

<template>
  <div v-if="!isLoaded">
    <!-- Handle loading state -->
  </div>

  <div v-else-if="!isSignedIn">
    <!-- Handle signed out state -->
  </div>

  <div v-else>
    <p>This session has been active since {{ session.lastActiveAt.toLocaleString() }}</p>
  </div>
</template>
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
