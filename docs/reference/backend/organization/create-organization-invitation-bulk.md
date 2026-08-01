# createOrganizationInvitationBulk()

> This endpoint is limited to a maximum of 10 invitations per call. If you need to send more invitations, make multiple requests, but keep in mind that this endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests) to **50 requests per hour** per application instance.

Creates multiple invitations for users to join an Organization.

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`OrganizationInvitation`](https://clerk.com/docs/reference/backend/types/backend-organization-invitation.md) objects and a `totalCount` property containing the total number of Organization invitations.

```typescript
function createOrganizationInvitationBulk(organizationId: string, params: Omit<CreateOrganizationInvitationParams, "organizationId">[]): Promise<PaginatedResourceResponse<OrganizationInvitation[]>>
```

## Parameters

| Parameter                 | Type                                                                                                                                                                                                                  | Description                                                                                                                                                                      |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organizationId`          | `string`                                                                                                                                                                                                              | The ID of the Organization to create the invitations for.                                                                                                                        |
| `params`                  | <code>Omit<<a href="https://clerk.com/docs/reference/backend/organization/create-organization-invitation.md#create-organization-invitation-params">CreateOrganizationInvitationParams</a>, "organizationId">[]</code> | The parameters to create the invitations with.                                                                                                                                   |
| `params.emailAddress`     | `string`                                                                                                                                                                                                              | The email address of the user being invited.                                                                                                                                     |
| `params.expiresInDays?`   | `number`                                                                                                                                                                                                              | The number of days until the invitation expires. Defaults to `30`.                                                                                                               |
| `params.inviterUserId?`   | `string`                                                                                                                                                                                                              | The ID of the user creating the invitation.                                                                                                                                      |
| `params.privateMetadata?` | [OrganizationInvitationPrivateMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-invitation-private-metadata)                                                                                  | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.                                               |
| `params.publicMetadata?`  | [OrganizationInvitationPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-invitation-public-metadata)                                                                                    | Metadata that can be read from the Frontend API and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}, but can be set only from the Backend API. |
| `params.redirectUrl?`     | `string`                                                                                                                                                                                                              | The full URL or path where the user will land after accepting the invitation.                                                                                                    |
| `params.role`             | [OrganizationCustomRoleKey](https://clerk.com/docs/reference/types/organization-custom-role-key.md)                                                                                                                   | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) to assign to the user.                                                           |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'
// Each object in the array represents a single invitation
const params = [
  {
    inviterUserId: 'user_1',
    emailAddress: 'testclerk1@clerk.dev',
    role: 'org:admin',
  },
  {
    inviterUserId: 'user_2',
    emailAddress: 'testclerk2@clerk.dev',
    role: 'org:member',
  },
]

const response = await clerkClient.organizations.createOrganizationInvitationBulk(
  organizationId,
  params,
)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/organizations/{organization_id}/invitations/bulk`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/POST/organizations/%7Borganization_id%7D/invitations/bulk){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
