# Nuxt Quickstart

**Example Repository**

- [Nuxt Quickstart Repo](https://github.com/clerk/clerk-nuxt-quickstart)

1. ## Create a new Nuxt app

   If you don't already have a Nuxt app, run the following commands to [create a new one](https://nuxt.com/docs/4.x/getting-started/installation).

   ```npm
   npm create nuxt@latest clerk-nuxt
   cd clerk-nuxt
   ```
2. ## Install `@clerk/nuxt`

   The [Clerk Nuxt SDK](https://clerk.com/docs/nuxt/reference/nuxt/overview.md) gives you access to prebuilt components, Vue composables, and helpers to make user authentication easier.

   Run the following command to install the SDK:

   ```npm
   npm install @clerk/nuxt
   ```

   ## Set your Clerk API keys

   Add the following keys to your `.env` file. These keys can always be retrieved from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

   filename: .env

   ```env
   NUXT_PUBLIC_CLERK_PUBLISHABLE_KEY={{pub_key}}
   NUXT_CLERK_SECRET_KEY={{secret}}
   ```
3. ## Configure `nuxt.config.ts`

   To enable Clerk in your Nuxt app, add `@clerk/nuxt` to your modules array in `nuxt.config.ts`. This automatically configures Clerk's middleware and plugins and imports Clerk's components.

   filename: nuxt.config.ts

   ```ts
   export default defineNuxtConfig({
     modules: ['@clerk/nuxt'],
   })
   ```
4. ## Create a header with Clerk components

   Nuxt automatically imports and makes all components in the `components/` directory globally available without requiring explicit imports. See the [Nuxt docs](https://nuxt.com/docs/guide/concepts/auto-imports) for details.

   You can control which content signed-in and signed-out users can see with Clerk's [prebuilt control components](https://clerk.com/docs/nuxt/reference/components/overview.md#control-components).

   The following example creates a header using the following components:

   - [<Show when="signed-in">](https://clerk.com/docs/nuxt/reference/components/control/show.md): Children of this component can only be seen while **signed in**.
   - [<Show when="signed-out">](https://clerk.com/docs/nuxt/reference/components/control/show.md): Children of this component can only be seen while **signed out**.
   - [<UserButton />](https://clerk.com/docs/nuxt/reference/components/user/user-button.md): Shows the signed-in user's avatar. Selecting it opens a dropdown menu with account management options.
   - [<SignInButton />](https://clerk.com/docs/nuxt/reference/components/unstyled/sign-in-button.md): An unstyled component that links to the sign-in page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=nuxt) are set for the sign-in URL, this component links to the [Account Portal sign-in page](https://clerk.com/docs/guides/account-portal/overview.md?sdk=nuxt#sign-in).
   - [<SignUpButton />](https://clerk.com/docs/nuxt/reference/components/unstyled/sign-up-button.md): An unstyled component that links to the sign-up page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=nuxt) are set for the sign-up URL, this component links to the [Account Portal sign-up page](https://clerk.com/docs/guides/account-portal/overview.md?sdk=nuxt#sign-up).

   filename: app/app.vue

   ```vue
   <script setup lang="ts">
   // Components are automatically imported
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

     <main>
       <NuxtPage />
     </main>
   </template>
   ```
5. ## Run your project

   Run your project with the following command:

   ```npm
   npm run dev
   ```
6. ## Create your first user

   1. Visit your app's homepage at http://localhost:3000.
   2. Select "Sign up" on the page and authenticate to create your first user.

   > To make configuration changes to your Clerk development instance, claim the Clerk keys that were generated for you by selecting **Configure your application** in the bottom right of your app. This will associate the application with your Clerk account. Once claimed, you can find your Publishable Key and Secret Key any time on the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

## Next steps

Explore the most relevant next steps for your SDK using the following guides.

- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=nuxt): Learn how to add Clerk's prebuilt authentication and user-management UI to your app.
- [Build custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=nuxt): Learn how to build custom user interfaces entirely from scratch using the Clerk API.
- [Read user data](https://clerk.com/docs/guides/users/reading.md?sdk=nuxt): Learn how to use Clerk's helpers to read user data in your app.
- [Protect API routes with clerkMiddleware()](https://clerk.com/docs/reference/nuxt/clerk-middleware.md?sdk=nuxt): Learn how to protect API routes from unauthenticated users.

## More to explore

Explore additional Clerk features that help you build, manage, and grow your application.

- [**Organizations**](https://clerk.com/docs/guides/organizations/overview.md?sdk=nuxt) - Organizations are shared accounts that let teams collaborate, manage members and roles, and control access to shared resources.
- [**Billing**](https://clerk.com/docs/guides/billing/overview.md?sdk=nuxt) - Billing enables you to manage subscriptions, free trials, payments, plans, and billing-related webhook events for B2C and B2B applications.
- [**Waitlist**](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=nuxt#waitlist) - Waitlist lets you collect signups and control access to new products or features before launch through a simple, integrated workflow.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
