# clerkClient

The `clerkClient` is a wrapper around the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }} that makes it easier to interact with the API **for JavaScript environments**. For example, to retrieve a list of all users in your application, you can use the [`users.getUserList()`](https://clerk.com/docs/reference/backend/user/get-user-list.md) method instead of manually making a fetch request to the [`https://api.clerk.com/v1/users`](https://clerk.com/docs/reference/backend-api/tag/users/GET/users){{ target: '_blank' }} endpoint.

**For AI agents:** Run `npx clerk@latest env pull` to write your Secret Key to your env file (under the framework-appropriate variable name, e.g. `CLERK_SECRET_KEY`) instead of copying it from the API keys page in the Dashboard, and use `npx clerk@latest api /users` to call any Backend API endpoint directly when you need to inspect or verify data while writing `clerkClient` code. Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md) with `npx skills add clerk/skills` for correct CLI and SDK usage.

## Installation

The SDK you are using already includes an instance of `clerkClient`, so you don't need to install `@clerk/backend` separately.

## Usage

`clerkClient()` is organized around [resources](#resources), such as **Users** and **Organizations**. To access a resource, you must **first instantiate a `clerkClient` instance.**

### Instantiate a default `clerkClient` instance

You can use the default instance of `clerkClient` provided by whichever SDK you are using, and skip the need to pass [configuration options](#create-clerk-client-options).

To use the default `clerkClient` instance, set your `CLERK_SECRET_KEY` [environment variable](https://clerk.com/docs/guides/development/clerk-environment-variables.md#clerk-publishable-and-secret-keys) and then import the `clerkClient` instance from the SDK as shown in the following example:

```jsx
import { clerkClient } from '@clerk/nextjs/server'

const client = await clerkClient()

const userList = await client.users.getUserList()
```

### Instantiate a custom `clerkClient` instance

If you would like to customize the behavior of `clerkClient()`, you can instantiate a custom instance yourself by calling `createClerkClient()` and passing in [`options`](#create-clerk-client-options).

```jsx
import { createClerkClient } from '@clerk/nextjs/server'

const clerkClient = createClerkClient({ secretKey: process.env.CLERK_SECRET_KEY })

const client = await clerkClient()

const userList = await client.users.getUserList()
```

### Example: Get the `userId` and other properties

The [`Auth`](https://clerk.com/docs/reference/backend/types/auth-object.md) object contains important information like the current user's session ID, user ID, and Organization ID.

The `Auth` object is available on the `request` object in server contexts. Some frameworks provide a helper that returns the `Auth` object. See the following table for more information.

| Framework            | How to access the `Auth` object                                                       |
| -------------------- | ------------------------------------------------------------------------------------- |
| Next.js App Router   | [auth()](https://clerk.com/docs/reference/nextjs/app-router/auth.md)                  |
| Next.js Pages Router | [getAuth()](https://clerk.com/docs/reference/nextjs/pages-router/get-auth.md)         |
| Astro                | [locals.auth()](https://clerk.com/docs/reference/astro/locals.md#locals-auth)         |
| Express              | [`req.auth`](https://clerk.com/docs/reference/express/overview.md)                    |
| Fastify              | [getAuth()](https://clerk.com/docs/reference/fastify/get-auth.md)                     |
| Nuxt                 | [event.context.auth()](https://clerk.com/docs/reference/nuxt/overview.md#auth-object) |
| React Router         | [getAuth()](https://clerk.com/docs/reference/react-router/get-auth.md)                |
| TanStack React Start | [auth()](https://clerk.com/docs/reference/tanstack-react-start/auth.md)               |
| Other                | `request.auth`                                                                        |

The following examples demonstrate how to retrieve the authenticated user's ID using framework-specific auth helpers and how to use the [`getUser()`](https://clerk.com/docs/reference/backend/user/get-user.md) method to get the [Backend `User` object](https://clerk.com/docs/reference/backend/types/backend-user.md).

For Next.js, the `Auth` object is accessed using the `auth()` helper in App Router apps and the `getAuth()` function in Pages Router apps. [Learn more about using these helpers](https://clerk.com/docs/nextjs/guides/users/reading.md#server-side).

Use the following tabs to see examples of how to use these helpers to access the user's ID in your App Router or Pages Router app.

**App Router**

filename: app/api/example/route.ts
```tsx
import { auth, clerkClient } from '@clerk/nextjs/server'
import { NextResponse } from 'next/server'

export async function GET() {
  // The `Auth` object gives you access to properties like `isAuthenticated` and `userId`
  // Accessing the `Auth` object differs depending on the SDK you're using
  // https://clerk.com/docs/reference/backend/types/auth-object#how-to-access-the-auth-object
  const { isAuthenticated, userId } = await auth()

  // Protect the route by checking if the user is signed in
  if (!isAuthenticated) {
    return new NextResponse('Unauthorized', { status: 401 })
  }

  // Initialize clerkClient
  const client = await clerkClient()

  // Use the `getUser()` method to get the Backend User object
  const user = await client.users.getUser(userId)

  // Return the Backend User object
  return NextResponse.json({ user: user }, { status: 200 })
}
```

**Pages Router**

filename: pages/api/auth.ts
```tsx
import { getAuth, clerkClient } from '@clerk/nextjs/server'
import type { NextApiRequest, NextApiResponse } from 'next'

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
  // Use `getAuth()` to access `isAuthenticated` and the user's ID
  const { isAuthenticated, userId } = getAuth(req)

  // Protect the route by checking if the user is signed in
  if (!isAuthenticated) {
    return res.status(401).json({ error: 'Unauthorized' })
  }

  // Initialize `clerkClient`
  const client = await clerkClient()

  // Use the `getUser()` method to get the user's full `Backend User` object
  const user = await client.users.getUser(userId)

  return res.status(200).json({ user })
}
```

### `createClerkClient({ options })`

The `createClerkClient()` function requires an `options` object with at least the `secretKey` provided. It is recommended to set these options as [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md#api-and-sdk-configuration) where possible, and then pass them. For example, you can set the `secretKey` option using the `CLERK_SECRET_KEY` environment variable, and then pass it like this: `createClerkClient({ secretKey: process.env.CLERK_SECRET_KEY })`.

The following options are available:

| Name                 | Type                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| secretKey (required) | string                                 | Your Clerk Secret KeyYour Clerk Secret Key is used to authenticate requests from your backend to Clerk's API. You can find it on the API keys page in the Clerk Dashboard. Do not expose this on the frontend with a public environment variable..                                                                                                                                                                                                                        |
| jwtKey?              | string                                 | The JWKS Public Key from the API keys in the Clerk Dashboard. For more information, refer to Manual JWT verification.                                                                                                                                                                                                                                                                                                                                                     |
| publishableKey?      | string                                 | Your Clerk Publishable KeyYour Clerk Publishable Key tells your app what your FAPI URL is, enabling your app to locate and communicate with your dedicated FAPI instance. You can find it on the API keys page in the Clerk Dashboard..                                                                                                                                                                                                                                   |
| domain?              | string                                 | The domain of a satellite application in a multi-domain setup.                                                                                                                                                                                                                                                                                                                                                                                                            |
| isSatellite?         | boolean                                | Whether the instance is a satellite domain in a multi-domain setup. Defaults to false.                                                                                                                                                                                                                                                                                                                                                                                    |
| satelliteAutoSync?   | boolean                                | Controls whether a satellite app automatically syncs authentication state with the primary domain on first page load. When false (default), the satellite app skips the automatic redirect if no session cookies exist, and only triggers the handshake after the user initiates a sign-in or sign-up action. When true, the satellite app redirects to the primary domain on every first visit to sync state. Defaults to false. See satellite domains for more details. |
| proxyUrl?            | string                                 | The proxy URL from a multi-domain setup.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| sdkMetadata?         | { name: string, version: string }     | Metadata about the SDK.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| telemetry?           | { disabled: boolean, debug: boolean } | Telemetry configuration.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| userAgent?           | string                                 | The User-Agent request header passed to the Clerk API.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| apiUrl?              | string                                 | The Clerk Backend API endpoint. Defaults to 'https://api.clerk.com'.                                                                                                                                                                                                                                                                                                                                                                                                     |
| apiVersion?          | string                                 | The version passed to the Clerk API. Defaults to 'v1'.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| audience?            | string | string[]                    | A string or list of audiences.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| taskUrls?            | Record<SessionTask['key'], string>   | The URL paths users are redirected to after sign-up or sign-in when specific session tasks need to be completed. For example, { 'choose-organization': '/onboarding/choose-organization' } redirects users to /onboarding/choose-organization after sign-up if they need to choose an Organization.                                                                                                                                                                      |

## Resources

The SDK is organized around resources, such as **Users** and **Organizations**. Each resource provides a set of operations (for example, creating, listing, or updating) that map directly to the Backend API. Each section below highlights the primary resources available in the SDK. For a complete list of resources and operations, see the [Backend API reference](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.

### Users

The **User** resource provides operations for creating, retrieving, and managing users within your application. Most operations return, or work directly with, the Backend [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md) object, which represents a user who has successfully signed up to your application. It holds information about a user, such as their unique identifier, name, email addresses, phone numbers, and more.

### Organizations

The **Organization** resource provides operations for creating, retrieving, and managing Organizations within your application. Most operations return, or work directly with, the following Backend objects:

- [`Organization`](https://clerk.com/docs/reference/backend/types/backend-organization.md) object holds information about an Organization.
- [`OrganizationInvitation`](https://clerk.com/docs/reference/backend/types/backend-organization-invitation.md) object is the model around an Organization invitation.
- [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md) object is the model around an Organization membership entity and describes the relationship between users and Organizations.

### Billing

The **Billing** resource provides operations for creating and managing Subscription Plans and Features within your application. Most operations return, or work directly with, the following Backend objects:

- [`BillingSubscription`](https://clerk.com/docs/reference/backend/types/billing-subscription.md) object holds information about a Subscription, as well as methods for managing it.
- [`BillingSubscriptionItem`](https://clerk.com/docs/reference/backend/types/billing-subscription-item.md) object holds information about a Subscription Item, as well as methods for managing it.
- [`BillingPlan`](https://clerk.com/docs/reference/backend/types/billing-plan.md) object holds information about a Plan, as well as methods for managing it.
- [`Feature`](https://clerk.com/docs/reference/backend/types/feature.md) object represents a Feature of a Subscription Plan.

### Allowlist identifiers

The **Allowlist Identifier** resource allows you to control who can sign up to your application, by restricting access based on the user's email address or phone number. Most operations return, or work directly with, the Backend [`AllowlistIdentifier`](https://clerk.com/docs/reference/backend/types/backend-allowlist-identifier.md) object, which represents an identifier that has been added to the allowlist of your application.

### API keys

The **API Key** resource allows you to manage API keys for your application. Most operations return, or work directly with, the Backend [`APIKey`](https://clerk.com/docs/reference/backend/types/backend-api-key.md) object.

### Domains

The **Domain** resource allows you to manage the domains associated with your Clerk instance. Each domain contains information about the URLs where Clerk operates and the required CNAME targets.

### Sessions

The **Session** resource provides operations for creating, retrieving, and managing sessions within your application. Sessions are created when a user successfully goes through the sign-in or sign-up flows. Most operations return, or work directly with, the Backend [`Session`](https://clerk.com/docs/reference/backend/types/backend-session.md) object, which is an abstraction over an HTTP session and models the period of information exchange between a user and the server.

### Clients

The **Client** resource provides operations for creating, retrieving, and managing clients within your application. Most operations return, or work directly with, the Backend [`Client`](https://clerk.com/docs/reference/backend/types/backend-client.md) object, which tracks authenticated sessions for a given device or software accessing your application, such as your web browser, native application, or Chrome Extension.

### Invitations

The **Invitation** resource allows you to manage invitations for your application. Invitations allow you to invite someone to sign up to your application, via email. Most operations return, or work directly with, the Backend [`Invitation`](https://clerk.com/docs/reference/backend/types/backend-invitation.md) object, which represents an invitation that has been sent to a potential user.

### Redirect URLs

The **Redirect URL** resource allows you to manage the redirect URLs associated with your Clerk instance. Redirect URLs are whitelisted URLs that facilitate secure authentication flows in native applications, such as React Native or Expo. In these contexts, Clerk ensures that security-critical nonces are passed only to the whitelisted URLs. Most operations return, or work directly with, the Backend [`RedirectURL`](https://clerk.com/docs/reference/backend/types/backend-redirect-url.md) object, which holds information about a redirect URL.

### Email addresses

The **Email Address** resource allows you to manage email addresses associated with your users. Email addresses are one of the identifiers used to provide identification for users. They must be verified to ensure that they are assigned to their rightful owners. Most operations return, or work directly with, the Backend [`EmailAddress`](https://clerk.com/docs/reference/backend/types/backend-email-address.md) object, which holds all necessary state around the verification process.

### Phone numbers

The **Phone Number** resource allows you to manage phone numbers associated with your users. Phone numbers can be used as a proof of identification for users, or simply as a means of contacting users. They must be verified to ensure that they are assigned to the rightful owners. Most operations return, or work directly with, the Backend [`PhoneNumber`](https://clerk.com/docs/reference/backend/types/backend-phone-number.md) object, which holds all necessary state around the verification process.

### SAML connections

The **SAML Connection** resource allows you to manage SAML connections associated with your Organizations. A SAML Connection holds configuration data required for facilitating a SAML SSO flow between your Clerk Instance (SP) and a particular SAML IdP. Most operations return, or work directly with, the Backend [`SamlConnection`](https://clerk.com/docs/reference/backend/types/backend-saml-connection.md) object, which holds information about a SAML connection for an Organization.

### Sign-in tokens

The **Sign-in Token** resource allows you to create and manage sign-in tokens for your application. Sign-in tokens are JWTs that can be used to sign in to an application without specifying any credentials. A sign-in token can be used at most once and can be consumed from the Frontend API using the `ticket` strategy.

### Agent Tasks

The **Agent Task** resource allows you to create [Agent Tasks](https://clerk.com/docs/guides/development/testing/agent-tasks.md) that generate URLs for creating sessions on behalf of users. This is useful for automated testing or agent-driven flows where full authentication isn't practical. The [`create()`](https://clerk.com/docs/reference/backend/agent-tasks/create.md) operation returns an [`AgentTask`](https://clerk.com/docs/reference/types/agent-task.md) object, which contains a `url` that, when visited, creates a session for the specified user.

### Testing Tokens

The **Testing Token** resource allows you to create and manage [Testing Tokens](https://clerk.com/docs/guides/development/testing/overview.md#testing-tokens) for your application. Testing Tokens allow you to bypass bot detection mechanisms that protect Clerk applications from malicious bots, ensuring your end-to-end test suites run smoothly. Without Testing Tokens, you may encounter "Bot traffic detected" errors in your requests.

### M2M tokens

The **M2M Token** resource allows you to create and manage [machine-to-machine (M2M) tokens](https://clerk.com/docs/guides/development/machine-auth/m2m-tokens.md) for your application. M2M tokens allow you to manage authentication between machines. It is intended primarily as a method for authenticating requests between different backend services within your own infrastructure.

### OAuth applications

The **OAuth Application** resource allows you to create and manage OAuth applications for your Clerk instance. OAuth applications contain data for clients using Clerk as an OAuth2 identity provider. Most operations return, or work directly with, the Backend [`OAuthApplication`](https://clerk.com/docs/reference/backend/types/backend-oauth-application.md) object, which holds information about an OAuth application.

## Authentication utilities

In addition to the resources listed above, [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md) is a wrapper around the Backend API that provides low-level methods that can be used to verify Clerk-generated tokens and authenticate requests from your frontend:

- [`authenticateRequest()`](https://clerk.com/docs/reference/backend/authenticate-request.md): Authenticates a token passed from the frontend.
- [`verifyToken()`](https://clerk.com/docs/reference/backend/verify-token.md): Verifies a Clerk-generated token signature.
- [`verifyWebhook()`](https://clerk.com/docs/reference/backend/verify-webhook.md): Verifies the authenticity of a webhook request using Svix.

## Error handling

The [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md) methods throw errors ([ClerkAPIResponseError](https://clerk.com/docs/reference/types/clerk-api-response-error.md)) when something goes wrong. You'll need to catch them in a `try/catch` block and handle them gracefully. For example:

filename: example.ts
```ts
try {
  const res = await someBackendApiCall()
} catch (error) {
  // Error handling
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
