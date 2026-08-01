# Clerk TanStack React Start SDK

The Clerk TanStack React Start SDK gives you access to prebuilt components, React hooks, and helpers to make user authentication easier. Refer to the [quickstart guide](https://clerk.com/docs/tanstack-react-start/getting-started/quickstart.md) to get started.

## Client-side helpers

Because the TanStack React Start SDK is built on top of the React SDK, you can use the hooks that the React SDK provides. These hooks include access to the [Clerk](https://clerk.com/docs/reference/objects/clerk.md) object, [User object](https://clerk.com/docs/reference/objects/user.md), [Organization object](https://clerk.com/docs/reference/objects/organization.md), and a set of useful helper methods for signing in and signing up. Learn more in the [Clerk React SDK reference](https://clerk.com/docs/reference/react/overview.md).

- [useUser()](https://clerk.com/docs/reference/hooks/use-user.md)
- [useClerk()](https://clerk.com/docs/reference/hooks/use-clerk.md)
- [useAuth()](https://clerk.com/docs/reference/hooks/use-auth.md)
- [useOAuthConsent()](https://clerk.com/docs/reference/hooks/use-oauth-consent.md)
- [useSignIn()](https://clerk.com/docs/reference/hooks/use-sign-in.md)
- [useSignUp()](https://clerk.com/docs/reference/hooks/use-sign-up.md)
- [useWaitlist()](https://clerk.com/docs/reference/hooks/use-waitlist.md)
- [useSession()](https://clerk.com/docs/reference/hooks/use-session.md)
- [useSessionList()](https://clerk.com/docs/reference/hooks/use-session-list.md)
- [useOrganization()](https://clerk.com/docs/reference/hooks/use-organization.md)
- [useOrganizationList()](https://clerk.com/docs/reference/hooks/use-organization-list.md)
- [useOrganizationCreationDefaults()](https://clerk.com/docs/reference/hooks/use-organization-creation-defaults.md)
- [useReverification()](https://clerk.com/docs/reference/hooks/use-reverification.md)
- [useCheckout()](https://clerk.com/docs/reference/hooks/use-checkout.md)
- [usePaymentElement()](https://clerk.com/docs/reference/hooks/use-payment-element.md)
- [usePaymentMethods()](https://clerk.com/docs/reference/hooks/use-payment-methods.md)
- [usePlans()](https://clerk.com/docs/reference/hooks/use-plans.md)
- [useSubscription()](https://clerk.com/docs/reference/hooks/use-subscription.md)
- [usePaymentAttempts()](https://clerk.com/docs/reference/hooks/use-payment-attempts.md)
- [useStatements()](https://clerk.com/docs/reference/hooks/use-statements.md)
- [useAPIKeys()](https://clerk.com/docs/reference/hooks/use-api-keys.md)

## Server-side helpers

The following references show how to integrate Clerk features into applications using TanStack React Start server functions and API routes.

- [auth()](https://clerk.com/docs/reference/tanstack-react-start/auth.md)
- [clerkMiddleware()](https://clerk.com/docs/reference/tanstack-react-start/clerk-middleware.md)

### `clerkClient`

[`clerkClient`](https://clerk.com/docs/reference/backend/overview.md) is a wrapper around the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }} that makes it easier to interact with the API. For example, to retrieve a list of all users in your application, you can use the `users.getUserList()` method instead of manually making a fetch request to the `https://api.clerk.com/v1/users` endpoint.

To access a resource, you must first instantiate a `clerkClient` instance. See the [reference documentation](https://clerk.com/docs/reference/backend/overview.md) for more information.

### `Auth` object

The `auth()` returns an `Auth` object. This JavaScript object contains important information like session data, your user's ID, as well as their Organization ID. Learn more about the `Auth` object [here](https://clerk.com/docs/reference/backend/types/auth-object.md).

## Objects

Learn about the [key Clerk objects](https://clerk.com/docs/reference/objects/overview.md) that power many of Clerk's SDKs.

## Types

See the [reference docs on types](https://clerk.com/docs/reference/types/overview.md) to get more information about the different types available for typing your application.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
