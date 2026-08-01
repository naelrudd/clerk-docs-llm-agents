# create()

> Looking for the Publishable Key and Secret Key you use to connect your own app to Clerk? Those are different from the API keys described here. You can copy them from the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard, or learn more in the [Clerk environment variables](https://clerk.com/docs/guides/development/clerk-environment-variables.md) reference.

Creates a new API key for the given user or Organization.

Returns the created [`APIKey`](https://clerk.com/docs/reference/backend/types/backend-api-key.md) object.

```typescript
function create(params: CreateAPIKeyParams): Promise<APIKey>
```

## `CreateAPIKeyParams`

| Property                                                      | Type                                    | Description                                                                          |
| ------------------------------------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------ |
| <a id="claims"></a> `claims?`                                 | <code>Record<string, any> | null</code> | Custom claims to store additional information about the API key.                     |
| <a id="createdby"></a> `createdBy?`                           | `string | null`              | The user ID of the user who created the API key.                                     |
| <a id="description"></a> `description?`                       | `string | null`              | The description of the API key.                                                      |
| <a id="name"></a> `name`                                      | `string`                                | A descriptive name for the API key (e.g., "Production API Key", "Development Key").  |
| <a id="scopes"></a> `scopes?`                                 | `string[]`                   | Scopes to limit the API key's access to specific resources.                          |
| <a id="secondsuntilexpiration"></a> `secondsUntilExpiration?` | `number | null`              | The number of seconds until the API key expires. Defaults to `null` (never expires). |
| <a id="subject"></a> `subject`                                | `string`                                | The user or Organization ID to associate the API key with.                           |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Create a basic API key

```tsx
const userId = 'user_123'

const apiKey = await clerkClient.apiKeys.create({
  name: 'My API Key',
  subject: userId,
})
```

### Create an API key with optional parameters

```tsx
const userId = 'user_123'

const apiKey = await clerkClient.apiKeys.create({
  name: 'Production API Key',
  subject: userId,
  description: 'API key for accessing my application',
  scopes: ['read:users', 'write:users'],
  secondsUntilExpiration: 86400, // expires in 24 hours
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/api_keys`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/api-keys/POST/api_keys){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
