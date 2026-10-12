# deleteInvitation()

Permanently deletes the given invitation and the copies of the invitation email Clerk stored for its recipient.

Unlike revoking, deleting removes the invitation record itself, which helps honor a data erasure request from someone who was invited but never signed up. Other records that contain the same email address, such as users or organization invitations, are not affected.

Invitations of any status can be deleted.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md) object.

```typescript
function deleteInvitation(invitationId: string): Promise<DeletedObject>
```

## Parameters

| Parameter      | Type     | Description                         |
| -------------- | -------- | ----------------------------------- |
| `invitationId` | `string` | The ID of the invitation to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-userid-and-other-properties).

```tsx
const invitationId = 'inv_123'

const response = await clerkClient.invitations.deleteInvitation(invitationId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/invitations/{invitation_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/invitations/DELETE/invitations/%7Binvitation_id%7D) for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
