# auth()

The `auth()` helper returns the [`Auth`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=nextjs){{ target: '_blank' }} object of the currently active user, as well as the [redirectToSignIn()](https://clerk.com/docs/nextjs/reference/app-router/auth.md#redirect-to-sign-in) method. It includes a single method, `protect()`, which you can use to check if a user is authenticated or authorized to access certain parts of your application or even entire routes.

- Only available for App Router.
- Only works on the server-side, such as in Server Components, Route Handlers, and Server Actions.
- Requires [clerkMiddleware()](https://clerk.com/docs/nextjs/reference/clerk-middleware.md) to be configured.

## Parameters

| Name                                                                            | Type                                                                                                                        | Description |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------- |
| acceptsToken?: The type of authentication token(s) to accept. Valid values are: | treatPendingAsSignedOut?: A boolean that indicates whether to treat pending session status as signed out. Defaults to true. |             |

## `auth.protect()`

`auth` includes a single property, the `protect()` method, which you can use in three ways:

- to check if a user is authenticated (signed in)
- to check if a user is authorized (has the correct Role, Permission, Feature, or Plan) to access something, such as a component or a route handler
- to check if a request includes a valid machine token (e.g., API key or OAuth token) and enforce access rules accordingly

The following table describes how `auth.protect()` behaves based on user authentication or authorization status:

| Authenticated | Authorized | `auth.protect()` will                                                                                                       |
| ------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------- |
| Yes           | Yes        | Return the [`Auth`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=nextjs){{ target: '_blank' }} object. |
| Yes           | No         | Return a `404` error.                                                                                                       |
| No            | No         | Redirect the user to the sign-in page.                                                                                      |

> For non-document requests, such as API requests, `auth.protect()` returns:
>
> - A `401` error for unauthenticated Server Action requests.
> - A `404` error for other unauthenticated requests with session token type.
> - A `401` error for unauthenticated requests with machine token types.

`auth.protect()` accepts the following parameters:

| Name                 | Type                                                                           | Description                                                                                                               |
| -------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| role?                | string                                                                         | The Role to check for.                                                                                                    |
| permission?          | string                                                                         | The Permission to check for.                                                                                              |
| has?                 | (isAuthorizedParams: CheckAuthorizationParamsWithCustomPermissions) => boolean | A function that checks if the user has an Organization Role or Custom Permission. See the reference for more information. |
| unauthorizedUrl?     | string                                                                         | The URL to redirect the user to if they are not authorized.                                                               |
| unauthenticatedUrl?  | string                                                                         | The URL to redirect the user to if they are not authenticated.                                                            |
| A single token type. | An array of token types.                                                       | Defaults to 'session\_token'.                                                                                             |

### Example

`auth.protect()` can be used to check:

- A signed-in user: See detailed examples in the [guide on protecting content from unauthenticated users](https://clerk.com/docs/nextjs/guides/secure/protect-content.md).
- A specific Role, Permission, Feature, or Plan: See detailed examples in the [guide on authorization checks](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=nextjs).
- Machine requests (API keys, OAuth tokens, machine tokens): See the [section on verifying machine requests](https://clerk.com/docs/nextjs/reference/app-router/auth.md#verify-machine-requests).

## Returns

The `auth()` helper returns the following:

- The [`Auth`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=nextjs){{ target: '_blank' }} object.
- The [redirectToSignIn()](https://clerk.com/docs/nextjs/reference/app-router/auth.md#redirect-to-sign-in) method.

### `redirectToSignIn()`

The `auth()` helper returns the `redirectToSignIn()` method, which you can use to redirect the user to the sign-in page.

`redirectToSignIn()` accepts the following parameters:

| Name           | Type          | Description                                              |
| -------------- | ------------- | -------------------------------------------------------- |
| returnBackUrl? | string | URL | The URL to redirect the user back to after they sign in. |

> `auth()` on the server-side can only access redirect URLs defined via [environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md?sdk=nextjs#sign-in-and-sign-up-redirects) or [clerkMiddleware dynamic keys](https://clerk.com/docs/nextjs/reference/clerk-middleware.md#dynamic-keys).

#### Example

The following example shows how to use `redirectToSignIn()` to redirect the user to the sign-in page if they are not authenticated. For more detailed examples, see the [guide on protecting content from unauthenticated users](https://clerk.com/docs/nextjs/guides/secure/protect-content.md).

filename: app/page.tsx
```tsx
import { auth } from '@clerk/nextjs/server'

export default async function Page() {
  const { isAuthenticated, redirectToSignIn, userId } = await auth()

  if (!isAuthenticated) return redirectToSignIn()

  return <h1>Hello, {userId}</h1>
}
```

## `auth()` usage

### Protect pages and routes

You can use `auth()` to check if `isAuthenticated` is true. If it's false, then there is not an authenticated (signed in) user. See detailed examples in the [guide on protecting content from unauthenticated users](https://clerk.com/docs/nextjs/guides/secure/protect-content.md).

### Check if a user is authorized

You can use `auth()` to check if a user is authorized to access certain parts of your application or even entire routes by checking their type of access control. See detailed examples in the [guide on verifying if a user is authorized](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=nextjs).

### Verify machine requests

You can use `auth()` to verify the following machine tokens by passing in the `acceptsToken` parameter:

- OAuth access tokens: See detailed examples in the [guide on verifying OAuth access tokens](https://clerk.com/docs/nextjs/guides/development/verifying-oauth-access-tokens.md).
- [M2M (machine-to-machine) tokens](https://clerk.com/docs/guides/development/machine-auth/m2m-tokens.md?sdk=nextjs)
- API keys: See detailed examples in the [guide on verifying API keys](https://clerk.com/docs/nextjs/guides/development/verifying-api-keys.md).

### Data fetching with `getToken()`

If you need to send a JWT along to a server, such as when making authenticated requests to an external API, use the `getToken()` method. `getToken()` retrieves the current user's [session token](https://clerk.com/docs/guides/sessions/session-tokens.md?sdk=nextjs) or a [custom JWT template](https://clerk.com/docs/guides/sessions/jwt-templates.md?sdk=nextjs). See detailed examples in the [`Auth` object reference](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=nextjs#get-token){{ target: '_blank' }}.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
