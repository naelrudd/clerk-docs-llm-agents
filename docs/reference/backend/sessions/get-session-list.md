# getSessionList()

Gets a list of sessions for either the specified client or user. Requires either `clientId` or `userId` to be provided. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`Session`](https://clerk.com/docs/reference/backend/types/backend-session.md) objects and a `totalCount` property containing the total number of sessions.

```typescript
function getSessionList(params: SessionListParams): Promise<PaginatedResourceResponse<Session[]>>
```

## `SessionListParams`

| Property                      | Type                                                                      | Description                                                                                                                                                                            |
| ----------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `clientId?`                   | `string`                                                                  | The ID of the client to get sessions for.                                                                                                                                              |
| <a id="limit"></a> `limit?`   | `number`                                                                  | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?` | `number`                                                                  | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `status?`                     | [SessionStatus](https://clerk.com/docs/reference/types/session-status.md) | The status of the sessions to get.                                                                                                                                                     |
| `userId?`                     | `string`                                                                  | The ID of the user to get sessions for.                                                                                                                                                |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

Get a list of sessions for a specific `userId`:

```tsx
const userId = 'user_123'

const response = await clerkClient.sessions.getSessionList({ userId })
```

### Filter by session status

In this example, a list of sessions with a `status` of `'expired'` is retrieved. You can see that the returned [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) includes `data`, which is an array of [`Session`](https://clerk.com/docs/reference/backend/types/backend-session.md) objects, and `totalCount`, which indicates the total number of sessions for the specified user.

```tsx
const userId = 'user_123'

const status = 'expired'

const response = await clerkClient.sessions.getSessionList({ userId, status })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/sessions`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/sessions/GET/sessions){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
