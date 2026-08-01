# Clerk Nuxt SDK

The Clerk Nuxt SDK gives you access to prebuilt components, composables, and helpers to make user authentication easier. Refer to the [quickstart guide](https://clerk.com/docs/nuxt/getting-started/quickstart.md) to get started.

## Integration

To configure Clerk with Nuxt, you must pass the `@clerk/nuxt` module to your Nuxt config in your `nuxt.config.ts` file. See the [reference](https://clerk.com/docs/reference/nuxt/integration.md) for more information on configuring the module, including setting Clerk options like `signInForceRedirectUrl`.

## Client-side helpers

Because the Nuxt SDK is built on top of the Clerk Vue SDK, you can use the composables that the Vue SDK provides. These composables include access to the [Clerk](https://clerk.com/docs/reference/objects/clerk.md) object, [User object](https://clerk.com/docs/reference/objects/user.md), [Organization object](https://clerk.com/docs/reference/objects/organization.md), and a set of useful helper methods for signing in and signing up. Learn more in the [Clerk Vue SDK reference](https://clerk.com/docs/reference/vue/overview.md).

- [useUser()](https://clerk.com/docs/reference/composables/use-user.md)
- [useClerk()](https://clerk.com/docs/reference/composables/use-clerk.md)
- [useAuth()](https://clerk.com/docs/reference/composables/use-auth.md)
- [useSignIn()](https://clerk.com/docs/reference/composables/use-sign-in.md)
- [useSignUp()](https://clerk.com/docs/reference/composables/use-sign-up.md)
- [useSession()](https://clerk.com/docs/reference/composables/use-session.md)
- [useSessionList()](https://clerk.com/docs/reference/composables/use-session-list.md)
- [useOrganization()](https://clerk.com/docs/reference/composables/use-organization.md)

## Objects

Learn about the [key Clerk objects](https://clerk.com/docs/reference/objects/overview.md) that power many of Clerk's SDKs.

## Types

See the [reference docs on types](https://clerk.com/docs/reference/types/overview.md) to get more information about the different types available for typing your application.

## `Auth` object

The `Auth` object is available at `event.context.auth()` in your [event handlers](https://h3.unjs.io/guide/event-handler). This JavaScript object contains important information like session data, your user's ID, as well as their Organization ID. [Learn more](https://clerk.com/docs/reference/backend/types/auth-object.md).

### `event.context.auth()` options

| Name                                                                            | Type                                                                                                                        | Description |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------- |
| acceptsToken?: The type of authentication token(s) to accept. Valid values are: | treatPendingAsSignedOut?: A boolean that indicates whether to treat pending session status as signed out. Defaults to true. |             |

### Example: Protect a route based on token type

The following example uses `event.context.auth()` to protect the route based on token type:

- It accepts any token type `(acceptsToken: 'any')` from the request.
- If the token is a `session_token`, it logs that the request is from a user session.
- Otherwise, it logs that the request uses a machine token and specifies its type.

```ts
export default eventHandler((event) => {
  // Use `event.context.auth()` to protect a route based on token type
  const authObject = event.context.auth({ acceptsToken: 'any' })

  if (authObject.tokenType === 'session_token') {
    console.log('This is a session token from a user')
  } else {
    console.log(`This is a ${authObject.tokenType} token`)
  }

  return {}
})
```

## `clerkMiddleware()`

The `clerkMiddleware()` helper integrates Clerk authentication and authorization into your Nuxt application through middleware. [Learn more](https://clerk.com/docs/reference/nuxt/clerk-middleware.md).

## `clerkClient`

[`clerkClient`](https://clerk.com/docs/reference/backend/overview.md) is a wrapper around the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }} that makes it easier to interact with the API. For example, to retrieve a list of all users in your application, you can use the `users.getUserList()` method instead of manually making a fetch request to the `https://api.clerk.com/v1/users` endpoint.

To access a resource, you must first instantiate a `clerkClient` instance. See the [reference documentation](https://clerk.com/docs/reference/backend/overview.md) for more information.

[Learn more](https://clerk.com/docs/guides/users/reading.md).

## Protect pages and API routes

To protect pages, use the `useAuth()` helper to protect a single page, or use Nuxt's built-in [route middleware](https://nuxt.com/docs/4.x/guide/directory-structure/middleware) to protect multiple pages. [Learn more](https://clerk.com/docs/guides/secure/protect-content.md).

To protect API routes (`/api/**`), use the `clerkMiddleware()` helper. [Learn more](https://clerk.com/docs/reference/nuxt/clerk-middleware.md).

> [!QUIZ]
> When protecting pages/routes using middleware, what is the difference between using `defineNuxtRouteMiddleware()` and `clerkMiddleware()`? Why not use one or the other?
>
> ***
>
> `defineNuxtRouteMiddleware()` is used to protect pages only and cannot protect API routes. `clerkMiddleware()` is used to protect API routes. It can protect pages, **but on initial page reload only**. On subsequent navigations, it won't run, because client-side navigation doesn't reach the server middleware.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
