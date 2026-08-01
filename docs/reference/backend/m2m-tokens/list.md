# list()

> JWT tokens are not stored by Clerk, so they cannot be fetched via the **list** endpoint (`clerkClient.m2m.list()`). The list endpoint will only return opaque tokens. Additionally, since JWT verification happens client-side, Clerk cannot track `last_used_at` for JWT tokens.

Gets a list of M2M tokens for the given machine. By default, the list is returned in descending order by creation date (newest first). This endpoint can be authenticated by either a [Machine](https://clerk.com/docs/reference/backend/types/backend-machine.md) Secret Key or by a Clerk Secret Key.

- When fetching M2M tokens with a [Machine](https://clerk.com/docs/reference/backend/types/backend-machine.md) Secret Key, only tokens associated with the authenticated machine can be retrieved.
- When fetching M2M tokens with a Clerk Secret Key, tokens for any machine in the instance can be retrieved.

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`M2MToken`](https://clerk.com/docs/reference/backend/types/backend-m2m-token.md) objects and a `totalCount` property containing the total number of M2M tokens for the machine.

```typescript
function list(queryParams: GetM2MTokenListParams): Promise<PaginatedResourceResponse<M2MToken[]>>
```

## `GetM2MTokenListParams`

| Property                      | Type      | Description                                                                                                                                                                            |
| ----------------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `expired?`                    | `boolean` | Whether to include expired M2M tokens. Defaults to `false`.                                                                                                                            |
| <a id="limit"></a> `limit?`   | `number`  | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| `machineSecretKey?`           | `string`  | The custom machine secret key for authentication. If not provided, the SDK will use the value from the environment variables.                                                          |
| <a id="offset"></a> `offset?` | `number`  | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `revoked?`                    | `boolean` | Whether to include revoked M2M tokens. Defaults to `false`.                                                                                                                            |
| `subject`                     | `string`  | The machine ID to query M2M tokens by.                                                                                                                                                 |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Filter by machine ID

Gets a list of M2M tokens for a machine

```tsx
const machineId = 'mt_123'

const m2mTokens = await clerkClient.m2m.list({
  subject: machineId,
})
```

### Filter by machine ID, including revoked and expired tokens

Gets a list of M2M tokens for a machine, including revoked and expired ones

```tsx
const machineId = 'mt_123'

const m2mTokens = await clerkClient.m2m.list({
  subject: machineId,
  revoked: true,
  expired: true,
})
```

### Filer by machine ID, including revoked and expired tokens, with pagination

Gets a list of M2M tokens for a machine with pagination

```tsx
const machineId = 'mt_123'

const m2mTokens = await clerkClient.m2m.list({
  subject: machineId,
  limit: 20,
  offset: 0,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/m2m_tokens`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/m2m-tokens/GET/m2m_tokens){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
