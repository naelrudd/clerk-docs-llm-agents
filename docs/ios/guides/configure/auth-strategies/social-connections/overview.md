# Social connections (OAuth)

**Before you start**

- [A Clerk application is required.](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md?sdk=ios)
- [Follow the quickstart guide.](https://clerk.com/docs/getting-started/quickstart.md?sdk=ios)

Social connections, also known as OAuth connections in Clerk, allow users to gain access to your application by using their existing credentials from an Identity Provider (IdP), like Google or Microsoft. For example, if you enable Google as a social provider, then when a user wants to sign in to your application, they can select Google and use their Google account to sign in.

> When using social connections, the sign-up and sign-in flows are equivalent. If a user doesn't have an account and tries to sign in, an account will be made for them, and vice versa.

The easiest way to add social connections to your Clerk app is by using [prebuilt views](https://clerk.com/docs/ios/reference/views/overview.md). If you require more control over the logic, you can [build a custom OAuth flow using the Clerk API](https://clerk.com/docs/guides/development/custom-flows/authentication/oauth-connections.md?sdk=ios).

## Enable a social connection

**For AI agents:** Instead of enabling providers through the Dashboard steps below, run `npx clerk@latest config patch --json '{"connection_oauth_<provider>":{"enabled":true}}'` (e.g., `connection_oauth_google`, `connection_oauth_github`). Discover all provider keys with `npx clerk@latest config schema`. Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md?sdk=ios) with `npx skills add clerk/skills` for correct CLI and SDK usage.

1. In the Clerk Dashboard, navigate to the [**SSO connections**](https://dashboard.clerk.com/~/user-authentication/sso-connections) page.
2. Select the **Add connection** button, and select **For all users**.
3. Select the provider you want to use.
4. Enabling **Enable for sign-up and sign-in** will depend on your use case:
   - If you want to allow users to sign up and sign in using the provider, enable this option.
   - If you want to allow users to link their account with this provider to their Clerk account, but not use it for sign-up or sign-in, disable this option. Users can manage their social connections on their user profile page.
5. Enabling **Use custom credentials** will depend on your instance type:
   - For **development** instances, Clerk uses **pre-configured, shared credentials** to make the setup process as smooth as possible. For most social providers, you can leave this option disabled.
   - For **production** instances, you need to configure the provider with custom OAuth credentials. See the [list of supported providers](https://clerk.com/docs/ios/guides/configure/auth-strategies/social-connections/overview.md#supported-social-providers) for provider-specific setup instructions.
6. Select **Enable connection** when you're ready for the connection to be available to your users.

### Allowlist OAuth redirect URLs

In addition to enabling a social connection in the Clerk Dashboard, native applications require allowlisting the redirect URLs used during the OAuth flow.

Clerk ensures that security critical nonces are passed only to allowlisted URLs when the SSO flow is completed in native browsers or webviews. For maximum security in your **production** instances, you need to allowlist your custom redirect URLs via the [Clerk Dashboard](https://dashboard.clerk.com/) or the [Clerk Backend API](https://clerk.com/docs/reference/backend/redirect-urls/create-redirect-url.md?sdk=ios).

To allowlist a redirect URL via the Clerk Dashboard:

1. In the Clerk Dashboard, navigate to the [**Native applications**](https://dashboard.clerk.com/~/native-applications) page.
2. Scroll down to the **Allowlist for mobile SSO redirect** section and add your redirect URLs.

> By default, Clerk uses `{bundleIdentifier}://callback` as the redirect URL.

## Configure additional OAuth scopes

Each OAuth provider requires a specific set of scopes that are necessary for proper authentication with Clerk. **These essential scopes are pre-configured and automatically included by Clerk.** They typically include permissions for basic profile information and email access, which are fundamental for user authentication and account creation.

In addition to the essential scopes, you can specify additional scopes supported by the provider. These scopes can be used to access additional user data from the provider.

To add additional OAuth scopes, when you [enable a new social connection](https://clerk.com/docs/ios/guides/configure/auth-strategies/social-connections/overview.md#enable-a-social-connection), enable **Use custom credentials**. The **Scopes** field will appear.

## Request additional OAuth scopes after sign-up

Clerk allows you to request additional OAuth scopes even after a user has signed up.

Apply the `.userProfileOAuthConfig(_:)` modifier to the [UserProfileView](https://clerk.com/docs/ios/reference/views/user/user-profile-view.md) or [UserButton](https://clerk.com/docs/ios/reference/views/user/user-button.md) view, with any additional OAuth scopes you would like per provider. The user will be prompted to reconnect their account on their user profile page.

Use the following tabs to see how to add additional OAuth scopes to the `UserProfileView` and `UserButton` views.

**UserProfileView**

```swift
UserProfileView()
  .userProfileOAuthConfig([
    .init(provider: .google, additionalScopes: ["foo", "bar"]),
    .init(provider: .github, additionalScopes: ["qux"]),
  ])
```

**UserButton**

```swift
UserButton()
  .userProfileOAuthConfig([
    .init(provider: .google, additionalScopes: ["foo", "bar"]),
    .init(provider: .github, additionalScopes: ["qux"]),
  ])
```

## Sign in with Apple

You can use [Apple's Sign in with Apple feature](https://developer.apple.com/sign-in-with-apple/) to offer a native authentication experience in your iOS, watchOS, macOS, or tvOS apps.

Instead of the typical OAuth flow that redirects through a browser, you can use Apple's native authentication and send the resulting ID token and authorization code to Clerk. Clerk verifies the user against the information Apple provides.

For additional information, see the [Sign in with Apple guide](https://clerk.com/docs/ios/guides/configure/auth-strategies/sign-in-with-apple.md).

## Supported social providers

Clerk provides a wide range of social providers to ease your users' sign-up and sign-in processes. Select a provider to learn how to configure it for your Clerk app.

- [Apple](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/apple.md?sdk=ios): Add Apple as an authentication provider for your Clerk app.
- [Atlassian](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/atlassian.md?sdk=ios): Add Atlassian as an authentication provider for your Clerk app.
- [Bitbucket](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/bitbucket.md?sdk=ios): Add Bitbucket as an authentication provider for your Clerk app.
- [Box](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/box.md?sdk=ios): Add Box as an authentication provider for your Clerk app.
- [Coinbase](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/coinbase.md?sdk=ios): Add Coinbase as an authentication provider for your Clerk app.
- [Discord](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/discord.md?sdk=ios): Add Discord as an authentication provider for your Clerk app.
- [Dropbox](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/dropbox.md?sdk=ios): Add Dropbox as an authentication provider for your Clerk app.
- [Facebook](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/facebook.md?sdk=ios): Add Facebook as an authentication provider for your Clerk app.
- [GitHub](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/github.md?sdk=ios): Add GitHub as an authentication provider for your Clerk app.
- [GitLab](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/gitlab.md?sdk=ios): Add GitLab as an authentication provider for your Clerk app.
- [Google](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/google.md?sdk=ios): Add Google as an authentication provider for your Clerk app.
- [HubSpot](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/hubspot.md?sdk=ios): Add HubSpot as an authentication provider for your Clerk app.
- [Hugging Face](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/hugging-face.md?sdk=ios): Add Hugging Face as an authentication provider for your Clerk app.
- [LINE](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/line.md?sdk=ios): Add LINE as an authentication provider for your Clerk app.
- [Linear](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/linear.md?sdk=ios): Add Linear as an authentication provider for your Clerk app.
- [LinkedIn](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/linkedin-oidc.md?sdk=ios): Add LinkedIn as an authentication provider for your Clerk app.
- [Microsoft](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/microsoft.md?sdk=ios): Add Microsoft as an authentication provider for your Clerk app.
- [Notion](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/notion.md?sdk=ios): Add Notion as an authentication provider for your Clerk app.
- [Slack](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/slack.md?sdk=ios): Add Slack as an authentication provider for your Clerk app.
- [Spotify](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/spotify.md?sdk=ios): Add Spotify as an authentication provider for your Clerk app.
- [TikTok](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/tiktok.md?sdk=ios): Add TikTok as an authentication provider for your Clerk app.
- [Twitch](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/twitch.md?sdk=ios): Add Twitch as an authentication provider for your Clerk app.
- [Vercel](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/vercel.md?sdk=ios): Add Vercel as an authentication provider for your Clerk app.
- [X/Twitter v2](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/x-twitter.md?sdk=ios): Add X (Twitter v2) as an authentication provider for your Clerk app.
- [Xero](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/xero.md?sdk=ios): Add Xero as an authentication provider for your Clerk app.

Don't see the provider you're looking for? You can [configure a custom OIDC-compatible provider](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/custom-provider.md?sdk=ios) or [request a new one](https://feedback.clerk.com/roadmap).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
