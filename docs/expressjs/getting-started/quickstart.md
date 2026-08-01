# Express Quickstart

**Example Repository**

- [Express Quickstart Repo](https://github.com/clerk/clerk-express-quickstart)

**Before you start**

- [Set up a Clerk application](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md?sdk=expressjs)

Learn how to integrate Clerk into your Express backend for secure user authentication and management. This guide focuses on backend implementation and requires a [Clerk frontend SDK](https://clerk.com/docs.md#explore-by-frontend-framework) to function correctly.

1. ## Create a new Express app

   If you don't already have an Express app, run the following commands to [create a new one](https://expressjs.com/en/starter/installing.html).

   ```npm
   mkdir clerk-express
   cd clerk-express
   npm init -y
   npm install express
   ```
2. ## Install `@clerk/express`

   The [Clerk Express SDK](https://clerk.com/docs/reference/express/overview.md?sdk=expressjs) provides a range of backend utilities to simplify user authentication and management in your application.

   Run the following command to install the SDK:

   ```npm
   npm install @clerk/express
   ```
3. ## Set your Clerk API keys

   Add the following keys to your `.env` file. These keys can always be retrieved from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

   1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page.
   2. In the **Quick Copy** section, copy your Clerk Publishable Key and Secret Key.
   3. Paste your keys into your `.env` file.

   The final result should resemble the following:

   filename: .env

   ```sh
   CLERK_PUBLISHABLE_KEY={{pub_key}}
   CLERK_SECRET_KEY={{secret}}
   ```

   Node can load `.env` files natively. When running your app, use the `--env-file=.env` flag so environment variables can be accessed at import time.
4. ## Add `clerkMiddleware()` to your app

   The [`clerkMiddleware()`](https://clerk.com/docs/reference/express/clerk-middleware.md?sdk=expressjs) function checks the request's cookies and headers for a session JWT and, if found, attaches the [`Auth`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=expressjs){{ target: '_blank' }} object to the `request` object under the `auth` key.

   filename: index.ts

   ```ts
   import express from 'express'
   import { clerkMiddleware } from '@clerk/express'

   const app = express()
   const PORT = 3000

   app.use(clerkMiddleware())

   // Start the server and listen on the specified port
   app.listen(PORT, () => {
     console.log(`Example app listening at http://localhost:${PORT}`)
   })
   ```
5. ## Protect your routes using `getAuth()`

   To protect your routes, use the [`getAuth()`](https://clerk.com/docs/reference/express/get-auth.md?sdk=expressjs) helper in the route body. `getAuth()` returns the request's auth state, so you can choose how your application responds when the user isn't authenticated.

   In the following example, `getAuth()` is used to protect the `/protected` route. If the user isn't authenticated, the route returns a `401` status code. If the user is authenticated, the `userId` is passed to [`clerkClient.users.getUser()`](https://clerk.com/docs/reference/backend/user/get-user.md?sdk=expressjs){{ target: '_blank' }} to fetch the current user's `User` object.

   filename: index.ts

   ```ts
   import express from 'express'
   import { clerkMiddleware, clerkClient, getAuth } from '@clerk/express'

   const app = express()
   const PORT = 3000

   app.use(clerkMiddleware())

   app.get('/protected', async (req, res) => {
     // Use `getAuth()` to get the user's `userId`
     const { isAuthenticated, userId } = getAuth(req)

     if (!isAuthenticated) {
       res.status(401).json({ error: 'Unauthorized' })
       return
     }

     // Use the `getUser()` method to get the user's User object
     const user = await clerkClient.users.getUser(userId)

     res.json({ user })
   })

   // Start the server and listen on the specified port
   app.listen(PORT, () => {
     console.log(`Example app listening at http://localhost:${PORT}`)
   })
   ```
6. ## Add global TypeScript type (optional)

   If you're using TypeScript, add a global type reference to your project to enable auto-completion and type checking for the `auth` object in Express request handlers.

   1. In your application's root folder, create a `types/` directory.
   2. Inside this directory, create a `globals.d.ts` file with the following code.

   filename: types/globals.d.ts

   ```ts
   /// <reference types="@clerk/express/env" />
   ```

## Next steps

Explore the most relevant next steps for your backend SDK using the following guides.

- [Protect routes using ](https://clerk.com/docs/reference/express/get-auth.md?sdk=expressjs): Learn how to protect specific routes from unauthenticated users.
- [Protect routes based on authorization status](https://clerk.com/docs/reference/express/get-auth.md?sdk=expressjs): Learn how to protect a route based on both authentication and authorization status.
- [Deploy to production](https://clerk.com/docs/guides/development/deployment/production.md?sdk=expressjs): Learn how to deploy your Clerk app to production.
- [Clerk Express SDK reference](https://clerk.com/docs/reference/express/overview.md?sdk=expressjs): Learn about the Clerk Express SDK and how to integrate it into your app.

## More to explore

Explore additional Clerk features that help you build, manage, and grow your application.

- [**Organizations**](https://clerk.com/docs/guides/organizations/overview.md?sdk=expressjs) - Organizations are shared accounts that let teams collaborate, manage members and roles, and control access to shared resources.
- [**Billing**](https://clerk.com/docs/guides/billing/overview.md?sdk=expressjs) - Billing enables you to manage subscriptions, free trials, payments, plans, and billing-related webhook events for B2C and B2B applications.
- [**Waitlist**](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=expressjs#waitlist) - Waitlist lets you collect signups and control access to new products or features before launch through a simple, integrated workflow.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
