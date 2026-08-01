# Clerk React SDK

The Clerk React SDK is built on top of the [JavaScript SDK](https://clerk.com/docs/reference/javascript/overview.md) and gives you access to prebuilt components, hooks, and helpers to make user authentication easier. Refer to the [quickstart guide](https://clerk.com/docs/react/getting-started/quickstart.md) to get started.

## Custom hooks

The React SDK provides hooks that include access to the [Clerk](https://clerk.com/docs/reference/objects/clerk.md) object, [User object](https://clerk.com/docs/reference/objects/user.md), [Organization object](https://clerk.com/docs/reference/objects/organization.md), and a set of useful helper methods for signing in and signing up.

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

## Objects

Learn about the [key Clerk objects](https://clerk.com/docs/reference/objects/overview.md) that power many of Clerk's SDKs.

## Types

See the [reference docs on types](https://clerk.com/docs/reference/types/overview.md) to get more information about the different types available for typing your application.

## Framework-specific SDKs

> Clerk provides optimized SDKs for specific React frameworks. If you're using one of the supported frameworks below, you should use its dedicated SDK instead of `@clerk/react`.

Clerk offers framework-specific SDKs that are customized to provide the better developer experience and integration with each framework's features. Choose the appropriate SDK based on your framework:

| Framework            | Package                       | Docs                                                                                          |
| -------------------- | ----------------------------- | --------------------------------------------------------------------------------------------- |
| Next.js              | `@clerk/nextjs`               | [Next.js SDK](https://clerk.com/docs/reference/nextjs/overview.md)                            |
| React Router         | `@clerk/react-router`         | [React Router SDK](https://clerk.com/docs/reference/react-router/overview.md)                 |
| Astro                | `@clerk/astro`                | [Astro SDK](https://clerk.com/docs/reference/astro/overview.md)                               |
| TanStack React Start | `@clerk/tanstack-react-start` | [TanStack React Start SDK](https://clerk.com/docs/reference/tanstack-react-start/overview.md) |

## Set up Clerk React

Before you can add Clerk to your React application, you must create a Clerk app in the Clerk Dashboard. To get started, follow the [setup guide](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md). Then, follow the [quickstart guide](https://clerk.com/docs/react/getting-started/quickstart.md) to set up the React SDK in your app.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
