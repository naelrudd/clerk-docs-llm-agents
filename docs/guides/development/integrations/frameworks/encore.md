# Integrate Encore with Clerk

**Before you start**

- [Set up a Clerk application](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md)
- [Create an Encore app](https://encore.dev/docs/ts/quick-start)

[Encore](https://encore.dev) is an open source backend framework for TypeScript with built-in infrastructure automation and observability.

This tutorial outlines how to integrate Clerk's authentication into your Encore backend application, allowing you to manage user authentication and sessions securely. This guide uses TypeScript and Encore's built-in auth handler pattern.

1. ## Install `@clerk/backend`

   `@clerk/backend` is a wrapper around the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }} that makes it easier to interact with the API **for JavaScript environments**. It provides utilities to verify session tokens and manage users.

   Run the following command to install the SDK:

   ```npm
   npm install @clerk/backend
   ```
2. ## Set your Clerk API keys

   1. In the Clerk Dashboard, navigate to the [**API keys**](https://dashboard.clerk.com/~/api-keys) page.
   2. In the **Quick Copy** section, copy your Clerk Secret Key.
   3. Encore provides built-in [secrets management](https://encore.dev/docs/ts/primitives/secrets) to securely store sensitive values. Add your key to Encore's secrets with the following command:

      filename: terminal

      ```bash
      encore secret set --dev ClerkSecretKey
      ```

   > When you deploy your Encore app, you can set a different value for production to keep your keys secure.
   >
   > filename: terminal
   >
   > ```bash
   > encore secret set --prod ClerkSecretKey
   > ```
3. ## Create a Clerk client

   1. Create an `auth` folder.
   2. In the `auth` folder, create a `clerk.ts` file.
   3. In your `clerk.ts` file, configure the Clerk client using the Clerk Secret Key you set, using [`createClerkClient`](https://clerk.com/docs/reference/backend/overview.md) from `@clerk/backend`:

   filename: auth/clerk.ts

   ```ts
   import { createClerkClient } from '@clerk/backend'
   import { secret } from 'encore.dev/config'

   const clerkSecretKey = secret('ClerkSecretKey')

   export const clerk = createClerkClient({
     secretKey: clerkSecretKey(),
   })
   ```
4. ## Create an auth handler

   Encore has a built-in auth handler pattern for protecting endpoints. In the `auth` folder, create a `handler.ts` file and copy and paste the following code. This is the auth handler that verifies Clerk [session tokens](https://clerk.com/docs/guides/sessions/session-tokens.md) using the [`verifyToken()`](https://clerk.com/docs/reference/backend/verify-token.md) function and makes authenticated user data available to your endpoints:

   > For optimal performance and to avoid rate limiting, it's recommended to use the [useUser()](https://clerk.com/docs/reference/hooks/use-user.md) hook on the client-side when possible. Only use `getUser()` when you specifically need user data in a server context.

   filename: auth/handler.ts

   ```ts
   import { APIError, Gateway, Header } from 'encore.dev/api'
   import { authHandler } from 'encore.dev/auth'
   import { verifyToken } from '@clerk/backend'
   import { secret } from 'encore.dev/config'
   import { clerk } from './clerk'

   const clerkSecretKey = secret('ClerkSecretKey')

   interface AuthParams {
     authorization: Header<'Authorization'>
   }

   export interface AuthData {
     userID: string
     email: string
   }

   export const auth = authHandler<AuthParams, AuthData>(async (params) => {
     const token = params.authorization?.replace('Bearer ', '')

     if (!token) {
       throw APIError.unauthenticated('Missing session token')
     }

     try {
       const payload = await verifyToken(token, {
         secretKey: clerkSecretKey(),
         // Optional: restrict allowed origins to prevent subdomain cookie leakage
         // Replace with your authorized parties
         authorizedParties: ['http://localhost:3001', 'https://example.com'],
       })

       const userId = payload.sub

       if (!userId) {
         throw new Error('No user ID in session token')
       }

       const user = await clerk.users.getUser(userId)

       return {
         userID: user.id,
         email:
           user.emailAddresses.find((e) => e.id === user.primaryEmailAddressId)?.emailAddress || '',
       }
     } catch (err) {
       throw APIError.unauthenticated('Invalid session token')
     }
   })

   export const gateway = new Gateway({
     authHandler: auth,
   })
   ```
5. ## Protect your routes using `getAuthData()`

   This endpoint gets the authenticated user's profile information. The `auth: true` option protects the endpoint, allowing only authenticated requests to access it. The `getAuthData()` function retrieves the authenticated user's data from the auth handler. Learn more about authentication in [Encore documentation](https://encore.dev/docs/ts/develop/auth).

   filename: user/profile.ts

   ```ts
   import { api } from 'encore.dev/api'
   import { getAuthData } from '~encore/auth'

   export const getProfile = api(
     { expose: true, auth: true, method: 'GET', path: '/user/profile' },
     async () => {
       const auth = getAuthData()!

       return {
         userId: auth.userID,
         email: auth.email,
       }
     },
   )
   ```
6. ## Run your project

   Start your Encore app with the following command:

   ```bash
   encore run
   ```

   Open the local development dashboard at http://localhost:9400 in your browser to view traces for all requests, including auth handler execution.

If you want to add more to your Clerk + Encore integration, such as database integration, webhooks, or Organizations, check out this advanced [Clerk + Encore tutorial](https://encore.dev/blog/clerk-tutorial) guide.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
