# revoke()

> Looking for the Publishable Key and Secret Key you use to connect your own app to Clerk? Those are different from the API keys described here. You can copy them from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard, or learn more in the [Clerk environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) reference.

Revokes the given API key. This will immediately invalidate the API key and prevent it from being used to authenticate any future requests.

Returns the revoked [`APIKey`](https://clerk.com/docs/reference/backend/types/backend-api-key.md) object.

```typescript
function revoke(params: RevokeAPIKeyParams): Promise<APIKey>
```

## `RevokeAPIKeyParams`

| Property                                          | Type                       | Description                                                   |
| ------------------------------------------------- | -------------------------- | ------------------------------------------------------------- |
| <a id="apikeyid"></a> `apiKeyId`                  | `string`                   | The ID of the API key to revoke.                              |
| <a id="revocationreason"></a> `revocationReason?` | `string | null` | The reason for revoking the API key. Useful for your records. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Revoke an API key

```tsx
const apiKeyId = 'apikey_123'

const response = await clerkClient.apiKeys.revoke({
  apiKeyId: apiKeyId,
})
```

### Revoke an API key with a reason

```tsx
const apiKeyId = 'apikey_123'

const response = await clerkClient.apiKeys.revoke({
  apiKeyId: apiKeyId,
  revocationReason: 'Key compromised',
})
```

> When you revoke an API key, it is immediately invalidated. Any requests using that API key will be rejected. Make sure to notify users or update your systems before revoking API keys that are in active use.

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/api_keys/{apiKeyID}/revoke`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/api-keys/POST/api_keys/%7BapiKeyID%7D/revoke){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
