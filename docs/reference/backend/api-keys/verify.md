# verify()

> Looking for the Publishable Key and Secret Key you use to connect your own app to Clerk? Those are different from the API keys described here. You can copy them from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard, or learn more in the [Clerk environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) reference.

> In most cases, you'll want to verify API keys using framework-specific helpers like `auth()` in Next.js, which handles the verification automatically. See the [verifying API keys](https://clerk.com/docs/guides/development/verifying-api-keys.md) guide for more details.

Verifies the given API key.

- If the API key is valid, the method returns the API key object with its properties.
- If the API key is invalid, revoked, or expired, the method will throw an error.

Returns the verified [`APIKey`](https://clerk.com/docs/reference/backend/types/backend-api-key.md) object.

```typescript
function verify(secret: string): Promise<APIKey>
```

## Parameters

| Parameter | Type     | Description                          |
| --------- | -------- | ------------------------------------ |
| `secret`  | `string` | The secret of the API key to verify. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const apiKeySecret = 'ak_live_123'

const response = await clerkClient.apiKeys.verify(apiKeySecret)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/api_keys/verify`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/api-keys/POST/api_keys/verify){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
