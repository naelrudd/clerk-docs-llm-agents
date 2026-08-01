# getOrganizationMembershipList()

Gets a list of the given user's Organization memberships. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property that contains an array of [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md) objects, and a `totalCount` property that indicates the total number of Organization memberships for the user.

```typescript
function getOrganizationMembershipList(params: GetOrganizationMembershipListParams): Promise<PaginatedResourceResponse<OrganizationMembership[]>>
```

## `GetOrganizationMembershipListParams`

| Property                      | Type     | Description                                                                                                                                                                            |
| ----------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="limit"></a> `limit?`   | `number` | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?` | `number` | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `userId`                      | `string` | The ID of the user to get the list of Organization memberships for.                                                                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Basic

```tsx
const userId = 'user_123'

const response = await clerkClient.users.getOrganizationMembershipList({ userId })
```

### Limit the number of results

Gets a list of a user's Organization memberships, limited to the specified number of results.

```tsx
const userId = 'user_123'

const { data, totalCount } = await clerkClient.users.getOrganizationMembershipList({
  userId,
  // returns the first 10 memberships
  limit: 10,
})
```

### Skip results

Gets a list of a user's Organization memberships, skipping the specified number of results.

```tsx
const userId = 'user_123'

const { data, totalCount } = await clerkClient.users.getOrganizationMembershipList({
  userId,
  // skips the first 10 memberships
  offset: 10,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/users/{user_id}/organization_memberships`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/GET/users/%7Buser_id%7D/organization_memberships){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
