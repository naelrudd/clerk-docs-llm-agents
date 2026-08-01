# updateOrganizationLogo()

Updates the logo of the given Organization.

Returns the updated [`Organization`](https://clerk.com/docs/reference/backend/types/backend-organization.md).

```typescript
function updateOrganizationLogo(organizationId: string, params: { file: Blob | File; uploaderUserId?: string }): Promise<Organization>
```

## Parameters

| Parameter                | Type                                                         | Description                                        |
| ------------------------ | ------------------------------------------------------------ | -------------------------------------------------- |
| `organizationId`         | `string`                                                     | The ID of the Organization to update the logo for. |
| `params`                 | `{ file: Blob | File; uploaderUserId?: string; }` | The parameters to update the logo with.            |
| `params.file`            | `Blob | File`                                     | The file to upload as the logo.                    |
| `params.uploaderUserId?` | `string`                                                     | The ID of the user uploading the logo.             |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

> Using `clerkClient` methods can contribute towards rate limiting. To set an Organization's logo, it's recommended to use the frontend [organization.setLogo()](https://clerk.com/docs/reference/objects/organization.md#set-logo) method instead.

```tsx
const organizationId = 'org_123'
const uploaderUserId = 'user_123'

const fileBits = ['logo-pic-content']
const fileName = 'logo.png'
const file = new File(fileBits, fileName, { type: 'image/png' })

const params = {
  file,
  uploaderUserId,
}

const response = await clerkClient.organizations.updateOrganizationLogo(organizationId, params)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PUT/organizations/{organization_id}/logo`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organizations/PUT/organizations/%7Borganization_id%7D/logo){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
