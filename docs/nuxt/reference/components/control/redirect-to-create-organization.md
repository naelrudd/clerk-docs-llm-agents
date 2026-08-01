# <RedirectToCreateOrganization /> (deprecated)

> This feature is deprecated. Please use the [redirectToCreateOrganization() method](https://clerk.com/docs/nuxt/reference/objects/clerk.md#redirect-to-create-organization) instead.

The `<RedirectToCreateOrganization />` component will navigate to the create Organization flow which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: App.vue
```vue
<script setup lang="ts">
// Components are automatically imported
</script>

<template>
  <Show when="signed-in">
    <RedirectToCreateOrganization />
  </Show>
  <Show when="signed-out">
    <p>You need to sign in to create an Organization.</p>
  </Show>
</template>
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
