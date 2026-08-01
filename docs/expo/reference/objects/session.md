# Session object

The `Session` object is an abstraction over an HTTP session. It models the period of information exchange between a user and the server.

The `Session` object includes methods for recording session activity and ending the session client-side. For security reasons, sessions can also expire server-side.

As soon as a [User](https://clerk.com/docs/expo/reference/objects/user.md) signs in, Clerk creates a `Session` for the current [Client](https://clerk.com/docs/expo/reference/objects/client.md). Clients can have more than one sessions at any point in time, but only one of those sessions will be **active**.

In certain scenarios, a session might be replaced by another one. This is often the case with [multi-session applications](https://clerk.com/docs/guides/secure/session-options.md?sdk=expo#multi-session-applications).

All sessions that are **expired**, **removed**, **replaced**, **ended** or **abandoned** are not considered valid.

> For more information regarding the different session states, see the [guide on session management](https://clerk.com/docs/guides/secure/session-options.md?sdk=expo).

## Example

The following example uses the [useSession()](https://clerk.com/docs/expo/reference/hooks/use-session.md) hook to access the [Session](https://clerk.com/docs/expo/reference/objects/session.md) object. The `Session` object is used to access the `lastActiveAt` property, which is a `Date` object used to show the time the session was last active.

filename: src/app/(session)/page.tsx
```tsx
import { useSession } from '@clerk/expo'
import { Text, View } from 'react-native'

export default function HomePage() {
  const { isLoaded, session, isSignedIn } = useSession()

  // Handle loading state
  if (!isLoaded)
    return (
      <View>
        <Text>Loading...</Text>
      </View>
    )

  // Protect the page from unauthenticated users
  if (!isSignedIn)
    return (
      <View>
        <Text>Sign in to view this page</Text>
      </View>
    )

  return (
    <View>
      <Text>This session has been active since {session.lastActiveAt.toLocaleString()}</Text>
    </View>
  )
}
```

## Properties

| Property                                                         | Type                                                                                                        | Description                                                                                                                                                                                                                |
| ---------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="abandonat"></a> `abandonAt`                               | `Date`                                                                                                      | The date and time when the session was abandoned by the user.                                                                                                                                                              |
| <a id="actor"></a> `actor`                                       | `null | { [x: string]: unknown; sub: string; type?: "agent"; }`                                  | The JWT actor for the session. Holds identifier for the user that is impersonating the current user. Read more about [impersonation](https://clerk.com/docs/guides/users/impersonation.md?sdk=expo).                       |
| `actor.sub`                                                      | `string`                                                                                                    | The identifier for the user that is impersonating the current user.                                                                                                                                                        |
| `actor.type?`                                                    | `"agent"`                                                                                                   | The type of the actor.                                                                                                                                                                                                     |
| <a id="agent"></a> `agent`                                       | `null | { [x: string]: unknown; sub: string; type?: "agent"; } & { type: "agent"; }`             | When the session's actor claim has `type: 'agent'`, this property exposes information about the agent and [Agent Task](https://clerk.com/docs/reference/types/agent-task.md?sdk=expo) that was used to create the session. |
| <a id="createdat"></a> `createdAt`                               | `Date`                                                                                                      | The date and time when the session was first created.                                                                                                                                                                      |
| <a id="currenttask"></a> `currentTask?`                          | [SessionTask](https://clerk.com/docs/expo/reference/types/session-task.md)                                  | The user's current pending [session task](https://clerk.com/docs/guides/configure/session-tasks.md?sdk=expo).                                                                                                              |
| <a id="expireat"></a> `expireAt`                                 | `Date`                                                                                                      | The date and time when the session will expire.                                                                                                                                                                            |
| <a id="factorverificationage"></a> `factorVerificationAge`       | `null | [number, number]`                                                                        | An array where each item represents the number of minutes since the last verification of a first or second factor: `[firstFactorAge, secondFactorAge]`.                                                                    |
| <a id="id"></a> `id`                                             | `string`                                                                                                    | The unique identifier for the session.                                                                                                                                                                                     |
| <a id="lastactiveat"></a> `lastActiveAt`                         | `Date`                                                                                                      | The date and time when the session was last active on the [Client](https://clerk.com/docs/expo/reference/objects/client.md).                                                                                               |
| <a id="lastactiveorganizationid"></a> `lastActiveOrganizationId` | `null | string`                                                                                  | The ID of the last Active Organization.                                                                                                                                                                                    |
| <a id="lastactivetoken"></a> `lastActiveToken`                   | `null | TokenResource`                                                                           | The token that was last used to authenticate the session.                                                                                                                                                                  |
| <a id="publicuserdata"></a> `publicUserData`                     | [PublicUserData](https://clerk.com/docs/expo/reference/types/public-user-data.md)                           | Publicly available information about the current [User](https://clerk.com/docs/expo/reference/objects/user.md).                                                                                                            |
| <a id="status"></a> `status`                                     | [SessionStatus](https://clerk.com/docs/expo/reference/types/session-status.md)                              | The current state of the session.                                                                                                                                                                                          |
| <a id="tasks"></a> `tasks`                                       | <code>null | <a href="https://clerk.com/docs/expo/reference/types/session-task.md">SessionTask</a>[]</code> | The user's pending [session tasks](https://clerk.com/docs/guides/configure/session-tasks.md?sdk=expo).                                                                                                                     |
| <a id="updatedat"></a> `updatedAt`                               | `Date`                                                                                                      | The date and time when the session was last updated.                                                                                                                                                                       |
| <a id="user"></a> `user`                                         | <code>null | <a href="https://clerk.com/docs/expo/reference/objects/user.md">UserResource</a></code>        | The [User](https://clerk.com/docs/expo/reference/objects/user.md) associated with the session.                                                                                                                             |

## Methods

### `attemptFirstFactorVerification()`

Attempts to complete the first factor verification process.

Returns a [SessionVerification](https://clerk.com/docs/expo/reference/types/session-verification.md) instance with its status and supported factors.

```typescript
function attemptFirstFactorVerification(attemptFactor: SessionVerifyAttemptFirstFactorParams): Promise<SessionVerificationResource>
```

#### `SessionVerifyAttemptFirstFactorParams`

```ts
type SessionVerifyAttemptFirstFactorParams =
  | EmailCodeAttempt
  | PhoneCodeAttempt
  | PasswordAttempt
  | PasskeyAttempt

type EmailCodeAttempt = {
  strategy: 'email_code'
  code: string
}

type PhoneCodeAttempt = {
  strategy: 'phone_code'
  code: string
}

type PasswordAttempt = {
  strategy: 'password'
  password: string
}

type PasskeyAttempt = {
  strategy: 'passkey'
  publicKeyCredential: PublicKeyCredentialWithAuthenticatorAssertionResponse
}
```

### `attemptSecondFactorVerification()`

Attempts to complete the second factor verification process.

Returns a [SessionVerification](https://clerk.com/docs/expo/reference/types/session-verification.md) instance with its status and supported factors.

```typescript
function attemptSecondFactorVerification(params: SessionVerifyAttemptSecondFactorParams): Promise<SessionVerificationResource>
```

#### `SessionVerifyAttemptSecondFactorParams`

```ts
type SessionVerifyAttemptSecondFactorParams = PhoneCodeAttempt | TOTPAttempt | BackupCodeAttempt

type PhoneCodeAttempt = {
  strategy: 'phone_code'
  code: string
}

type TOTPAttempt = {
  strategy: 'totp'
  code: string
}

type BackupCodeAttempt = {
  strategy: 'backup_code'
  code: string
}
```

### `checkAuthorization()`

Checks if the user is [authorized for the specified Role, Permission, Feature, or Plan](https://clerk.com/docs/guides/secure/authorization-checks.md?sdk=expo) or requires the user to [reverify their credentials](https://clerk.com/docs/guides/secure/reverification.md?sdk=expo) if their last verification is older than allowed.

```typescript
function checkAuthorization(isAuthorizedParams: CheckAuthorizationParams): boolean
```

#### `CheckAuthorizationParams`

```typescript
type WithReverification<T> = T & {
  /**
   * The reverification configuration to check for. This feature is currently in public beta. **It is not recommended for production use.** See https://clerk.com/docs/reference/backend/types/auth-object#reverification-config for more information.
   */
  reverification?: ReverificationConfig
}

type CheckAuthorizationParams = WithReverification<
  | {
      /**
       * The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions) to check for.
       */
      role: OrganizationCustomRoleKey
      /**
       * The [Permission](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions) to check for.
       */
      permission?: never
      /**
       * The [Feature](https://clerk.com/docs/guides/secure/features) to check for.
       */
      feature?: never
      /**
       * The [Plan](https://clerk.com/docs/guides/billing/overview) to check for.
       */
      plan?: never
    }
  | {
      role?: never
      permission: OrganizationPermissionKey
      feature?: never
      plan?: never
    }
  | {
      role?: never
      permission?: never
      feature: Autocomplete<`user:${string}` | `org:${string}`>
      plan?: never
    }
  | {
      role?: never
      permission?: never
      feature?: never
      plan: Autocomplete<`user:${string}` | `org:${string}`>
    }
  | { role?: never; permission?: never; feature?: never; plan?: never }
>
```

### `clearCache()`

Clears the cache for the current session. This is useful if the session has been updated and the cache is no longer valid.

```typescript
function clearCache(): void
```

### `end()`

Marks the session as ended. The session will no longer be active for this `Client` and its status will become **ended**.

```typescript
function end(): Promise<SessionResource>
```

### `getToken()`

Gets the current user's [session token](https://clerk.com/docs/guides/sessions/session-tokens.md?sdk=expo) or a [custom JWT template](https://clerk.com/docs/guides/sessions/jwt-templates.md?sdk=expo).

This method uses a cache so a network request will only be made if the token in memory has expired. The TTL for a Clerk token is one minute. It retries on transient failures (e.g., network errors); when the browser is offline and retries are exhausted, it throws `ClerkOfflineError`.

Tokens can only be generated if the user is signed in.

```typescript
function getToken(options?: GetTokenOptions): Promise<null | string>
```

#### `GetTokenOptions`

| Property                                      | Type      | Description                                                                                                                                                                                                                 |
| --------------------------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="organizationid"></a> `organizationId?` | `string`  | The Organization associated with the generated session token. _Does not modify the session's currently Active Organization._                                                                                                |
| <a id="skipcache"></a> `skipCache?`           | `boolean` | Whether to skip the cache lookup and force a call to the server instead, even within the TTL. Useful if the token claims are time-sensitive or depend on data that can be updated (e.g., user fields). Defaults to `false`. |
| <a id="template"></a> `template?`             | `string`  | The name of the JWT template from the [Clerk Dashboard](https://dashboard.clerk.com/~/jwt-templates) to generate a new token from. E.g., 'firebase', 'grafbase', or your custom template's name.                            |

### `prepareFirstFactorVerification()`

Initiates the first factor verification process. This is a required step to complete a reverification flow when using a preparable factor.

Returns a [SessionVerification](https://clerk.com/docs/expo/reference/types/session-verification.md) instance with its status and supported factors.

```typescript
function prepareFirstFactorVerification(factor: SessionVerifyPrepareFirstFactorParams): Promise<SessionVerificationResource>
```

#### `SessionVerifyPrepareFirstFactorParams`

```ts
type SessionVerifyPrepareFirstFactorParams =
  | EmailCodeConfig
  | PhoneCodeConfig
  | PassKeyConfig
  | Omit<EnterpriseSSOConfig, 'actionCompleteRedirectUrl'>

type EmailCodeConfig = {
  /**
   * The strategy type.
   */
  strategy: 'email_code'
  /**
   * The ID of the email address used for the email code factor.
   */
  emailAddressId: string
  /**
   * Indicates whether the email address is set as the primary email address, as multiple can be added to a user's profile.
   */
  primary?: boolean
}

type PhoneCodeConfig = {
  /**
   * The strategy type.
   */
  strategy: 'phone_code'
  /**
   * The ID of the phone number used for the phone code factor.
   */
  phoneNumberId: string
  /**
   * Indicates whether the phone number is set as the primary phone number, as multiple can be added to a user's profile.
   */
  primary?: boolean
  /**
   * Indicates whether the phone number is set as the default identifier.
   */
  default?: boolean
  /**
   * The channel used for the phone code factor.
   */
  channel?: 'sms' | 'whatsapp'
}

type PassKeyConfig = {
  /**
   * The strategy type.
   */
  strategy: 'passkey'
}

type EnterpriseSSOConfig = {
  /**
   * The strategy type.
   */
  strategy: 'enterprise_sso'
  /**
   * The ID of the enterprise connection.
   * @experimental
   */
  enterpriseConnectionId?: string
  /**
   * The name of the enterprise connection.
   * @experimental
   */
  enterpriseConnectionName?: string
  /**
   * The URL to redirect to after the OAuth flow is completed.
   */
  redirectUrl: string
  /**
   * The OIDC prompt parameter to use for the OAuth flow.
   */
  oidcPrompt?: string
  /**
   * The ID of the email address used for the enterprise SSO factor.
   * @experimental
   */
  emailAddressId?: string
}
```

### `prepareSecondFactorVerification()`

Initiates the second factor verification process. This is a required step to complete a reverification flow when using a preparable factor.

Returns a [SessionVerification](https://clerk.com/docs/expo/reference/types/session-verification.md) instance with its status and supported factors.

```typescript
function prepareSecondFactorVerification(params: PhoneCodeSecondFactorConfig): Promise<SessionVerificationResource>
```

#### `PhoneCodeSecondFactorConfig`

```ts
type PhoneCodeSecondFactorConfig = {
  /**
   * The strategy type.
   */
  strategy: 'phone_code'
  /**
   * The ID of the phone number used for the phone code second factor.
   */
  phoneNumberId?: string
}
```

### `remove()`

Invalidates the current session by marking it as removed. Once removed, the session will be deactivated for the current Client instance and its `status` will be set to `removed`. This operation cannot be undone.

```typescript
function remove(): Promise<SessionResource>
```

### `startVerification()`

Initiates the reverification flow.

Returns a [SessionVerification](https://clerk.com/docs/expo/reference/types/session-verification.md) instance with its status and supported factors.

```typescript
function startVerification(params: SessionVerifyCreateParams): Promise<SessionVerificationResource>
```

#### `SessionVerifyCreateParams`

| Property                   | Type                                                           | Description                              |
| -------------------------- | -------------------------------------------------------------- | ---------------------------------------- |
| <a id="level"></a> `level` | `"first_factor" | "second_factor" | "multi_factor"` | The level of the verification to create. |

### `touch()`

Updates the session's last active timestamp to the current time. This method should be called periodically to indicate ongoing user activity and prevent the session from becoming stale. The updated timestamp is used for session management and analytics purposes.

```typescript
function touch(params?: SessionTouchParams): Promise<SessionResource>
```

#### `SessionTouchParams`

| Property                      | Type                                                   | Description                        |
| ----------------------------- | ------------------------------------------------------ | ---------------------------------- |
| <a id="intent"></a> `intent?` | `"focus" | "select_session" | "select_org"` | The intent of the touch operation. |

### `verifyWithPasskey()`

Initiates a verification flow using passkeys.

Returns a [SessionVerification](https://clerk.com/docs/expo/reference/types/session-verification.md) instance with its status and supported factors.

```typescript
function verifyWithPasskey(): Promise<SessionVerificationResource>
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
