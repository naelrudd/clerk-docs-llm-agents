# View Reference

Clerk offers a comprehensive suite of views designed to seamlessly integrate authentication and multi-tenancy into your application. With Clerk views, you can easily customize the appearance of authentication views and pages, manage the entire authentication flow to suit your specific needs, and even build robust SaaS applications.

## Clerk views

- [AuthView](https://clerk.com/docs/ios/reference/views/authentication/auth-view.md) - Renders a full authentication interface, supporting multiple sign-up and sign-in methods, multi-factor authentication (MFA), and password recovery flows.
- [UserButton](https://clerk.com/docs/ios/reference/views/user/user-button.md) - Displays the signed-in user's profile image.
- [UserProfileView](https://clerk.com/docs/ios/reference/views/user/user-profile-view.md) - Renders a complete user profile interface with personal information, security settings, account switching, and sign-out options.
- [OrganizationListView](https://clerk.com/docs/ios/reference/views/organization/organization-list-view.md) - Renders a standalone account picker for choosing between the user's Personal Account and Organization accounts.
- [OrganizationProfileView](https://clerk.com/docs/ios/reference/views/organization/organization-profile-view.md) - Renders the Active Organization's management interface, including members, domains, and other Organization settings.
- [OrganizationSwitcher](https://clerk.com/docs/ios/reference/views/organization/organization-switcher.md) - Renders an account switcher interface that lets signed-in users switch between their Personal and Organization accounts.

## Customization

To learn how to customize Clerk views, see the [dedicated guide](https://clerk.com/docs/ios/guides/customizing-clerk/clerk-theme.md).

> Clerk iOS views automatically localize based on the current SwiftUI locale and the device's preferred language.
> To see the languages Clerk iOS currently supports, check the SDK's [`Localizable.xcstrings`](https://github.com/clerk/clerk-ios/blob/main/Sources/ClerkKitUI/Resources/Localizable.xcstrings) file. The list of supported languages expands as Clerk adds new translations.
>
> If you want to test localization in SwiftUI, you can force a locale on the view. For example:
>
> ```swift
> AuthView()
>   .environment(\.locale, .init(identifier: "es"))
> ```
>
> For more about working with locales in SwiftUI, see Apple's [`locale` environment value documentation](https://developer.apple.com/documentation/swiftui/environmentvalues/locale).

If Clerk's prebuilt views don't meet your specific needs or if you require more control over the logic, you can rebuild the existing Clerk flows using the Clerk API. For more information, see the [custom flow guides](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=ios).

### Secured by Clerk branding

> This feature requires a [paid plan](https://clerk.com/pricing){{ target: '_blank' }} for production use, but all features are free to use in development mode so that you can try out what works for you. See the [pricing](https://clerk.com/pricing){{ target: '_blank' }} page for more information.

By default, Clerk displays a **Secured by Clerk** badge on Clerk views. You can remove this branding by following these steps:

1. In the Clerk Dashboard, navigate to your application's [**Settings**](https://dashboard.clerk.com/~/settings).
2. Under **Branding**, toggle on the **Remove "Secured by Clerk" branding** option.

- [Join the Discord community](https://clerk.com/discord): Join the official Discord community to connect with other developers.
- [Need help?](https://clerk.com/contact/support): Contact the support team to get answers to your questions.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
