# createSignInToken()

Creates a new sign-in token for the given user. By default, sign-in tokens expire in 30 days. You can optionally specify a custom expiration time in seconds using the `expiresInSeconds` parameter.

Returns the created [`SignInToken`](https://clerk.com/docs/reference/backend/types/backend-sign-in-token.md) object.

```typescript
function createSignInToken(params: CreateSignInTokensParams): Promise<SignInToken>
```

## `CreateSignInTokensParams`

| Property                                         | Type     | Description                                                                                                                                                       |
| ------------------------------------------------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="expiresinseconds"></a> `expiresInSeconds` | `number` | The number of seconds until the sign-in token expires. By default, the duration is `2592000` (30 days).                                                           |
| <a id="orgid"></a> `orgId?`                      | `string` | The ID of the organization to activate when the user signs in. Organizations must be enabled for the instance, and the user must be a member of the organization. |
| <a id="userid"></a> `userId`                     | `string` | The ID of the user to create the sign-in token for.                                                                                                               |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'
const orgId = 'org_123'

const expiresInSeconds = 60 * 60 * 24 * 7 // 1 week

const response = await clerkClient.signInTokens.createSignInToken({
  userId,
  orgId,
  expiresInSeconds,
})
```

The `orgId` parameter scopes the token to an Organization: when the token is redeemed, Clerk activates that Organization for the new session. Organizations must be enabled for the instance, and the user must be a member of the Organization. To consume the returned token in a native app, pass `response.token` to [signInWithTicket() for Android](https://clerk.com/docs/android/reference/native-mobile/auth.md#sign-in-with-ticket) or [signInWithTicket() for iOS](https://clerk.com/docs/ios/reference/native-mobile/auth.md#sign-in-with-ticket).

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST /sign_in_tokens`. The SDK's `orgId` parameter is sent to the Backend API as `org_id`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/sign-in-tokens/POST/sign_in_tokens){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
