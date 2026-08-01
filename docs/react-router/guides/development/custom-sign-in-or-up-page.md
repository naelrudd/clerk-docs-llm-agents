# Build your own sign-in-or-up page for your React Router app with Clerk

This guide shows you how to use the [<SignIn />](https://clerk.com/docs/react-router/reference/components/authentication/sign-in.md) component to build a custom page **that allows users to sign in or sign up within a single flow**.

To set up separate sign-in and sign-up pages, follow this guide, and then follow the [custom sign-up page guide](https://clerk.com/docs/react-router/guides/development/custom-sign-up-page.md).

> If prebuilt components don't meet your specific needs or if you require more control over the logic, you can rebuild the existing Clerk flows using the Clerk API. For more information, see the [custom flow guides](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=react-router).

1. ## Build a sign-in-or-up page

   The following example demonstrates how to render the [<SignIn />](https://clerk.com/docs/react-router/reference/components/authentication/sign-in.md) component on a dedicated page using the [React Router Splat route](https://reactrouter.com/start/framework/routing#splats).

   filename: app/routes/sign-in.tsx

   ```tsx
   import { SignIn } from '@clerk/react-router'

   export default function SignInPage() {
     return (
       <div>
         <h1>Sign in or up route</h1>
         <SignIn />
       </div>
     )
   }
   ```
2. ## Configure routes

   React Router expects you to define routes in [`app/routes.ts`](https://reactrouter.com/start/framework/routing). Add the previously created sign-in-or-up page to your route configuration.

   filename: app/routes.ts

   ```tsx
   import { type RouteConfig, index, route } from '@react-router/dev/routes'

   export default [
     index('routes/home.tsx'),
     route('sign-in/*', 'routes/sign-in.tsx'),
   ] satisfies RouteConfig
   ```
3. ## Configure redirect behavior

   - Set the `CLERK_SIGN_IN_URL` environment variable to tell Clerk where the `<SignIn />` component is being hosted.
   - Set `CLERK_SIGN_IN_FALLBACK_REDIRECT_URL` as a fallback URL incase users visit the `/sign-in` route directly.
   - Set `CLERK_SIGN_UP_FALLBACK_REDIRECT_URL` as a fallback URL incase users select the 'Don't have an account? Sign up' link at the bottom of the component.

   Learn more about these environment variables and how to customize Clerk's redirect behavior in the [dedicated guide](https://clerk.com/docs/guides/development/customize-redirect-urls.md?sdk=react-router).

   filename: .env

   ```env
   CLERK_SIGN_IN_URL=/sign-in
   CLERK_SIGN_IN_FALLBACK_REDIRECT_URL=/
   CLERK_SIGN_UP_FALLBACK_REDIRECT_URL=/
   ```
4. ## Visit your new page

   Run your project with the following command:

   ```npm
   npm run dev
   ```

   Visit your new custom page locally at [localhost:5173/sign-in](http://localhost:5173/sign-in).

## Next steps

Learn more about Clerk components, how to use them to create custom pages, and how to use Clerk's client-side helpers using the following guides.

- [Create a custom sign-up page](https://clerk.com/docs/react-router/guides/development/custom-sign-up-page.md): Learn how to add a custom sign-up page to your React Router app with Clerk's components.
- [Read user data](https://clerk.com/docs/react-router/guides/users/reading.md): Learn how to use Clerk's hooks and helpers to read user data in your React Router app.
- [Client-side helpers](https://clerk.com/docs/reference/react-router/overview.md?sdk=react-router#client-side-helpers): Learn more about Clerk's client-side helpers and how to use them.
- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=react-router): Learn how to quickly add authentication to your app using Clerk's suite of components.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
