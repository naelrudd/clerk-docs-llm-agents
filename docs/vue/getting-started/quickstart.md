# Vue Quickstart

**Example Repository**

- [Vue Quickstart Repo](https://github.com/clerk/clerk-vue-quickstart)

**Before you start**

- [Set up a Clerk application](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md?sdk=vue)

This tutorial assumes that you're using [Vue 3](https://vuejs.org/) with [TypeScript](https://www.typescriptlang.org/).

1. ## Create a new Vue app

   If you don't already have a Vue app, run the following commands to [create a new one using Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project):

   ```npm
   npm create vite@latest clerk-vue -- --template vue-ts
   cd clerk-vue
   npm install
   ```
2. ## Install `@clerk/vue`

   The [Clerk Vue SDK](https://clerk.com/docs/vue/reference/vue/overview.md) gives you access to prebuilt components, composables, and helpers to make user authentication easier.

   Run the following command to install the SDK:

   ```npm
   npm install @clerk/vue
   ```
3. ## Set your Clerk API keys

   Add your Clerk Publishable Key to your `.env` file.

   1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page.
   2. In the **Quick Copy** section, copy your Clerk Publishable Key.
   3. Paste your key into your `.env` file.

   The final result should resemble the following:

   filename: .env

   ```env
   VITE_CLERK_PUBLISHABLE_KEY={{pub_key}}
   ```
4. ## Add `clerkPlugin` to your app

   [clerkPlugin](https://clerk.com/docs/vue/reference/vue/clerk-plugin.md) provides session and user context to Clerk's components and composables. It's required to pass your Clerk Publishable Key as an option. You can add an `if` statement to check that the key is imported properly. This prevents the app from running without the Publishable Key and catches TypeScript errors.

   The `clerkPlugin` accepts optional options, such as `{ signInForceRedirectUrl: '/dashboard' }`.

   filename: src/main.ts

   ```ts
   import { createApp } from 'vue'
   import './style.css'
   import App from './App.vue'
   import { clerkPlugin } from '@clerk/vue'

   const PUBLISHABLE_KEY = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

   if (!PUBLISHABLE_KEY) {
     throw new Error('Add your Clerk Publishable Key to the .env file')
   }

   const app = createApp(App)
   app.use(clerkPlugin, { publishableKey: PUBLISHABLE_KEY })
   app.mount('#app')
   ```
5. ## Create a header with Clerk components

   You can control which content signed-in and signed-out users can see with Clerk's [prebuilt control components](https://clerk.com/docs/vue/reference/components/overview.md#control-components). The following example creates a header using the following components:

   - [<Show when="signed-in">](https://clerk.com/docs/vue/reference/components/control/show.md): Children of this component can only be seen while **signed in**.
   - [<Show when="signed-out">](https://clerk.com/docs/vue/reference/components/control/show.md): Children of this component can only be seen while **signed out**.
   - [<UserButton />](https://clerk.com/docs/vue/reference/components/user/user-button.md): Shows the signed-in user's avatar. Selecting it opens a dropdown menu with account management options.
   - [<SignInButton />](https://clerk.com/docs/vue/reference/components/unstyled/sign-in-button.md): An unstyled component that links to the sign-in page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=vue) are set for the sign-in URL, this component links to the [Account Portal sign-in page](https://clerk.com/docs/guides/account-portal/overview.md?sdk=vue#sign-in).
   - [<SignUpButton />](https://clerk.com/docs/vue/reference/components/unstyled/sign-up-button.md): An unstyled component that links to the sign-up page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=vue) are set for the sign-up URL, this component links to the [Account Portal sign-up page](https://clerk.com/docs/guides/account-portal/overview.md?sdk=vue#sign-up).

   filename: src/App.vue

   ```vue
   <script setup lang="ts">
   import { Show, SignInButton, SignUpButton, UserButton } from '@clerk/vue'
   </script>

   <template>
     <header>
       <Show when="signed-out">
         <SignInButton />
         <SignUpButton />
       </Show>
       <Show when="signed-in">
         <UserButton />
       </Show>
     </header>
   </template>
   ```
6. ## Run your project

   Run your project with the following command:

   ```npm
   npm run dev
   ```
7. ## Create your first user

   1. Visit your app's homepage at http://localhost:5173.
   2. Select "Sign up" on the page and authenticate to create your first user.

## Next steps

Explore the most relevant next steps for your SDK using the following guides.

- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=vue): Learn how to add Clerk's prebuilt authentication and user-management UI to your app.
- [Build custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=vue): Learn how to build custom user interfaces entirely from scratch using the Clerk API.
- [Client-side helpers (composables)](https://clerk.com/docs/reference/vue/overview.md?sdk=vue#custom-composables): Learn more about Clerk's client-side helpers and how to use them.
- [Update Clerk options at runtime](https://clerk.com/docs/reference/vue/update-clerk-options.md?sdk=vue): Learn how to update Clerk's options at runtime in your Vue app.

## More to explore

Explore additional Clerk features that help you build, manage, and grow your application.

- [**Organizations**](https://clerk.com/docs/guides/organizations/overview.md?sdk=vue) - Organizations are shared accounts that let teams collaborate, manage members and roles, and control access to shared resources.
- [**Billing**](https://clerk.com/docs/guides/billing/overview.md?sdk=vue) - Billing enables you to manage subscriptions, free trials, payments, plans, and billing-related webhook events for B2C and B2B applications.
- [**Waitlist**](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=vue#waitlist) - Waitlist lets you collect signups and control access to new products or features before launch through a simple, integrated workflow.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
