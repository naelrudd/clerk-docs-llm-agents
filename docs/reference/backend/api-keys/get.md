# get()

> Looking for the Publishable Key and Secret Key you use to connect your own app to Clerk? Those are different from the API keys described here. You can copy them from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard, or learn more in the [Clerk environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) reference.

Gets the given [`APIKey`](https://clerk.com/docs/reference/backend/types/backend-api-key.md) object.

```typescript
function get(apiKeyId: string): Promise<APIKey>
```

## Parameters

| Parameter  | Type     | Description                   |
| ---------- | -------- | ----------------------------- |
| `apiKeyId` | `string` | The ID of the API key to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const apiKeyId = 'apikey_123'

const response = await clerkClient.apiKeys.get(apiKeyId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/api_keys/{apiKeyId}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/api-keys/GET/api_keys/%7BapiKeyID%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
