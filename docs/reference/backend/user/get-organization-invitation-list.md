# getOrganizationInvitationList()

Gets a list of the given user's Organization invitations. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property that contains an array of [`OrganizationInvitation`](https://clerk.com/docs/reference/backend/types/backend-organization-invitation.md) objects, and a `totalCount` property that indicates the total number of Organization invitations for the user.

```typescript
function getOrganizationInvitationList(params: GetOrganizationInvitationListParams): Promise<PaginatedResourceResponse<OrganizationInvitation[]>>
```

## `GetOrganizationInvitationListParams`

| Property                      | Type                                                        | Description                                                                                                                                                                            |
| ----------------------------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="limit"></a> `limit?`   | `number`                                                    | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?` | `number`                                                    | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `status?`                     | `"pending" | "accepted" | "revoked" | "expired"` | Filters the invitations by the provided status.                                                                                                                                        |
| `userId`                      | `string`                                                    | The ID of the user to get the list of Organization invitations for.                                                                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Basic

```tsx
const userId = 'user_123'

const response = await clerkClient.users.getOrganizationInvitationList({ userId })
```

### Filter by invitation status

Gets a list of a user's Organization invitations filtered by invitation status.

```tsx
const userId = 'user_123'

const { data, totalCount } = await clerkClient.users.getOrganizationInvitationList({
  userId,
  // returns a list of invitations that have not yet been accepted
  status: ['pending'],
})
```

### Limit the number of results

Gets a list of a user's Organization invitations, limited to the specified number of results.

```tsx
const userId = 'user_123'

const { data, totalCount } = await clerkClient.users.getOrganizationInvitationList({
  userId,
  // returns the first 10 invitations
  limit: 10,
})
```

### Skip results

Gets a list of a user's Organization invitations, skipping the specified number of results.

```tsx
const userId = 'user_123'

const { data, totalCount } = await clerkClient.users.getOrganizationInvitationList({
  userId,
  // skips the first 10 invitations
  offset: 10,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/users/{user_id}/organization_invitations`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/GET/users/%7Buser_id%7D/organization_invitations){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
