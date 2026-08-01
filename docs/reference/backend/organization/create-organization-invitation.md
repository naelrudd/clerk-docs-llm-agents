# createOrganizationInvitation()

> This endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests) to **250 requests per hour** per application instance.

Creates an invitation for a user to join an Organization.

Returns the newly created [`OrganizationInvitation`](https://clerk.com/docs/reference/backend/types/backend-organization-invitation.md) object.

```typescript
function createOrganizationInvitation(params: CreateOrganizationInvitationParams): Promise<OrganizationInvitation>
```

## `CreateOrganizationInvitationParams`

| Property                                        | Type                                                                                                                                 | Description                                                                                                                                                                      |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress`        | `string`                                                                                                                             | The email address of the user being invited.                                                                                                                                     |
| <a id="expiresindays"></a> `expiresInDays?`     | `number`                                                                                                                             | The number of days until the invitation expires. Defaults to `30`.                                                                                                               |
| <a id="inviteruserid"></a> `inviterUserId?`     | `string`                                                                                                                             | The ID of the user creating the invitation.                                                                                                                                      |
| <a id="organizationid"></a> `organizationId`    | `string`                                                                                                                             | The ID of the Organization the user is being invited to.                                                                                                                         |
| <a id="privatemetadata"></a> `privateMetadata?` | [OrganizationInvitationPrivateMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-invitation-private-metadata) | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.                                               |
| <a id="publicmetadata"></a> `publicMetadata?`   | [OrganizationInvitationPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-invitation-public-metadata)   | Metadata that can be read from the Frontend API and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}, but can be set only from the Backend API. |
| <a id="redirecturl"></a> `redirectUrl?`         | `string`                                                                                                                             | The full URL or path where the user will land after accepting the invitation.                                                                                                    |
| <a id="role"></a> `role`                        | [OrganizationCustomRoleKey](https://clerk.com/docs/reference/types/organization-custom-role-key.md)                                  | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) to assign to the user.                                                           |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'
const inviterUserId = 'user_123'
const emailAddress = 'testclerk123@clerk.dev'
const role = 'org:member'

const response = await clerkClient.organizations.createOrganizationInvitation({
  organizationId,
  inviterUserId,
  emailAddress,
  role,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/organizations/{organization_id}/invitations`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/POST/organizations/%7Borganization_id%7D/invitations){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
