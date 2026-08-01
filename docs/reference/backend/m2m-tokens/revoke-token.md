# revokeToken()

> Only opaque tokens can be revoked. JWT tokens are not stored by Clerk and therefore cannot be revoked. If you need revocation capability, use the default opaque token format when creating tokens.

Revokes an [M2M token](https://clerk.com/docs/guides/development/machine-auth/m2m-tokens.md). This endpoint can be authenticated by either a [Machine](https://clerk.com/docs/reference/backend/types/backend-machine.md) Secret Key or by a Clerk Secret Key.

- When revoking M2M tokens with a [Machine](https://clerk.com/docs/reference/backend/types/backend-machine.md) Secret Key, the token will be revoked using the machine secret key.
- When revoking M2M tokens with a Clerk Secret Key, the token will be revoked using the instance secret key.

Returns the revoked [`M2MToken`](https://clerk.com/docs/reference/backend/types/backend-m2m-token.md) object.

```typescript
function revokeToken(params: RevokeM2MTokenParams): Promise<M2MToken>
```

## `RevokeM2MTokenParams`

| Property                                          | Type                       | Description                                                                                                                   |
| ------------------------------------------------- | -------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <a id="m2mtokenid"></a> `m2mTokenId`              | `string`                   | The ID of the M2M token to revoke.                                                                                            |
| <a id="machinesecretkey"></a> `machineSecretKey?` | `string`                   | The custom machine secret key for authentication. If not provided, the SDK will use the value from the environment variables. |
| <a id="revocationreason"></a> `revocationReason?` | `string | null` | The reason for revoking the M2M token. Useful for your records.                                                               |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.m2m.revokeToken({ m2mTokenId })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/m2m_tokens/{m2m_token_id}/revoke`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/m2m-tokens/POST/m2m_tokens/%7Bm2m_token_id%7D/revoke){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
