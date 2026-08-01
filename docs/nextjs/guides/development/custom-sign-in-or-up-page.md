# Build your own sign-in-or-up page for your Next.js app with Clerk

This guide shows you how to use the [<SignIn />](https://clerk.com/docs/nextjs/reference/components/authentication/sign-in.md) component to build a custom page that **allows users to sign in or sign up within a single flow**.

To set up separate sign-in and sign-up pages, follow this guide, and then follow the [custom sign-up page guide](https://clerk.com/docs/nextjs/guides/development/custom-sign-up-page.md).

> If prebuilt components don't meet your specific needs or if you require more control over the logic, you can rebuild the existing Clerk flows using the Clerk API. For more information, see the [custom flow guides](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=nextjs).

1. ## Build a sign-in-or-up page

   The following example demonstrates how to render the [<SignIn />](https://clerk.com/docs/nextjs/reference/components/authentication/sign-in.md) component on a dedicated page using the [Next.js optional catch-all route](https://nextjs.org/docs/pages/building-your-application/routing/dynamic-routes#catch-all-segments).

   filename: app/sign-in/[[...sign-in]]/page.tsx

   ```tsx
   import { SignIn } from '@clerk/nextjs'

   export default function Page() {
     return <SignIn />
   }
   ```
2. ## Make the route public

   Ensure the `/sign-in` route is accessible to all users, including unauthenticated users.

   If your `clerkMiddleware()` includes auth checks, this pattern is no longer recommended. See [Migrating away from Middleware-based auth checks](https://clerk.com/docs/guides/development/upgrading/upgrade-guides/migrate-from-create-route-matcher.md?sdk=nextjs).
3. ## Update your environment variables

   - Set the `CLERK_SIGN_IN_URL` environment variable to tell Clerk where the `<SignIn />` component is being hosted.
   - Set `CLERK_SIGN_IN_FALLBACK_REDIRECT_URL` as a fallback URL incase users visit the `/sign-in` route directly.
   - Set `CLERK_SIGN_UP_FALLBACK_REDIRECT_URL` as a fallback URL incase users select the 'Don't have an account? Sign up' link at the bottom of the component.

   Learn more about these environment variables and how to customize Clerk's redirect behavior in the [dedicated guide](https://clerk.com/docs/guides/development/customize-redirect-urls.md?sdk=nextjs).

   filename: .env

   ```env
   NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
   NEXT_PUBLIC_CLERK_SIGN_IN_FALLBACK_REDIRECT_URL=/
   NEXT_PUBLIC_CLERK_SIGN_UP_FALLBACK_REDIRECT_URL=/
   ```
4. ## Visit your new page

   Run your project with the following command:

   ```npm
   npm run dev
   ```

   Visit your new custom page locally at [localhost:3000/sign-in](http://localhost:3000/sign-in).

## Next steps

Learn more about Clerk components, how to use them to create custom pages, and how to use Clerk's client-side helpers using the following guides.

- [Create a custom sign-up page](https://clerk.com/docs/nextjs/guides/development/custom-sign-up-page.md): Learn how to add a custom sign-up page to your Next.js app with Clerk components.
- [Read user data](https://clerk.com/docs/nextjs/guides/users/reading.md): Learn how to use Clerk's hooks and helpers to read user data in your Next.js app.
- [Client-side helpers](https://clerk.com/docs/reference/nextjs/overview.md?sdk=nextjs#client-side-helpers): Learn more about Clerk's client-side helpers and how to use them.
- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=nextjs): Learn how to quickly add authentication to your app using Clerk's suite of components.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
