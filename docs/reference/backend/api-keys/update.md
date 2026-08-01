# update()

> Looking for the Publishable Key and Secret Key you use to connect your own app to Clerk? Those are different from the API keys described here. You can copy them from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard, or learn more in the [Clerk environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) reference.

Updates the given API key.

Returns the updated [`APIKey`](https://clerk.com/docs/reference/backend/types/backend-api-key.md) object.

```typescript
function update(params: UpdateAPIKeyParams): Promise<APIKey>
```

## `UpdateAPIKeyParams`

| Property                                                      | Type                                    | Description                                                                          |
| ------------------------------------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------ |
| <a id="apikeyid"></a> `apiKeyId`                              | `string`                                | The ID of the API key to update.                                                     |
| <a id="claims"></a> `claims?`                                 | <code>Record<string, any> | null</code> | Custom claims to store additional information about the API key.                     |
| <a id="description"></a> `description?`                       | `string | null`              | The description of the API key.                                                      |
| <a id="scopes"></a> `scopes?`                                 | `string[]`                   | Scopes to limit the API key's access to specific resources.                          |
| <a id="secondsuntilexpiration"></a> `secondsUntilExpiration?` | `number | null`              | The number of seconds until the API key expires. Defaults to `null` (never expires). |
| <a id="subject"></a> `subject`                                | `string`                                | The user or Organization ID to associate the API key with.                           |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const apiKeyId = 'apikey_123'
const userId = 'user_123'

const response = await clerkClient.apiKeys.update({
  apiKeyId: apiKeyId,
  subject: userId,
  description: 'API key for accessing my application',
  scopes: ['read:users', 'write:users'],
  secondsUntilExpiration: 86400, // expires in 24 hours
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/api_keys/{apiKeyID}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/api-keys/PATCH/api_keys/%7BapiKeyID%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
