# getOrganizationDomainList()

Gets the list of [Verified Domains](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md) for the given Organization. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`OrganizationDomain`](https://clerk.com/docs/reference/backend/types/backend-organization-domain.md) objects and a `totalCount` property containing the total number of Verified Domains for the Organization.

```typescript
function getOrganizationDomainList(params: GetOrganizationDomainListParams): Promise<PaginatedResourceResponse<OrganizationDomain[]>>
```

## `GetOrganizationDomainListParams`

| Property                                     | Type     | Description                                                                                                                                                                            |
| -------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="limit"></a> `limit?`                  | `number` | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?`                | `number` | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| <a id="organizationid"></a> `organizationId` | `string` | The ID of the Organization to get the list of domains for.                                                                                                                             |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'

const response = await clerkClient.organizations.getOrganizationDomainList({ organizationId })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/organizations/{organization_id}/domains`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-domains/GET/organizations/%7Borganization_id%7D/domains){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
