# deleteUserPasskey()

Deletes the passkey identification for a given user and notifies them through email.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md) object.

```typescript
function deleteUserPasskey(params: DeleteUserPasskeyParams): Promise<DeletedObject>
```

## `DeleteUserPasskeyParams`

| Property                                                       | Type     | Description                                     |
| -------------------------------------------------------------- | -------- | ----------------------------------------------- |
| <a id="passkeyidentificationid"></a> `passkeyIdentificationId` | `string` | The ID of the passkey identification to delete. |
| <a id="userid"></a> `userId`                                   | `string` | The ID of the user to delete the passkey for.   |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'
const passkeyIdentificationId = 'passkey_identification_123'

const response = await clerkClient.users.deleteUserPasskey({
  userId,
  passkeyIdentificationId,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/users/{user_id}/passkeys/{passkey_identification_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/DELETE/users/%7Buser_id%7D/passkeys/%7Bpasskey_identification_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
