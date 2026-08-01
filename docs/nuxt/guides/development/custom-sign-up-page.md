# Build your own sign-up page for your Nuxt app with Clerk

By default, the [<SignIn />](https://clerk.com/docs/nuxt/reference/components/authentication/sign-in.md) component handles signing in and signing up, but if you'd like to have a dedicated sign-up page, this guide shows you how to use the [<SignUp />](https://clerk.com/docs/nuxt/reference/components/authentication/sign-up.md) component to build a custom sign-up page.

To set up a single sign-in-or-up page, follow the [custom sign-in-or-up page guide](https://clerk.com/docs/nuxt/guides/development/custom-sign-in-or-up-page.md).

> If prebuilt components don't meet your specific needs or if you require more control over the logic, you can rebuild the existing Clerk flows using the Clerk API. For more information, see the [custom flow guides](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=nuxt).

1. ## Build a sign-up page

   The following example demonstrates how to render the `<SignUp />` component on a dedicated sign-up page using a [Nuxt catch-all route](https://nuxt.com/docs/directory-structure/app/pages#catch-all-route).

   filename: app/pages/sign-up/[...slug].vue

   ```vue
   <template>
     <SignUp />
   </template>
   ```
2. ## Configure your sign-up page

   - Set the `CLERK_SIGN_UP_URL` environment variable to tell Clerk where the `<SignUp />` component is being hosted.

   There are other environment variables that you can set to customize Clerk's redirect behavior, such as `CLERK_SIGN_UP_FORCE_REDIRECT_URL`. Learn more about these environment variables and how to customize Clerk's redirect behavior in the [dedicated guide](https://clerk.com/docs/guides/development/customize-redirect-urls.md?sdk=nuxt).

   filename: .env

   ```env
   NUXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
   ```
3. ## Visit your new pages

   Run your project with the following command:

   ```npm
   npm run dev
   ```

   Visit your new custom page locally at [localhost:3000/sign-up](http://localhost:3000/sign-up).

## Next steps

Learn more about Clerk components, how to customize them, and how to use Clerk's client-side helpers using the following guides.

- [Read user data](https://clerk.com/docs/nuxt/guides/users/reading.md): Learn how to use Clerk's composables and helpers to read user data in your Nuxt app.
- [Client-side helpers](https://clerk.com/docs/reference/nuxt/overview.md?sdk=nuxt#client-side-helpers): Learn more about Clerk's client-side helpers and how to use them.
- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=nuxt): Learn how to quickly add authentication to your app using Clerk's suite of components.
- [Customization & localization](https://clerk.com/docs/guides/customizing-clerk/appearance-prop/overview.md?sdk=nuxt): Learn how to customize and localize Clerk components.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
