# createOrganization()

Creates an [`Organization`](https://clerk.com/docs/reference/backend/types/backend-organization.md).

```typescript
function createOrganization(params: CreateParams): Promise<Organization>
```

## `CreateParams`

| Property                 | Type                                                                                                            | Description                                                                                                                                                                                            |
| ------------------------ | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `createdBy?`             | `string`                                                                                                        | The ID of the user creating the Organization. The user will become an [admin](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md#default-roles) for the Organization. |
| `maxAllowedMemberships?` | `number`                                                                                                        | The maximum number of memberships allowed in the Organization. `0` means unlimited.                                                                                                                    |
| `name`                   | `string`                                                                                                        | The name of the Organization.                                                                                                                                                                          |
| `privateMetadata?`       | [OrganizationPrivateMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-private-metadata) | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.                                                                     |
| `publicMetadata?`        | [OrganizationPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-public-metadata)   | Metadata that can be read from the Frontend API and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}, but can be set only from the Backend API.                       |
| `slug?`                  | `string`                                                                                                        | The slug of the Organization.                                                                                                                                                                          |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const name = 'test-org'
const createdBy = 'user_123'
const response = await clerkClient.organizations.createOrganization({ name, createdBy })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/organizations`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organizations/POST/organizations){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
