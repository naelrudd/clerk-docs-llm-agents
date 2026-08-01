# React Router Quickstart

**Example Repository**

- [React Router Quickstart Repo](https://github.com/clerk/clerk-react-router-quickstart)

React Router can be used in different modes: **declarative**, **data**, or **framework**. This tutorial explains how to use React Router in **framework** mode. To use React Router in **declarative** mode instead, see the [dedicated guide](https://clerk.com/docs/react-router/guides/development/declarative-mode.md).

This tutorial assumes that you're using React Router **v7.9.0 or later**, or **v8.3.0 or later** in framework mode.

1. ## Create a new React app using React Router

   If you don't already have a React app using React Router, run the following commands to [create a new one](https://reactrouter.com/start/framework/installation).

   ```npm
   npm create react-router@latest clerk-react-router
   cd clerk-react-router
   ```
2. ## Install `@clerk/react-router`

   The [Clerk React Router SDK](https://clerk.com/docs/react-router/reference/react-router/overview.md) gives you access to prebuilt components, hooks, and helpers to make user authentication easier.

   Run the following command to install the SDK:

   ```npm
   npm install @clerk/react-router
   ```

   ## Set your Clerk API keys

   Add the following keys to your `.env` file. These keys can always be retrieved from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

   filename: .env

   ```env
   VITE_CLERK_PUBLISHABLE_KEY={{pub_key}}
   CLERK_SECRET_KEY={{secret}}
   ```
3. ## Add `clerkMiddleware()` and `rootAuthLoader()` to your app

   [clerkMiddleware()](https://clerk.com/docs/react-router/reference/react-router/clerk-middleware.md) grants you access to user authentication state throughout your app. It also allows you to protect specific routes from unauthenticated users. To add `clerkMiddleware()` to your app, follow these steps:

   > If you're using React Router v7, enable the `v8_middleware` future flag in your `react-router.config.ts` file.
   >
   > filename: react-router.config.ts
   >
   > ```ts
   > import type { Config } from '@react-router/dev/config'
   >
   > export default {
   >   // ...
   >   future: {
   >     v8_middleware: true,
   >   },
   > } satisfies Config
   > ```

   1. Add the following code to your `root.tsx` file to configure the `clerkMiddleware()` and [rootAuthLoader()](https://clerk.com/docs/react-router/reference/react-router/root-auth-loader.md) functions.

      filename: app/root.tsx

      ```tsx
      import { isRouteErrorResponse, Links, Meta, Outlet, Scripts, ScrollRestoration } from 'react-router'
      import type { Route } from './+types/root'
      import stylesheet from './app.css?url'
      import { clerkMiddleware, rootAuthLoader } from '@clerk/react-router/server'

      export const middleware: Route.MiddlewareFunction[] = [clerkMiddleware()]

      export const loader = (args: Route.LoaderArgs) => rootAuthLoader(args)

      export const links: Route.LinksFunction = () => [
        { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
        {
          rel: 'preconnect',
          href: 'https://fonts.gstatic.com',
          crossOrigin: 'anonymous',
        },
        {
          rel: 'stylesheet',
          href: 'https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap',
        },
        { rel: 'stylesheet', href: stylesheet },
      ]

      export function Layout({ children }: { children: React.ReactNode }) {
        return (
          <html lang="en">
            <head>
              <meta charSet="utf-8" />
              <meta name="viewport" content="width=device-width, initial-scale=1" />
              <Meta />
              <Links />
            </head>
            <body>
              {children}
              <ScrollRestoration />
              <Scripts />
            </body>
          </html>
        )
      }

      export default function App() {
        return <Outlet />
      }

      export function ErrorBoundary({ error }: Route.ErrorBoundaryProps) {
        let message = 'Oops!'
        let details = 'An unexpected error occurred.'
        let stack: string | undefined

        if (isRouteErrorResponse(error)) {
          message = error.status === 404 ? '404' : 'Error'
          details =
            error.status === 404 ? 'The requested page could not be found.' : error.statusText || details
        } else if (import.meta.env.DEV && error && error instanceof Error) {
          details = error.message
          stack = error.stack
        }

        return (
          <main className="pt-16 p-4 container mx-auto">
            <h1>{message}</h1>
            <p>{details}</p>
            {stack && (
              <pre className="w-full p-4 overflow-x-auto">
                `{stack}`
              </pre>
            )}
          </main>
        )
      }
      ```

   2. By default, `clerkMiddleware()` will not protect any routes. All routes are public and you must opt-in to protection for routes. See the [clerkMiddleware() reference](https://clerk.com/docs/react-router/reference/react-router/clerk-middleware.md) to learn how to require authentication for specific routes.
4. ## Add `<ClerkProvider>` and Clerk components to your app

   The [<ClerkProvider>](https://clerk.com/docs/react-router/reference/components/clerk-provider.md) component provides session and user context to Clerk's hooks and components. It's recommended to wrap your entire app at the entry point with `<ClerkProvider>` to make authentication globally accessible. See the [reference docs](https://clerk.com/docs/react-router/reference/components/clerk-provider.md) for other configuration options.

   Copy and paste the following code into your `root.tsx` file. This:

   - Adds the `<ClerkProvider>` to your app, providing Clerk's authentication context to your app. Pass `loaderData` to the provider so it can access the authentication data loaded by `rootAuthLoader()`.
   - Creates a header with Clerk's [prebuilt components](https://clerk.com/docs/react-router/reference/components/overview.md) to allow users to sign in and out, and display different content for signed-in and signed-out users.

   filename: app/root.tsx

   ```tsx
   import { ClerkProvider, SignInButton, SignUpButton, Show, UserButton } from '@clerk/react-router'
   import { isRouteErrorResponse, Links, Meta, Outlet, Scripts, ScrollRestoration } from 'react-router'
   import { clerkMiddleware, rootAuthLoader } from '@clerk/react-router/server'

   import type { Route } from './+types/root'
   import stylesheet from './app.css?url'

   export const middleware: Route.MiddlewareFunction[] = [clerkMiddleware()]

   export const loader = (args: Route.LoaderArgs) => rootAuthLoader(args)

   export const links: Route.LinksFunction = () => [
     { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
     {
       rel: 'preconnect',
       href: 'https://fonts.gstatic.com',
       crossOrigin: 'anonymous',
     },
     {
       rel: 'stylesheet',
       href: 'https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap',
     },
     { rel: 'stylesheet', href: stylesheet },
   ]

   export function Layout({ children }: { children: React.ReactNode }) {
     return (
       <html lang="en">
         <head>
           <meta charSet="utf-8" />
           <meta name="viewport" content="width=device-width, initial-scale=1" />
           <Meta />
           <Links />
         </head>
         <body>
           {children}
           <ScrollRestoration />
           <Scripts />
         </body>
       </html>
     )
   }

   // Pull in the `loaderData` from the `rootAuthLoader()` function
   export default function App({ loaderData }: Route.ComponentProps) {
     return (
       // Pass the `loaderData` to the `<ClerkProvider>` component
       <ClerkProvider loaderData={loaderData}>
         <header className="flex items-center justify-center py-8 px-4">
           <Show when="signed-out">
             <SignInButton />
             <SignUpButton />
           </Show>
           <Show when="signed-in">
             <UserButton />
           </Show>
         </header>
         <Outlet />
       </ClerkProvider>
     )
   }

   export function ErrorBoundary({ error }: Route.ErrorBoundaryProps) {
     let message = 'Oops!'
     let details = 'An unexpected error occurred.'
     let stack: string | undefined

     if (isRouteErrorResponse(error)) {
       message = error.status === 404 ? '404' : 'Error'
       details =
         error.status === 404 ? 'The requested page could not be found.' : error.statusText || details
     } else if (import.meta.env.DEV && error && error instanceof Error) {
       details = error.message
       stack = error.stack
     }

     return (
       <main className="pt-16 p-4 container mx-auto">
         <h1>{message}</h1>
         <p>{details}</p>
         {stack && (
           <pre className="w-full p-4 overflow-x-auto">
             `{stack}`
           </pre>
         )}
       </main>
     )
   }
   ```

   This example uses the following components:

   - [<Show when="signed-in">](https://clerk.com/docs/react-router/reference/components/control/show.md): Children of this component can only be seen while **signed in**.
   - [<Show when="signed-out">](https://clerk.com/docs/react-router/reference/components/control/show.md): Children of this component can only be seen while **signed out**.
   - [<UserButton />](https://clerk.com/docs/react-router/reference/components/user/user-button.md): Shows the signed-in user's avatar. Selecting it opens a dropdown menu with account management options.
   - [<SignInButton />](https://clerk.com/docs/react-router/reference/components/unstyled/sign-in-button.md): An unstyled component that links to the sign-in page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=react-router) are set for the sign-in URL, this component links to the [Account Portal sign-in page](https://clerk.com/docs/guides/account-portal/overview.md?sdk=react-router#sign-in).
   - [<SignUpButton />](https://clerk.com/docs/react-router/reference/components/unstyled/sign-up-button.md): An unstyled component that links to the sign-up page. In this example, since no props or [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=react-router) are set for the sign-up URL, this component links to the [Account Portal sign-up page](https://clerk.com/docs/guides/account-portal/overview.md?sdk=react-router#sign-up).
5. ## Run your project

   Run your project with the following command:

   ```npm
   npm run dev
   ```
6. ## Create your first user

   1. Visit your app's homepage at http://localhost:5173.
   2. Select "Sign up" on the page and authenticate to create your first user.

   > To make configuration changes to your Clerk development instance, claim the Clerk keys that were generated for you by selecting **Configure your application** in the bottom right of your app. This will associate the application with your Clerk account. Once claimed, you can find your Publishable Key and Secret Key any time on the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

## Next steps

Explore the most relevant next steps for your SDK using the following guides.

- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=react-router): Learn how to add Clerk's prebuilt authentication and user-management UI to your app.
- [Build custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=react-router): Learn how to build custom user interfaces entirely from scratch using the Clerk API.
- [Read user data](https://clerk.com/docs/guides/users/reading.md?sdk=react-router): Learn how to use Clerk's helpers to read user data in your app.
- [Customization & localization](https://clerk.com/docs/guides/customizing-clerk/appearance-prop/overview.md?sdk=react-router): Learn how to customize and localize Clerk components.

## More to explore

Explore additional Clerk features that help you build, manage, and grow your application.

- [**Organizations**](https://clerk.com/docs/guides/organizations/overview.md?sdk=react-router) - Organizations are shared accounts that let teams collaborate, manage members and roles, and control access to shared resources.
- [**Billing**](https://clerk.com/docs/guides/billing/overview.md?sdk=react-router) - Billing enables you to manage subscriptions, free trials, payments, plans, and billing-related webhook events for B2C and B2B applications.
- [**Waitlist**](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=react-router#waitlist) - Waitlist lets you collect signups and control access to new products or features before launch through a simple, integrated workflow.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
