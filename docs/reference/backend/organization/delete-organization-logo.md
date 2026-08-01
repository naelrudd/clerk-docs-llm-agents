# deleteOrganizationLogo()

Deletes the logo of the given Organization.

Returns the deleted [`Organization`](https://clerk.com/docs/reference/backend/types/backend-organization.md).

```typescript
function deleteOrganizationLogo(organizationId: string): Promise<Organization>
```

## Parameters

| Parameter        | Type     | Description                                        |
| ---------------- | -------- | -------------------------------------------------- |
| `organizationId` | `string` | The ID of the Organization to delete the logo for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'

const response = await clerkClient.organizations.deleteOrganizationLogo(organizationId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/organizations/{organization_id}/logo`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organizations/DELETE/organizations/%7Borganization_id%7D/logo){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
