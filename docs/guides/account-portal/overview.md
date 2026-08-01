# Account Portal overview

The Account Portal in Clerk provides hosted sign-in, sign-up, and profile management without requiring you to build or host your own pages. Web applications can link directly to Account Portal pages. Native applications can open Account Portal in a browser authentication session and activate the resulting session in the native SDK.

- To add Account Portal to a web application, see the [setup guide](https://clerk.com/docs/guides/account-portal/getting-started.md).
- To add Account Portal to an Expo, iOS, or Android app, see the [hosted authentication guide](https://clerk.com/docs/guides/account-portal/hosted-auth.md).

## Why use the Account Portal?

The Account Portal provides the pages necessary for your users to sign-up, sign-in, and manage their accounts, all while maintaining seamless integration with your application. These pages are hosted on Clerk servers for you and they require minimal setup to get started. If you're looking for the fastest way to add authentication and user management to your application, then this is a great choice.

However, if you require more precise customization or prefer having your application self-contained, then you can use Clerk's fully customizable [prebuilt components](https://clerk.com/docs/reference/components/overview.md), or you can build your own [custom user interface using the Clerk API](https://clerk.com/docs/guides/development/custom-flows/overview.md).

## How the Account Portal works

The Account Portal uses Clerk's [prebuilt components](https://clerk.com/docs/reference/components/overview.md), which are embedded into dedicated pages hosted on Clerk servers.

After a user finishes a flow in Account Portal, Clerk redirects them to your application with the required authentication context. In a native hosted authentication flow, the SDK activates the session in the app without retaining a separate active browser session.

For each application environment, Clerk provides pages for sign-up, sign-in, user profile, Organization profile, and Organization creation flow.

### Customizing your pages

These pages cannot be customized beyond the options provided in the [Clerk Dashboard](https://dashboard.clerk.com). If you need more customization such as [localization](https://clerk.com/docs/guides/customizing-clerk/localization.md), consider using [prebuilt components](https://clerk.com/docs/reference/components/overview.md) or building your own [custom user interface](https://clerk.com/docs/guides/development/custom-flows/overview.md).

## Available Account Portal pages

### Sign-in

The sign-in page hosts the prebuilt [<SignIn />](https://clerk.com/docs/reference/components/authentication/sign-in.md) component, which renders a UI for signing in users. The functionality of the `<SignIn />` component is controlled by the instance settings you specify in the [Clerk Dashboard](https://dashboard.clerk.com), such as [sign-up and sign-in options](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md) and [social connections](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/overview.md). The `<SignIn />` component also displays any session tasks that are required for the user to complete after signing in.

Redirect users to the sign-in page using the [<RedirectToSignIn />](https://clerk.com/docs/reference/components/control/redirect-to-sign-in.md) control component.

### Sign-up

The sign-up page hosts the prebuilt [<SignUp />](https://clerk.com/docs/reference/components/authentication/sign-up.md) component, which renders a UI for signing up users. The functionality of the `<SignUp />` component is controlled by the instance settings you specify in the [Clerk Dashboard](https://dashboard.clerk.com), such as [sign-up and sign-in options](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md) and [social connections](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/overview.md). The `<SignUp />` component also displays any session tasks that are required for the user to complete after signing up.

Redirect users to the sign-up page using the [<RedirectToSignUp />](https://clerk.com/docs/reference/components/control/redirect-to-sign-up.md) control component.

### User profile

The user profile page hosts the prebuilt [<UserProfile />](https://clerk.com/docs/reference/components/user/user-profile.md) component, which renders a beautiful, full-featured account management UI that allows users to manage their profile and security settings.

Redirect your authenticated users to their user profile page using the [<RedirectToUserProfile />](https://clerk.com/docs/reference/components/control/redirect-to-user-profile.md) control component.

### Unauthorized sign-in

The unauthorized sign-in page doesn't host any prebuilt Clerk component. It displays a UI confirming that a session from an unrecognized device was successfully revoked. For more information, see the [Unauthorized sign-in](https://clerk.com/docs/guides/secure/best-practices/unauthorized-sign-in.md) feature.

### Create Organization

The create Organization page hosts the prebuilt [<CreateOrganization />](https://clerk.com/docs/reference/components/organization/create-organization.md) component, which provides a streamlined interface for users to create new Organizations within your application.

Redirect your authenticated users to the create Organization page using the [<RedirectToCreateOrganization />](https://clerk.com/docs/reference/components/control/redirect-to-create-organization.md) control component.

### Organization Profile

The Organization profile page hosts the prebuilt [<OrganizationProfile />](https://clerk.com/docs/reference/components/organization/organization-profile.md) component, which renders a beautiful, full-featured Organization management UI that allows users to manage their Organization profile and security settings.

Redirect your authenticated users to their Organization Profile page using the [<RedirectToOrganizationProfile />](https://clerk.com/docs/reference/components/control/redirect-to-organization-profile.md) control component.

### Waitlist

The waitlist page hosts the prebuilt [<Waitlist />](https://clerk.com/docs/reference/components/authentication/waitlist.md) component which renders a form that allows users to join for early access to your app.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
