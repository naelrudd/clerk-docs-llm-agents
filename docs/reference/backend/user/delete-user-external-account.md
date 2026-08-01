# deleteUserExternalAccount()

Deletes an external account for the given user.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md) object.

```typescript
function deleteUserExternalAccount(params: DeleteUserExternalAccountParams): Promise<DeletedObject>
```

## `DeleteUserExternalAccountParams`

| Property                                           | Type     | Description                                            |
| -------------------------------------------------- | -------- | ------------------------------------------------------ |
| <a id="externalaccountid"></a> `externalAccountId` | `string` | The ID of the external account to delete.              |
| <a id="userid"></a> `userId`                       | `string` | The ID of the user to delete the external account for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'
const externalAccountId = 'external_account_123'

const response = await clerkClient.users.deleteUserExternalAccount({
  userId,
  externalAccountId,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/users/{user_id}/external_accounts/{external_account_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/DELETE/users/%7Buser_id%7D/external_accounts/%7Bexternal_account_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
