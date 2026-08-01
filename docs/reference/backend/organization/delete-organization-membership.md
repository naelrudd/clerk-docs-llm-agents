# deleteOrganizationMembership()

Removes a user from the given Organization.

Returns the deleted [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md).

```typescript
function deleteOrganizationMembership(params: DeleteOrganizationMembershipParams): Promise<OrganizationMembership>
```

## `DeleteOrganizationMembershipParams`

| Property                                     | Type     | Description                                         |
| -------------------------------------------- | -------- | --------------------------------------------------- |
| <a id="organizationid"></a> `organizationId` | `string` | The ID of the Organization to remove the user from. |
| <a id="userid"></a> `userId`                 | `string` | The ID of the user to remove from the Organization. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'
const userId = 'user_123'

const response = await clerkClient.organizations.deleteOrganizationMembership({
  organizationId,
  userId,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/organizations/{organization_id}/memberships/{user_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-memberships/DELETE/organizations/%7Borganization_id%7D/memberships/%7Buser_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
