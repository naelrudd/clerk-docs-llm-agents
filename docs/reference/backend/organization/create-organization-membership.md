# createOrganizationMembership()

Creates a membership to an Organization for a user directly (circumventing the need for an invitation).

Returns the newly created [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md) object.

```typescript
function createOrganizationMembership(params: CreateOrganizationMembershipParams): Promise<OrganizationMembership>
```

## `CreateOrganizationMembershipParams`

| Property                                     | Type                                                                                                | Description                                                                                                            |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| <a id="organizationid"></a> `organizationId` | `string`                                                                                            | The ID of the Organization the user is being added to.                                                                 |
| <a id="role"></a> `role`                     | [OrganizationCustomRoleKey](https://clerk.com/docs/reference/types/organization-custom-role-key.md) | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) to assign to the user. |
| <a id="userid"></a> `userId`                 | `string`                                                                                            | The ID of the user to be added to the Organization.                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

In the following example, an [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md) is created for a user with the Role `org:member`.

```tsx
const organizationId = 'org_123'
const userId = 'user_123'
const role = 'org:member'

const response = await clerkClient.organizations.createOrganizationMembership({
  organizationId,
  userId,
  role,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/organizations/{organization_id}/memberships`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-memberships/POST/organizations/%7Borganization_id%7D/memberships){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
