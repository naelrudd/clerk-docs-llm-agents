# getInstanceOrganizationMembershipList()

Gets the list of Organization memberships for the instance. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md) objects and a `totalCount` property containing the total number of Organization memberships for the instance.

> To get the list of Organization memberships **for a specific Organization**, use [`getOrganizationMembershipList()`](https://clerk.com/docs/reference/backend/organization/get-organization-membership-list.md).

```typescript
function getInstanceOrganizationMembershipList(params: GetInstanceOrganizationMembershipListParams): Promise<PaginatedResourceResponse<OrganizationMembership[]>>
```

## `GetInstanceOrganizationMembershipListParams`

| Property                      | Type                                                                                                                | Description                                                                                                                                                                            |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="limit"></a> `limit?`   | `number`                                                                                                            | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?` | `number`                                                                                                            | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `orderBy?`                    | `WithSign`<`"phone_number" | "email_address" | "created_at" | "first_name" | "last_name" | "username"`> | Filters Organization memberships in a particular order. Prefix a value with `+` to sort in ascending order, or `-` to sort in descending order. Defaults to `-created_at`.             |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.organizations.getInstanceOrganizationMembershipList()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/organization_memberships`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-memberships/GET/organization_memberships){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
