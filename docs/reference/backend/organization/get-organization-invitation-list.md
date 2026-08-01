# getOrganizationInvitationList()

Gets the list of Organization invitations for the specified Organization.

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`OrganizationInvitation`](https://clerk.com/docs/reference/backend/types/backend-organization-invitation.md) objects and a `totalCount` property containing the total number of Organization invitations for the Organization.

```typescript
function getOrganizationInvitationList(params: GetOrganizationInvitationListParams): Promise<PaginatedResourceResponse<OrganizationInvitation[]>>
```

## `GetOrganizationInvitationListParams`

| Property                      | Type                                                            | Description                                                                                                                                                                            |
| ----------------------------- | --------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="limit"></a> `limit?`   | `number`                                                        | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?` | `number`                                                        | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `organizationId`              | `string`                                                        | The ID of the Organization to get the list of invitations for.                                                                                                                         |
| `status?`                     | `("pending" | "accepted" | "revoked" | "expired")[]` | Filters Organization invitations by status. Accepts up to 100 statuses.                                                                                                                |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Basic

```tsx
const organizationId = 'org_123'

const response = await clerkClient.organizations.getOrganizationInvitationList({ organizationId })
```

### Filter by invitation status

Gets a list of Organization invitations filtered by invitation status.

```tsx
const organizationId = 'org_123'

const { data, totalCount } = await clerkClient.organizations.getOrganizationInvitationList({
  organizationId,
  // returns a list of invitations that have not yet been accepted
  status: ['pending'],
})
```

### Limit the number of results

Gets a list of Organization invitations, limited to the specified number of results.

```tsx
const organizationId = 'org_123'

const { data, totalCount } = await clerkClient.organizations.getOrganizationInvitationList({
  organizationId,
  // returns the first 10 results
  limit: 10,
})
```

### Skip results

Gets a list of Organization invitations, skipping the specified number of results.

```tsx
const organizationId = 'org_123'

const { data, totalCount } = await clerkClient.organizations.getOrganizationInvitationList({
  organizationId,
  // skips the first 10 results
  offset: 10,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/organizations/{organization_id}/invitations`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/GET/organizations/%7Borganization_id%7D/invitations){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
