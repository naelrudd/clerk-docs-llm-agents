# updateOrganizationMembership()

Updates a user's [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md).

Returns the updated [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md) object.

```typescript
function updateOrganizationMembership(params: CreateOrganizationMembershipParams): Promise<OrganizationMembership>
```

## `CreateOrganizationMembershipParams`

| Property                                     | Type                                                                                                | Description                                                                                                            |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| <a id="organizationid"></a> `organizationId` | `string`                                                                                            | The ID of the Organization the user is being added to.                                                                 |
| <a id="role"></a> `role`                     | [OrganizationCustomRoleKey](https://clerk.com/docs/reference/types/organization-custom-role-key.md) | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) to assign to the user. |
| <a id="userid"></a> `userId`                 | `string`                                                                                            | The ID of the user to be added to the Organization.                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'
const userId = 'user_123'
const role = 'org:admin'

const response = await clerkClient.organizations.updateOrganizationMembership({
  organizationId,
  userId,
  role,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/organizations/{organization_id}/memberships/{user_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-memberships/PATCH/organizations/%7Borganization_id%7D/memberships/%7Buser_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
