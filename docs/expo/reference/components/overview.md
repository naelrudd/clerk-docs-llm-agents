# Component Reference

Clerk offers a comprehensive suite of components designed to seamlessly integrate authentication and multi-tenancy into your application. With Clerk components, you can easily customize the appearance of authentication components and pages, manage the entire authentication flow to suit your specific needs, and even build robust SaaS applications.

Expo apps can target both **native** (iOS/Android) and **web** surfaces, and Clerk ships a distinct component suite for each. Select your target platform to see the components available to it.

**Expo native**

> Expo native components are currently in beta. If you run into any issues, please reach out to the [support team](https://clerk.com/contact/support).

For **native** Expo apps, Clerk provides a dedicated suite of components rendered with SwiftUI on iOS and Jetpack Compose on Android. These are distinct from the web UI components — they don't run on Expo web.

| Component                                                                                                 | Description                                        |
| --------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| [<AuthView />](https://clerk.com/docs/expo/reference/expo/native-components/auth-view.md)                | Full sign-in and sign-up authentication UI         |
| [<UserButton />](https://clerk.com/docs/expo/reference/expo/native-components/user-button.md)            | Circular avatar button that opens the user profile |
| [<UserProfileView />](https://clerk.com/docs/expo/reference/expo/native-components/user-profile-view.md) | Complete profile management interface              |

See the [native components overview](https://clerk.com/docs/expo/reference/expo/native-components/overview.md) for installation, requirements, and theming.

You can also use Clerk's control components — [<ClerkLoaded />](https://clerk.com/docs/expo/reference/components/control/clerk-loaded.md), [<ClerkLoading />](https://clerk.com/docs/expo/reference/components/control/clerk-loading.md), and [<Show />](https://clerk.com/docs/expo/reference/components/control/show.md) — in native apps. They manage conditional rendering based on authentication state and render no UI of their own.

**Expo web**

The components below are Clerk's web UI components. Most don't work in native builds — if you're building for iOS or Android, switch to the **Expo native** tab, which also names the control components that do.

## Authentication components

- [<SignIn />](https://clerk.com/docs/expo/reference/components/authentication/sign-in.md)
- [<SignUp />](https://clerk.com/docs/expo/reference/components/authentication/sign-up.md)
- [<GoogleOneTap />](https://clerk.com/docs/expo/reference/components/authentication/google-one-tap.md)
- [<Waitlist />](https://clerk.com/docs/expo/reference/components/authentication/waitlist.md)

## User components

- [<UserAvatar />](https://clerk.com/docs/expo/reference/components/user/user-avatar.md)
- [<UserButton />](https://clerk.com/docs/expo/reference/components/user/user-button.md)
- [<UserProfile />](https://clerk.com/docs/expo/reference/components/user/user-profile.md)

## Organization components

- [<CreateOrganization />](https://clerk.com/docs/expo/reference/components/organization/create-organization.md)
- [<OrganizationProfile />](https://clerk.com/docs/expo/reference/components/organization/organization-profile.md)
- [<OrganizationSwitcher />](https://clerk.com/docs/expo/reference/components/organization/organization-switcher.md)
- [<OrganizationList />](https://clerk.com/docs/expo/reference/components/organization/organization-list.md)

## Billing components

- [<PricingTable />](https://clerk.com/docs/expo/reference/components/billing/pricing-table.md)

## Control components

Control components manage authentication-related behaviors in your application. They handle tasks such as controlling content visibility based on user authentication status, managing loading states during authentication processes, and redirecting users to appropriate pages. A common example is the [<Show />](https://clerk.com/docs/expo/reference/components/control/show.md) component, which allows you to conditionally render content based on authentication and authorization state.

- [<ClerkLoaded />](https://clerk.com/docs/expo/reference/components/control/clerk-loaded.md)
- [<ClerkLoading />](https://clerk.com/docs/expo/reference/components/control/clerk-loading.md)
- [<RedirectToTasks />](https://clerk.com/docs/expo/reference/components/control/redirect-to-tasks.md)
- [<Show />](https://clerk.com/docs/expo/reference/components/control/show.md)

## Unstyled components

- [<SignInButton />](https://clerk.com/docs/expo/reference/components/unstyled/sign-in-button.md)
- [<SignInWithMetamaskButton />](https://clerk.com/docs/expo/reference/components/unstyled/sign-in-with-metamask.md)
- [<SignUpButton />](https://clerk.com/docs/expo/reference/components/unstyled/sign-up-button.md)
- [<SignOutButton />](https://clerk.com/docs/expo/reference/components/unstyled/sign-out-button.md)

## Utilities components

- [<UNSAFE\_PortalProvider />](https://clerk.com/docs/expo/reference/components/utilities/portal-provider.md)

## Customization guides

- [Customize components with the appearance prop](https://clerk.com/docs/expo/guides/customizing-clerk/appearance-prop/overview.md)
- [Localize components with the `localization` prop (experimental)](https://clerk.com/docs/guides/customizing-clerk/localization.md?sdk=expo)
- [Add pages to the <UserProfile /> component](https://clerk.com/docs/expo/guides/customizing-clerk/adding-items/user-profile.md)
- [Add pages to the <OrganizationProfile /> component](https://clerk.com/docs/expo/guides/customizing-clerk/adding-items/organization-profile.md)

### Secured by Clerk branding

> This feature requires a [paid plan](https://clerk.com/pricing){{ target: '_blank' }} for production use, but all features are free to use in development mode so that you can try out what works for you. See the [pricing](https://clerk.com/pricing){{ target: '_blank' }} page for more information.

By default, Clerk displays a **Secured by Clerk** badge on Clerk components. You can remove this branding by following these steps:

1. In the Clerk Dashboard, navigate to your application's [**Settings**](https://dashboard.clerk.com/~/settings).
2. Under **Branding**, toggle on the **Remove "Secured by Clerk" branding** option.

- [Join the Discord community](https://clerk.com/discord): Join the official Discord community to connect with other developers.
- [Need help?](https://clerk.com/contact/support): Contact the support team to get answers to your questions.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
