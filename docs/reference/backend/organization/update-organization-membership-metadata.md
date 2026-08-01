# updateOrganizationMembershipMetadata()

Updates the metadata for the given Organization membership, by merging existing values with the provided parameters.

A "deep" merge will be performed - "deep" means that any nested JSON objects will be merged as well. You can remove metadata keys at any level by setting their value to `null`.

Returns the updated [`OrganizationMembership`](https://clerk.com/docs/reference/backend/types/backend-organization-membership.md).

```typescript
function updateOrganizationMembershipMetadata(params: UpdateOrganizationMembershipMetadataParams): Promise<OrganizationMembership>
```

## `UpdateOrganizationMembershipMetadataParams`

| Property           | Type                                                                                                            | Description                                                                                                                                                                      |
| ------------------ | --------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organizationId`   | `string`                                                                                                        | The ID of the Organization the membership belongs to.                                                                                                                            |
| `privateMetadata?` | [OrganizationPrivateMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-private-metadata) | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.                                               |
| `publicMetadata?`  | [OrganizationPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-public-metadata)   | Metadata that can be read from the Frontend API and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}, but can be set only from the Backend API. |
| `userId`           | `string`                                                                                                        | The ID of the user the membership belongs to.                                                                                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'
const userId = 'user_123'

const response = await clerkClient.organizations.updateOrganizationMembershipMetadata({
  organizationId,
  userId,
  publicMetadata: {
    example: 'this value is updated!',
  },
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/organizations/{organization_id}/memberships/{user_id}/metadata`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-memberships/PATCH/organizations/%7Borganization_id%7D/memberships/%7Buser_id%7D/metadata){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
