# getOrganizationInvitation()

Gets an [`OrganizationInvitation`](https://clerk.com/docs/reference/backend/types/backend-organization-invitation.md).

```typescript
function getOrganizationInvitation(params: GetOrganizationInvitationParams): Promise<OrganizationInvitation>
```

## `GetOrganizationInvitationParams`

| Property                                     | Type     | Description                                           |
| -------------------------------------------- | -------- | ----------------------------------------------------- |
| <a id="invitationid"></a> `invitationId`     | `string` | The ID of the Organization invitation to get.         |
| <a id="organizationid"></a> `organizationId` | `string` | The ID of the Organization to get the invitation for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'

const invitationId = 'orginv_123'

const response = await clerkClient.organizations.getOrganizationInvitation({
  organizationId,
  invitationId,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/organizations/{organization_id}/invitations/{invitation_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/GET/organizations/%7Borganization_id%7D/invitations/%7Binvitation_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
