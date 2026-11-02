# updateClerkOptions()

The `updateClerkOptions()` function is used to update Clerk's options at runtime. It can be called at any time after [Clerk has been initialized](https://clerk.com/docs/nuxt/reference/integration.md). The `@clerk/nuxt` module auto-imports `updateClerkOptions()`, so you don't need to import it yourself.

## Usage

The following example changes the language of Clerk's components when the user selects a different language. It uses [`@clerk/localizations`](https://clerk.com/docs/guides/customizing-clerk/localization.md?sdk=nuxt) to pass the selected language to the `localization` option.

filename: app/components/LanguageSwitcher.vue
```vue
<script setup lang="ts">
import { enUS, esES, frFR } from '@clerk/localizations'

const localizations = {
  'en-US': enUS,
  'es-ES': esES,
  'fr-FR': frFR,
}

const locale = ref<keyof typeof localizations>('en-US')

watch(locale, (newLocale) => {
  updateClerkOptions({
    localization: localizations[newLocale],
  })
})
</script>

<template>
  <select v-model="locale">
    <option value="en-US">English</option>
    <option value="es-ES">Español</option>
    <option value="fr-FR">Français</option>
  </select>
</template>
```

## Properties

| Name          | Type                      | Description                                                                                            |
| ------------- | ------------------------- | ------------------------------------------------------------------------------------------------------ |
| appearance?   | Appearance | undefined   | An object to style your components. Will only affect Clerk components and not Account Portal pages.    |
| localization? | Localization | undefined | An object to localize your components. Will only affect Clerk components and not Account Portal pages. |

[components-ref]: /docs/reference/components/overview

[ap-ref]: /docs/guides/account-portal/overview

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
