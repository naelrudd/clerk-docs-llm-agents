# $sessionStore

The `$sessionStore` store provides a convenient way to access the current user's [Session](https://clerk.com/docs/astro/reference/objects/session.md){{ target: '_blank' }} object, as well as helpers for setting the active session.

## How to use the `$sessionStore` store

The following example demonstrates how to use the [$sessionStore](https://clerk.com/docs/astro/reference/client-side-helpers/session-store.md) store to access the [Session](https://clerk.com/docs/astro/reference/objects/session.md) object. The `Session` object is used to access the `lastActiveAt` property, which is a `Date` object used to show the time the session was last active.

**React**

filename: session.tsx
```tsx
import { useStore } from '@nanostores/react'
import { $sessionStore } from '@clerk/astro/client'

export default function Session() {
  const session = useStore($sessionStore)

  if (session === undefined) {
    // Add logic to handle loading state
    return null
  }

  if (session === null) {
    // Add logic to handle not signed in state
    return null
  }

  return (
    <div>
      <p>This session has been active since {session.lastActiveAt.toLocaleString()}</p>
    </div>
  )
}
```

**Vue**

filename: session.vue
```vue
<script setup>
import { useStore } from '@nanostores/vue'
import { $sessionStore } from '@clerk/astro/client'

const session = useStore($sessionStore)
</script>

<template>
  <div v-if="session === undefined">
    <!-- Add logic to handle loading state -->
  </div>
  <div v-else-if="session === null">
    <!-- Add logic to handle not signed in state -->
  </div>
  <div v-else>
    <p>This session has been active since {{ session.lastActiveAt.toLocaleString() }}</p>
  </div>
</template>
```

**Svelte**

filename: session.svelte
```svelte
<script>
  // The $ prefix is reserved in Svelte for its own reactivity system.
  // Alias the imports to avoid conflicts.
  import { $sessionStore as session } from '@clerk/astro/client'
</script>

{#if $session === undefined}
  <!-- Add logic to handle loading state -->
{:else if $session === null}
  <!-- Add logic to handle not signed in state -->
{:else}
  <div>
    <p>This session has been active since {$session.lastActiveAt.toLocaleString()}</p>
  </div>
{/if}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
