# getSecret()

> Looking for the Publishable Key and Secret Key you use to connect your own app to Clerk? Those are different from the API keys described here. You can copy them from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard, or learn more in the [Clerk environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) reference.

Gets the secret of the given API key.

```typescript
function getSecret(apiKeyId: string): Promise<{ secret: string }>
```

## Parameters

| Parameter  | Type     | Description                                 |
| ---------- | -------- | ------------------------------------------- |
| `apiKeyId` | `string` | The ID of the API key to get the secret of. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.apiKeys.getSecret('apikey_123')
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/api_keys/{apiKeyId}/secret`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/api-keys/GET/api_keys/%7BapiKeyID%7D/secret){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
