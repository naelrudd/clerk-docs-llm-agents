# <RedirectToOrganizationProfile /> (deprecated)

> This feature is deprecated. Please use the [redirectToOrganizationProfile() method](https://clerk.com/docs/nuxt/reference/objects/clerk.md#redirect-to-organization-profile) instead.

The `<RedirectToOrganizationProfile />` component will navigate to the Organization profile URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: App.vue
```vue
<script setup lang="ts">
// Components are automatically imported
</script>

<template>
  <Show when="signed-in">
    <RedirectToOrganizationProfile />
  </Show>
  <Show when="signed-out">
    <p>You need to sign in to view your Organization profile.</p>
  </Show>
</template>
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
