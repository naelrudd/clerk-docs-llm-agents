# Clerk Expo SDK

The Clerk Expo SDK gives you access to prebuilt components, React hooks, and helpers to make user authentication easier. Refer to the [quickstart guide](https://clerk.com/docs/expo/getting-started/quickstart.md) to get started.

## Hosted authentication

[useHostedAuth()](https://clerk.com/docs/expo/reference/native-hooks/use-hosted-auth.md) opens Clerk's [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md?sdk=expo) in a browser authentication session and activates the session created there. Choose hosted authentication for the fastest setup and support for every authentication method enabled in the Clerk Dashboard.

See the [hosted authentication guide](https://clerk.com/docs/expo/guides/account-portal/hosted-auth.md) for setup instructions and tradeoffs.

## Components

### Native components

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

Prebuilt native components rendered with **SwiftUI** on iOS and **Jetpack Compose** on Android. These components require a [development build](https://docs.expo.dev/develop/development-builds/introduction/).

- [<AuthView />](https://clerk.com/docs/expo/reference/native-components/auth-view.md) - Renders a full authentication interface, supporting multiple sign-up and sign-in methods, multi-factor authentication (MFA), and password recovery flows.
- [<UserButton />](https://clerk.com/docs/expo/reference/native-components/user-button.md) - Displays the signed-in user's profile image.
- [<UserProfileView />](https://clerk.com/docs/expo/reference/native-components/user-profile-view.md) - Renders a complete user profile interface with personal information, security settings, account switching, and sign-out options.

See the [native components overview](https://clerk.com/docs/expo/reference/native-components/overview.md) for more details.

### Control components

These components work across all approaches:

- [<Show>](https://clerk.com/docs/expo/reference/components/control/show.md) - Conditionally render content based on auth state
- [<ClerkLoaded>](https://clerk.com/docs/expo/reference/components/control/clerk-loaded.md) - Render children after Clerk loads
- [<ClerkLoading>](https://clerk.com/docs/expo/reference/components/control/clerk-loading.md) - Render children while Clerk loads

### Web components

All Clerk components are available from `@clerk/expo/web` for Expo web projects. See [the component docs](https://clerk.com/docs/expo/reference/components/overview.md) for more information.

## Hooks

### Native sign-in hooks

Hooks for native OAuth authentication without browser redirects. These hooks require a [development build](https://docs.expo.dev/develop/development-builds/introduction/).

- [useSignInWithApple()](https://clerk.com/docs/expo/reference/native-hooks/use-sign-in-with-apple.md) - Native Sign in with Apple (iOS only)
- [useSignInWithGoogle()](https://clerk.com/docs/expo/reference/native-hooks/use-sign-in-with-google.md) - Native Sign in with Google (iOS and Android)
- [useSSO()](https://clerk.com/docs/expo/reference/native-hooks/use-sso.md) - Browser-based SSO and OAuth flows

### Expo-specific hooks

Hooks designed specifically for Expo environments. These provide additional authentication capabilities, such as biometric credential management and browser-based OAuth flows.

- [useHostedAuth()](https://clerk.com/docs/expo/reference/native-hooks/use-hosted-auth.md) - Hosted sign-in and sign-up through Account Portal
- [useLocalCredentials()](https://clerk.com/docs/expo/reference/native-hooks/use-local-credentials.md) - Biometric credential management
- [useOAuth()](https://clerk.com/docs/expo/reference/native-hooks/use-oauth.md) - Browser-based OAuth flows

### React hooks

Because the Expo SDK is built on top of the Clerk React SDK, you can use the hooks that the React SDK provides. These hooks include access to the [Clerk](https://clerk.com/docs/expo/reference/objects/clerk.md) object, [User object](https://clerk.com/docs/expo/reference/objects/user.md), [Organization object](https://clerk.com/docs/expo/reference/objects/organization.md), and a set of useful helper methods for signing in and signing up.

- [useUser()](https://clerk.com/docs/expo/reference/hooks/use-user.md)
- [useClerk()](https://clerk.com/docs/expo/reference/hooks/use-clerk.md)
- [useAuth()](https://clerk.com/docs/expo/reference/hooks/use-auth.md)
- [useOAuthConsent()](https://clerk.com/docs/reference/hooks/use-oauth-consent.md)
- [useSignIn()](https://clerk.com/docs/expo/reference/hooks/use-sign-in.md)
- [useSignUp()](https://clerk.com/docs/expo/reference/hooks/use-sign-up.md)
- [useWaitlist()](https://clerk.com/docs/expo/reference/hooks/use-waitlist.md)
- [useSession()](https://clerk.com/docs/expo/reference/hooks/use-session.md)
- [useSessionList()](https://clerk.com/docs/expo/reference/hooks/use-session-list.md)
- [useOrganization()](https://clerk.com/docs/expo/reference/hooks/use-organization.md)
- [useOrganizationList()](https://clerk.com/docs/expo/reference/hooks/use-organization-list.md)
- [useOrganizationCreationDefaults()](https://clerk.com/docs/expo/reference/hooks/use-organization-creation-defaults.md)
- [useReverification()](https://clerk.com/docs/reference/hooks/use-reverification.md)
- [useCheckout()](https://clerk.com/docs/reference/hooks/use-checkout.md)
- [usePaymentElement()](https://clerk.com/docs/reference/hooks/use-payment-element.md)
- [usePaymentMethods()](https://clerk.com/docs/reference/hooks/use-payment-methods.md)
- [usePlans()](https://clerk.com/docs/reference/hooks/use-plans.md)
- [useSubscription()](https://clerk.com/docs/reference/hooks/use-subscription.md)
- [usePaymentAttempts()](https://clerk.com/docs/reference/hooks/use-payment-attempts.md)
- [useStatements()](https://clerk.com/docs/reference/hooks/use-statements.md)
- [useAPIKeys()](https://clerk.com/docs/reference/hooks/use-api-keys.md)

## Custom flows

Clerk provides prebuilt components for **native** applications and **web** applications. Use the components that correspond to your platform:

- For native apps, see the [native components](https://clerk.com/docs/expo/reference/native-components/overview.md).
- For web apps, see the [web components](https://clerk.com/docs/expo/reference/components/overview.md).

If the prebuilt components don't meet your needs, you can build [custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=expo) using the Clerk API.

## Configure passkeys

To configure passkeys for your Expo app, see the [passkeys configuration guide](https://clerk.com/docs/expo/reference/passkeys.md).

## Deploy your app

To learn how to deploy your Expo application, see the [dedicated guide](https://clerk.com/docs/expo/guides/development/deployment/expo.md).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
