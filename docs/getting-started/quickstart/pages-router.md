# Next.js Quickstart (Pages Router)

**Example Repository**

- [Next.js Pages Router Quickstart Repo](https://github.com/clerk/clerk-nextjs-pages-quickstart)

**Before you start**

- [Set up a Clerk application](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md)

> This quickstart is for apps that use Pages Router. Using App Router? Follow the [App Router quickstart](https://clerk.com/docs/getting-started/quickstart.md) instead.

1. ## Create a new Next.js app

   If you don't already have a Next.js app (Pages Router), run the following commands to [create a new one](https://nextjs.org/docs/pages/getting-started/installation).

   ```npm
   npm create next-app@latest clerk-nextjs-pages -- --no-app
   cd clerk-nextjs-pages
   ```
2. ## Install `@clerk/nextjs`

   The [Clerk Next.js SDK](https://clerk.com/docs/reference/nextjs/overview.md) gives you access to prebuilt components, hooks, and helpers to make user authentication easier.

   Run the following command to install the SDK:

   ```npm
   npm install @clerk/nextjs
   ```
3. ## Set your Clerk API keys

   Add the following keys to your `.env` file. These keys can always be retrieved from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

   1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page.
   2. In the **Quick Copy** section, copy your Clerk Publishable Key and Secret Key.
   3. Paste your keys into your `.env` file.

   The final result should resemble the following:

   filename: .env

   ```env
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY={{pub_key}}
   CLERK_SECRET_KEY={{secret}}
   ```
4. ## Add `clerkMiddleware()` to your app

   [clerkMiddleware()](https://clerk.com/docs/reference/nextjs/clerk-middleware.md) grants you access to user authentication state throughout your app. To add `clerkMiddleware()` to your app, follow these steps:

   > If you're using Next.js ≤15, name your file `middleware.ts` instead of `proxy.ts`. The code itself remains the same; only the filename changes.

   1. Create a `proxy.ts` file.
      - If you're using the `/src` directory, create `proxy.ts` in the `/src` directory.
      - If you're not using the `/src` directory, create `proxy.ts` in the root directory.
   2. In your `proxy.ts` file, export the `clerkMiddleware()` helper:

      filename: proxy.ts

      ```tsx
      import { clerkMiddleware } from '@clerk/nextjs/server'

      export default clerkMiddleware()

      export const config = {
        matcher: [
          // Skip Next.js internals and all static files, unless found in search params
          '/((?!_next|[^?]*\\.(?:html?|css|js(?!on)|jpe?g|webp|png|gif|svg|ttf|woff2?|ico|csv|docx?|xlsx?|zip|webmanifest)).*)',
          // Always run for API routes
          '/(api|trpc)(.*)',
          // Always run for Clerk-specific frontend API routes
          '/__clerk/(.*)',
        ],
      }
      ```
   3. By default, `clerkMiddleware()` will not protect any routes. All routes are public and you must opt-in to protection. To require a signed-in user, protect resources close to where they're used, as shown in the [guide on reading user data](https://clerk.com/docs/guides/users/reading.md#pages-router).
5. ## Add `<ClerkProvider>` and Clerk components to your app

   The [<ClerkProvider>](https://clerk.com/docs/reference/components/clerk-provider.md) component provides session and user context to Clerk's hooks and components. It's recommended to wrap your entire app at the entry point with `<ClerkProvider>` to make authentication globally accessible. See the [reference docs](https://clerk.com/docs/reference/components/clerk-provider.md) for other configuration options.

   Copy and paste the following code into your app. This:

   - Adds the `<ClerkProvider>` to your app, providing Clerk's authentication context to your app.
   - Creates a header with Clerk's [prebuilt components](https://clerk.com/docs/reference/components/overview.md) to allow users to sign in and out, and display different content for signed-in and signed-out users.

   filename: pages/\_app.tsx

   ```tsx
   import '@/styles/globals.css'
   import { ClerkProvider, SignInButton, SignUpButton, Show, UserButton } from '@clerk/nextjs'
   import type { AppProps } from 'next/app'

   function MyApp({ Component, pageProps }: AppProps) {
     return (
       <ClerkProvider
         {...pageProps}
         appearance={{
           cssLayerName: 'clerk',
         }}
       >
         <header className="flex justify-end items-center p-4 gap-4 h-16">
           <Show when="signed-out">
             <SignInButton />
             <SignUpButton>
               <button className="bg-[#6c47ff] text-white rounded-full font-medium text-sm sm:text-base h-10 sm:h-12 px-4 sm:px-5 cursor-pointer">
                 Sign Up
               </button>
             </SignUpButton>
           </Show>
           <Show when="signed-in">
             <UserButton />
           </Show>
         </header>
         <Component {...pageProps} />
       </ClerkProvider>
     )
   }

   export default MyApp
   ```

   This example uses the following components:

   - [<Show when="signed-in">](https://clerk.com/docs/reference/components/control/show.md): Children of this component can only be seen while **signed in**.
   - [<Show when="signed-out">](https://clerk.com/docs/reference/components/control/show.md): Children of this component can only be seen while **signed out**.
   - [<UserButton />](https://clerk.com/docs/reference/components/user/user-button.md): Shows the signed-in user's avatar. Selecting it opens a dropdown menu with account management options.
   - [<SignInButton />](https://clerk.com/docs/reference/components/unstyled/sign-in-button.md): An unstyled component that links to the sign-in page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) are set for the sign-in URL, this component links to the [Account Portal sign-in page](https://clerk.com/docs/guides/account-portal/overview.md#sign-in).
   - [<SignUpButton />](https://clerk.com/docs/reference/components/unstyled/sign-up-button.md): An unstyled component that links to the sign-up page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) are set for the sign-up URL, this component links to the [Account Portal sign-up page](https://clerk.com/docs/guides/account-portal/overview.md#sign-up).
6. ## Update `globals.css`

   In the previous step, the `cssLayerName` property is set on the `<ClerkProvider>` component. Now, you need to **add the following line to the top of your `globals.css` file** in order to include the layer you named in the `cssLayerName` property. The example names the layer `clerk` but you can name it anything you want. These steps are necessary for v4 of Tailwind as it ensures that Tailwind's utility styles are applied after Clerk's styles.

   filename: globals.css

   ```css
   + @layer theme, base, clerk, components, utilities;
     @import 'tailwindcss';
   ```
7. ## Run your project

   Run your project with the following command:

   ```npm
   npm run dev
   ```
8. ## Create your first user

   1. Visit your app's homepage at http://localhost:3000.
   2. Select "Sign up" on the page and authenticate to create your first user.

## Next steps

Explore the most relevant next steps for your SDK using the following guides.

- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md): Learn how to add Clerk's prebuilt authentication and user-management UI to your app.
- [Build custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md): Learn how to build custom user interfaces entirely from scratch using the Clerk API.
- [Read user data](https://clerk.com/docs/guides/users/reading.md): Learn how to use Clerk's helpers to read user data in your app.
- [Customization & localization](https://clerk.com/docs/guides/customizing-clerk/appearance-prop/overview.md): Learn how to customize and localize Clerk components.

## More to explore

Explore additional Clerk features that help you build, manage, and grow your application.

- [**Organizations**](https://clerk.com/docs/guides/organizations/overview.md) - Organizations are shared accounts that let teams collaborate, manage members and roles, and control access to shared resources.
- [**Billing**](https://clerk.com/docs/guides/billing/overview.md) - Billing enables you to manage subscriptions, free trials, payments, plans, and billing-related webhook events for B2C and B2B applications.
- [**Waitlist**](https://clerk.com/docs/guides/secure/restricting-access.md#waitlist) - Waitlist lets you collect signups and control access to new products or features before launch through a simple, integrated workflow.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
