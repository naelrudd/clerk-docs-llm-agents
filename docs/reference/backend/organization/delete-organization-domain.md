# deleteOrganizationDomain()

Deletes a [Verified Domain](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md) for the given Organization.

Returns the deleted [`OrganizationDomain`](https://clerk.com/docs/reference/backend/types/backend-organization-domain.md) object.

```typescript
function deleteOrganizationDomain(params: DeleteOrganizationDomainParams): Promise<OrganizationDomain>
```

## `DeleteOrganizationDomainParams`

| Property                                     | Type     | Description                                          |
| -------------------------------------------- | -------- | ---------------------------------------------------- |
| <a id="domainid"></a> `domainId`             | `string` | The ID of the domain to delete.                      |
| <a id="organizationid"></a> `organizationId` | `string` | The ID of the Organization to delete the domain for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'
const domainId = 'domain_123'

const response = await clerkClient.organizations.deleteOrganizationDomain({
  organizationId,
  domainId,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/organizations/{organization_id}/domains/{domain_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-domains/DELETE/organizations/%7Borganization_id%7D/domains/%7Bdomain_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
