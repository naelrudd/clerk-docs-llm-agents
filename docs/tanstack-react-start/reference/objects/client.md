# Client object

The `Client` object keeps track of the authenticated sessions in the current device. The device can be a browser, a native application, or any other medium that is usually the requesting part in a request/response architecture.

The `Client` object also holds information about any sign-in or sign-up attempts that might be in progress, tracking the sign-in or sign-up progress.

## Example

The `Client` object is available on the [Clerk](https://clerk.com/docs/tanstack-react-start/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/tanstack-react-start/reference/hooks/use-clerk.md) hook to access the `clerk` object, as shown in the following example.

filename: app/routes/index.tsx
```tsx
import { useClerk } from '@clerk/tanstack-react-start'
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/')({
  component: Home,
})

export default function Home() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Access the client object
  const client = clerk.client

  return <pre>{JSON.stringify(client, null, 2)}</pre>
}
```

## Properties

| Property                                                             | Type                                                                                                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="captchabypass"></a> `captchaBypass`                           | `boolean`                                                                                                                                                | Indicates whether CAPTCHA checks are skipped for this client.                                                                                                                                                                                                                                                                                                                                         |
| <a id="cookieexpiresat"></a> `cookieExpiresAt`                       | `null | Date`                                                                                                                                 | The date and time when the client's authentication cookie will expire.                                                                                                                                                                                                                                                                                                                                |
| <a id="createdat"></a> `createdAt`                                   | `null | Date`                                                                                                                                 | The date and time when the client was created.                                                                                                                                                                                                                                                                                                                                                        |
| <a id="id"></a> `id?`                                                | `string`                                                                                                                                                 | The unique identifier of the resource.                                                                                                                                                                                                                                                                                                                                                                |
| <a id="lastactivesessionid"></a> `lastActiveSessionId`               | `null | string`                                                                                                                               | The ID of the last active [Session](https://clerk.com/docs/tanstack-react-start/reference/objects/session.md) on this client.                                                                                                                                                                                                                                                                         |
| <a id="lastauthenticationstrategy"></a> `lastAuthenticationStrategy` | <code>null | <a href="https://clerk.com/docs/tanstack-react-start/reference/types/last-authentication-strategy.md">LastAuthenticationStrategy</a></code> | The last authentication strategy used by this client; `null` when unknown or feature disabled.                                                                                                                                                                                                                                                                                                        |
| <a id="sessions"></a> `sessions`                                     | <code><a href="https://clerk.com/docs/tanstack-react-start/reference/objects/session.md">SessionResource</a>[]</code>                                    | A list of sessions that have been created on this client.                                                                                                                                                                                                                                                                                                                                             |
| <a id="signedinsessions"></a> `signedInSessions`                     | <code><a href="https://clerk.com/docs/tanstack-react-start/reference/objects/session.md">SignedInSessionResource</a>[]</code>                            | A list of sessions on this client where the user has completed the full sign-in flow. Sessions can be in one of the following states: <ul> <li>`"active"`: The user has completed the full sign-in flow and all pending tasks.</li> <li>`"pending"`: The user has completed the sign-in flow but still needs to complete one or more required steps (pending tasks).</li> </ul> |
| <a id="signin"></a> `signIn`                                         | [SignInResource](https://clerk.com/docs/tanstack-react-start/reference/objects/sign-in.md)                                                               | The current sign-in attempt.                                                                                                                                                                                                                                                                                                                                                                          |
| <a id="signup"></a> `signUp`                                         | [SignUpResource](https://clerk.com/docs/tanstack-react-start/reference/objects/sign-up.md)                                                               | The current sign-up attempt.                                                                                                                                                                                                                                                                                                                                                                          |
| <a id="updatedat"></a> `updatedAt`                                   | `null | Date`                                                                                                                                 | The date and time when the client was last updated.                                                                                                                                                                                                                                                                                                                                                   |

## Methods

### `buildTouchUrl()`

Builds a URL that refreshes the current client's authentication state and then redirects the user to the specified URL.

```typescript
function buildTouchUrl(params: { redirectUrl: URL }): string
```

#### Parameters

| Parameter | Type                               | Description                      |
| --------- | ---------------------------------- | -------------------------------- |
| `params`  | `{ redirectUrl: URL; }` | The URL to redirect the user to. |

### `clearCache()`

Clears any locally cached session data for the current client.

```typescript
function clearCache(): void
```

### `create()`

Creates a new client for the current instance along with its cookie.

```typescript
function create(): Promise<ClientResource>
```

### `destroy()`

Deletes the client. All sessions will be reset.

```typescript
function destroy(): Promise<void>
```

### `isEligibleForTouch()`

Indicates whether the client cookie is due to expire in 8 days or less.

```typescript
function isEligibleForTouch(): boolean
```

### `isNew()`

Indicates whether this client hasn't been saved (created) yet in the Frontend API.

```typescript
function isNew(): boolean
```

### `reload()`

Reloads the resource, which is useful when you want to access the latest user data after performing a mutation. To make the updated data immediately available, this method forces a session token refresh instead of waiting for the automatic refresh cycle that could temporarily retain stale information. Learn more about [forcing a token refresh](https://clerk.com/docs/guides/sessions/force-token-refresh.md?sdk=tanstack-react-start).

```typescript
function reload(p?: ClerkResourceReloadParams): Promise<ClientResource>
```

#### `ClerkResourceReloadParams`

| Property                                              | Type     | Description                                                                                                                                                                   |
| ----------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="rotatingtokennonce"></a> `rotatingTokenNonce?` | `string` | A nonce to use for rotating the user's token. Used in native application OAuth flows to allow the native client to update its JWT once despite changes in its rotating token. |

### `removeSessions()`

Removes all sessions created on the client.

```typescript
function removeSessions(): Promise<ClientResource>
```

### `resetSignIn()`

Resets the current sign-in attempt. Clears the in-progress sign-in state on the client.

```typescript
function resetSignIn(): void
```

### `resetSignUp()`

Resets the current sign-up attempt. Clears the in-progress sign-up state on the client.

```typescript
function resetSignUp(): void
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
