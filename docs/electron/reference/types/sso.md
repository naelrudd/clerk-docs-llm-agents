# SSO Types

The types on this page describe the SSO values accepted by Clerk SDK methods.

Your SDK does not export these types and does not provide a `/types` entry point. To import them, first install `@clerk/shared`:

```npm
npm install @clerk/shared
```

Then, use a type-only import from `@clerk/shared/types`:

```ts
import type {
  OAuthProvider,
  OAuthStrategy,
  CustomOAuthStrategy,
  EnterpriseSSOStrategy,
} from '@clerk/shared/types'
```

## `OAuthStrategy`

A type that represents the OAuth strategy for a given provider.

For example, when creating a [SignIn](https://clerk.com/docs/electron/reference/objects/sign-in.md#signincreateparams) or [SignUp](https://clerk.com/docs/electron/reference/objects/sign-up.md#signupcreateparams), you can pass the `strategy` option to specify the OAuth strategy to use.

```ts
type OAuthStrategy = `oauth_${OAuthProvider}` | CustomOAuthStrategy
```

## `OAuthProvider`

A type that represents the provider portion of an OAuth strategy. For example, the provider is `'google'`, while the corresponding [OAuthStrategy](https://clerk.com/docs/electron/reference/types/sso.md#oauthstrategy) is `'oauth_google'`.

```ts
type OAuthProvider =
  | 'facebook'
  | 'google'
  | 'hubspot'
  | 'github'
  | 'tiktok'
  | 'gitlab'
  | 'discord'
  | 'twitter'
  | 'twitch'
  | 'linkedin'
  | 'linkedin_oidc'
  | 'dropbox'
  | 'atlassian'
  | 'bitbucket'
  | 'microsoft'
  | 'notion'
  | 'apple'
  | 'line'
  | 'instagram'
  | 'coinbase'
  | 'spotify'
  | 'xero'
  | 'box'
  | 'slack'
  | 'linear'
  | 'x'
  | 'enstall'
  | 'huggingface'
  | 'vercel'
  | 'agentid'
  | `custom_${string}`
```

## `CustomOAuthStrategy`

A type that represents a [custom OAuth strategy](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/custom-provider.md?sdk=electron).

```ts
type CustomOAuthStrategy = `oauth_custom_${string}`
```

## `EnterpriseSSOStrategy`

A type that represents an [Enterprise SSO](https://clerk.com/docs/guides/configure/auth-strategies/enterprise-connections/authentication-flows.md?sdk=electron) strategy.

```ts
type EnterpriseSSOStrategy = `enterprise_sso`
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
