# OAuthApplication

The `OAuthApplication` object provides helpers for building custom OAuth consent flows in Clerk.

Use this object together with the [useOAuthConsent()](https://clerk.com/docs/reference/hooks/use-oauth-consent.md) hook or the [<OAuthConsent />](https://clerk.com/docs/vue/reference/components/authentication/oauth-consent.md) component when you need to render a custom consent page for an OAuth application.

## Methods

### `buildConsentActionUrl()`

Returns the URL to use as the `action` attribute of your consent form. Clerk includes the current session context automatically, including `_clerk_session_id` and, in development, the dev browser JWT.

```typescript
function buildConsentActionUrl(params: { clientId: string }): string
```

#### Parameters

| Name     | Type   | Description                                      |
| -------- | ------ | ------------------------------------------------ |
| clientId | string | The OAuth client\_id from the authorize request. |

#### Example

```tsx
const actionUrl = clerk.oauthApplication.buildConsentActionUrl({
  clientId,
})
```

### `getConsentInfo()`

Loads the consent metadata for a signed-in user and OAuth application. Returns a [OAuthConsentInfo](https://clerk.com/docs/vue/reference/types/oauth-consent-info.md) object.

Use this method when you want to build your own consent UI without the [useOAuthConsent()](https://clerk.com/docs/reference/hooks/use-oauth-consent.md) hook.

```typescript
function getConsentInfo(params: GetOAuthConsentInfoParams): Promise<OAuthConsentInfo>
```

#### `GetOAuthConsentInfoParams`

| Name          | Type   | Description                                                |
| ------------- | ------ | ---------------------------------------------------------- |
| oauthClientId | string | The OAuth client\_id from the authorize request.           |
| scope?        | string | A space-delimited scope string from the authorize request. |

#### Example

```tsx
const consentInfo = await clerk.oauthApplication.getConsentInfo({
  oauthClientId: clientId,
  scope,
})
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
