# verify()

Verifies a [M2M token](https://clerk.com/docs/guides/development/machine-auth/m2m-tokens.md). Must be authenticated by a [Machine](https://clerk.com/docs/reference/backend/types/backend-machine.md) Secret Key.

Returns the verified [`M2MToken`](https://clerk.com/docs/reference/backend/types/backend-m2m-token.md) object.

```typescript
function verify(params: VerifyM2MTokenParams): Promise<M2MToken>
```

## `VerifyM2MTokenParams`

| Property                                          | Type     | Description                                                                                                                   |
| ------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------- |
| <a id="machinesecretkey"></a> `machineSecretKey?` | `string` | The custom machine secret key for authentication. If not provided, the SDK will use the value from the environment variables. |
| <a id="token"></a> `token`                        | `string` | The M2M token to verify.                                                                                                      |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.m2m.verify({ token })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/m2m_tokens/verify`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/m2m-tokens/POST/m2m_tokens/verify){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
