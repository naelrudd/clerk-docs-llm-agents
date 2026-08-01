# revokeSignInToken()

Revokes the given sign-in token.

Returns the revoked [`SignInToken`](https://clerk.com/docs/reference/backend/types/backend-sign-in-token.md) object.

```typescript
function revokeSignInToken(signInTokenId: string): Promise<SignInToken>
```

## Parameters

| Parameter       | Type     | Description                            |
| --------------- | -------- | -------------------------------------- |
| `signInTokenId` | `string` | The ID of the sign-in token to revoke. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const signInTokenId = 'sit_123'

const response = await clerkClient.signInTokens.revokeSignInToken(signInTokenId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/sign_in_tokens/{sign_in_token_id}/revoke`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/sign-in-tokens/POST/sign_in_tokens/%7Bsign_in_token_id%7D/revoke){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
