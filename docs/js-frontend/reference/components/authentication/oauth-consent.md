# <OAuthConsent /> component

The `<OAuthConsent />` component renders an OAuth consent screen for authenticated users after they are redirected to the OAuth authorization page. It retrieves the OAuth application's consent metadata and displays the requested scopes, allowing the user to approve or deny access.

By default, `<OAuthConsent />` reads the OAuth `client_id`, `scope`, and `redirect_uri` from the current URL. You can override the `client_id` and `scope` with props when rendering the component on a custom route.

For route setup guidance and security considerations, see [Set up a custom OAuth consent page](https://clerk.com/docs/js-frontend/guides/configure/auth-strategies/oauth/custom-consent-page.md).

> `<OAuthConsent />` only renders for authenticated users. If the user is signed out, the component will not be displayed.

> Pages that host OAuth consent flows must set the referrer policy to `strict-origin-when-cross-origin`. This ensures the cross-origin `POST` request to FAPI includes the `Origin` header and Clerk can validate the CSRF token.

## Usage with JavaScript

Add the following `<meta>` tag to the page that hosts the OAuth consent screen:

filename: index.html
```html
<meta name="referrer" content="strict-origin-when-cross-origin" />
```

The following methods available on an instance of the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) class are used to render and control the `<OAuthConsent />` component:

- [mountOAuthConsent()](https://clerk.com/docs/js-frontend/reference/components/authentication/oauth-consent.md#mount-o-auth-consent)
- [unmountOAuthConsent()](https://clerk.com/docs/js-frontend/reference/components/authentication/oauth-consent.md#unmount-o-auth-consent)

The following examples assume that you have followed the [quickstart](https://clerk.com/docs/js-frontend/getting-started/quickstart.md) in order to add Clerk to your JavaScript application.

### `mountOAuthConsent()`

Render the `<OAuthConsent />` component to an HTML `<div>` element.

```typescript
function mountOAuthConsent(node: HTMLDivElement, props?: OAuthConsentProps): void
```

#### `mountOAuthConsent()` params

| Name   | Type              | Description                                                                  |
| ------ | ----------------- | ---------------------------------------------------------------------------- |
| node   | HTMLDivElement    | The container <div> element used to render the <OAuthConsent /> component. |
| props? | OAuthConsentProps | The properties to pass to the <OAuthConsent /> component.                   |

#### `mountOAuthConsent()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

const clerkPubKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

const clerk = new Clerk(clerkPubKey)
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="oauth-consent"></div>
`

const oauthConsentDiv = document.getElementById('oauth-consent')

clerk.mountOAuthConsent(oauthConsentDiv)
```

### `unmountOAuthConsent()`

Unmount and run cleanup on an existing `<OAuthConsent />` component instance.

```typescript
function unmountOAuthConsent(node: HTMLDivElement): void
```

#### `unmountOAuthConsent()` params

| Name | Type           | Description                                                                        |
| ---- | -------------- | ---------------------------------------------------------------------------------- |
| node | HTMLDivElement | The container <div> element with a rendered <OAuthConsent /> component instance. |

#### `unmountOAuthConsent()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

const clerkPubKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

const clerk = new Clerk(clerkPubKey)
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="oauth-consent"></div>
`

const oauthConsentDiv = document.getElementById('oauth-consent')

clerk.mountOAuthConsent(oauthConsentDiv)

// ...

clerk.unmountOAuthConsent(oauthConsentDiv)
```

## Properties

All props are optional.

| Name           | Type                    | Description                                                                                                        |
| -------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------ |
| appearance?    | Appearance | undefined | An object to style your components. Will only affect Clerk components and not Account Portal pages.                |
| fallback?      | ReactNode               | An element to be rendered while the component is mounting.                                                         |
| oauthClientId? | string                  | Override the OAuth client ID. By default, Clerk reads this from the client\_id query parameter in the current URL. |
| scope?         | string                  | Override the OAuth scope. By default, Clerk reads this from the scope query parameter in the current URL.          |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
