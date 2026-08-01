# deleteUserBackupCodes()

Deletes all backup codes for the given user.

```typescript
function deleteUserBackupCodes(userId: string): Promise<UserID>
```

## Parameters

| Parameter | Type     | Description                                    |
| --------- | -------- | ---------------------------------------------- |
| `userId`  | `string` | The ID of the user to delete backup codes for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.deleteUserBackupCodes(userId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/users/{user_id}/backup_code`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/DELETE/users/%7Buser_id%7D/backup_code){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
