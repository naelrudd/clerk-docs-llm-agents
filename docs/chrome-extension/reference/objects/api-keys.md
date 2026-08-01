# APIKeys object

The `APIKeys` object provides methods for managing API keys that allow your application's users to grant third-party services programmatic access to your application's API endpoints on their behalf. API keys are long-lived, opaque tokens that can be instantly revoked.

> If a `subject` parameter is not provided, the methods will automatically use the Active Organization ID if available, otherwise they will use the current User ID.

## Example

The `APIKeys` object is available on the [Clerk](https://clerk.com/docs/chrome-extension/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/chrome-extension/reference/hooks/use-clerk.md) hook to access the `clerk` object, as shown in the following example.

filename: src/routes/page.tsx
```tsx
import { useClerk } from '@clerk/chrome-extension'

export default function Home() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Access the APIKeys object
  const apiKeys = clerk.apiKeys

  return <pre>{JSON.stringify(apiKeys, null, 2)}</pre>
}
```

## Properties

The `APIKeys` methods create, list, and revoke [APIKeyResource](https://clerk.com/docs/chrome-extension/reference/types/api-key-resource.md) objects. The properties below describe `APIKeyResource`.

| Property                                         | Type                                    | Description                                                                                                                                                                                        |
| ------------------------------------------------ | --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="claims"></a> `claims`                     | <code>null | Record<string, any></code> | Custom claims associated with the API key, or `null` if none.                                                                                                                                      |
| <a id="createdat"></a> `createdAt`               | `Date`                                  | The date and time when the API key was created.                                                                                                                                                    |
| <a id="createdby"></a> `createdBy`               | `null | string`              | The ID of the user that created the API key.                                                                                                                                                       |
| <a id="description"></a> `description`           | `null | string`              | A description for the API key.                                                                                                                                                                     |
| <a id="expiration"></a> `expiration`             | `null | Date`                | The expiration date and time for the API key, or `null` if the key never expires.                                                                                                                  |
| <a id="expired"></a> `expired`                   | `boolean`                               | Indicates whether the API key has expired.                                                                                                                                                         |
| <a id="id"></a> `id`                             | `string`                                | A unique identifier for the API key.                                                                                                                                                               |
| <a id="lastusedat"></a> `lastUsedAt`             | `null | Date`                | The date and time when the API key was last used to authenticate a request, or `null` if it has never been used.                                                                                   |
| <a id="name"></a> `name`                         | `string`                                | The name of the API key.                                                                                                                                                                           |
| <a id="revocationreason"></a> `revocationReason` | `null | string`              | The reason the API key was revoked, or `null` if not revoked.                                                                                                                                      |
| <a id="revoked"></a> `revoked`                   | `boolean`                               | Indicates whether the API key has been revoked.                                                                                                                                                    |
| <a id="scopes"></a> `scopes`                     | `string[]`                   | An array of scopes that define what the API key can access.                                                                                                                                        |
| <a id="secret"></a> `secret?`                    | `string`                                | The API key secret. **This property is only present in the response from [create()](https://clerk.com/docs/chrome-extension/reference/objects/api-keys.md#create) and cannot be retrieved later.** |
| <a id="subject"></a> `subject`                   | `string`                                | The user or organization ID that the API key is associated with.                                                                                                                                   |
| <a id="type"></a> `type`                         | `string`                                | The type of the API key.                                                                                                                                                                           |
| <a id="updatedat"></a> `updatedAt`               | `Date`                                  | The date and time when the API key was last updated.                                                                                                                                               |

## Methods

### `create()`

Creates a new API key.

Returns an [APIKeyResource](https://clerk.com/docs/chrome-extension/reference/types/api-key-resource.md) object that includes the `secret` property.

> Make sure to store the API key secret immediately after creation, as it will not be available again.

```typescript
function create(params: CreateAPIKeyParams): Promise<APIKeyResource>
```

#### `CreateAPIKeyParams`

| Property                                                      | Type     | Description                                                                                                                             |
| ------------------------------------------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="description"></a> `description?`                       | `string` | The description of the API key.                                                                                                         |
| <a id="name"></a> `name`                                      | `string` | The name of the API key.                                                                                                                |
| <a id="secondsuntilexpiration"></a> `secondsUntilExpiration?` | `number` | The number of seconds until the API key expires. Set to `null` or omit to create a key that never expires.                              |
| <a id="subject"></a> `subject?`                               | `string` | The user or organization ID to associate the API key with. If not provided, defaults to the Active Organization, then the current User. |

### `getAll()`

Gets a paginated list of API keys for the current user or organization.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/chrome-extension/reference/types/clerk-paginated-response.md) of [APIKeyResource](https://clerk.com/docs/chrome-extension/reference/types/api-key-resource.md) objects.

```typescript
function getAll(params?: GetAPIKeysParams): Promise<ClerkPaginatedResponse<APIKeyResource>>
```

#### `GetAPIKeysParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |
| `query?`                                | `string` | A search query to filter API keys by name.                                                                                                                          |
| `subject?`                              | `string` | The user or organization ID to query API keys by. If not provided, defaults to the Active Organization, then the current User.                                      |

### `reload()`

Reloads the resource, which is useful when you want to access the latest user data after performing a mutation. To make the updated data immediately available, this method forces a session token refresh instead of waiting for the automatic refresh cycle that could temporarily retain stale information. Learn more about [forcing a token refresh](https://clerk.com/docs/guides/sessions/force-token-refresh.md?sdk=chrome-extension).

```typescript
function reload(p?: ClerkResourceReloadParams): Promise<APIKeyResource>
```

#### `ClerkResourceReloadParams`

| Property                                              | Type     | Description                                                                                                                                                                   |
| ----------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="rotatingtokennonce"></a> `rotatingTokenNonce?` | `string` | A nonce to use for rotating the user's token. Used in native application OAuth flows to allow the native client to update its JWT once despite changes in its rotating token. |

### `revoke()`

Revokes a given API key by ID.

Returns an [APIKeyResource](https://clerk.com/docs/chrome-extension/reference/types/api-key-resource.md) object.

```typescript
function revoke(params: RevokeAPIKeyParams): Promise<APIKeyResource>
```

#### `RevokeAPIKeyParams`

| Property                                          | Type     | Description                          |
| ------------------------------------------------- | -------- | ------------------------------------ |
| <a id="apikeyid"></a> `apiKeyID`                  | `string` | The ID of the API key to revoke.     |
| <a id="revocationreason"></a> `revocationReason?` | `string` | The reason for revoking the API key. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
