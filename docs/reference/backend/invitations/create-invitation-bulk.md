# createInvitationBulk()

> This endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests) to **25 requests per hour** per application instance.

Creates multiple invitations for the given email addresses, and sends the invitation emails.

If an email address has already been invited or already exists in your application, trying to create a new invitation will return an error. To bypass this error and create a new invitation anyways, set `ignoreExisting` to `true`.

Returns an array of each created [`Invitation`](https://clerk.com/docs/reference/backend/types/backend-invitation.md) object.

```typescript
function createInvitationBulk(params: CreateBulkParams): Promise<Invitation[]>
```

## `CreateBulkParams`

| Property                                      | Type                                                                                          | Description                                                                                                                                                                                                                                                                                                                               |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress`      | `string`                                                                                      | The email address of the user to invite.                                                                                                                                                                                                                                                                                                  |
| <a id="expiresindays"></a> `expiresInDays?`   | `number`                                                                                      | The number of days until the invitation expires. Defaults to `30`.                                                                                                                                                                                                                                                                        |
| <a id="ignoreexisting"></a> `ignoreExisting?` | `boolean`                                                                                     | Whether an invitation should be created if there is already an existing invitation for this email address, or if the email address already exists in the application. Defaults to `false`.                                                                                                                                                |
| <a id="notify"></a> `notify?`                 | `boolean`                                                                                     | Whether an email invitation should be sent to the given email address. Defaults to `true`.                                                                                                                                                                                                                                                |
| <a id="publicmetadata"></a> `publicMetadata?` | [UserPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#user-public-metadata) | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}. Once the user accepts the invitation and signs up, these metadata will end up in the user's public metadata ([`User.publicMetadata`](https://clerk.com/docs/reference/backend/types/backend-user.md)). |
| <a id="redirecturl"></a> `redirectUrl?`       | `string`                                                                                      | The full URL or path where the user will land after accepting the invitation. See the [custom flow guide for handling application invitations](https://clerk.com/docs/guides/development/custom-flows/authentication/application-invitations.md).                                                                                         |
| <a id="templateslug"></a> `templateSlug?`     | `"invitation" | "waitlist_invitation"`                                             | The template slug to use for the invitation. Defaults to `invitation`.                                                                                                                                                                                                                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
// Each object in the array represents a single invitation
const params = [
  {
    emailAddress: 'invite@example.com',
    redirectUrl: 'https://www.example.com/my-sign-up',
    publicMetadata: {
      example: 'metadata',
      example_nested: {
        nested: 'metadata',
      },
    },
  },
  {
    emailAddress: 'invite2@example.com',
    redirectUrl: 'https://www.example.com/my-sign-up',
    publicMetadata: {
      example: 'metadata',
      example_nested: {
        nested: 'metadata',
      },
    },
  },
]

const response = await clerkClient.invitations.createInvitationBulk(params)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/invitations/bulk`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/invitations/POST/invitations/bulk){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
