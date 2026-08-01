# <RedirectToSignIn />

The `<RedirectToSignIn />` component will navigate to the sign in URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: App.vue
```vue
<script setup lang="ts">
// Components are automatically imported
</script>

<template>
  <Show when="signed-in">
    <UserButton />
  </Show>
  <Show when="signed-out">
    <RedirectToSignIn />
  </Show>
</template>
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
