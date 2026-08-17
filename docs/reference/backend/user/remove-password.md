# removePassword()

Removes the password credential from the given user. This is a privileged operation and does not require the user's current password. Password removal is allowed even when the user has no other sign-in method configured.

By default, existing sessions remain active. Set `signOutOfOtherSessions` to `true` to revoke sessions active when the request is processed.

Returns the updated [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md).

```typescript
function removePassword(userId: string, params: { signOutOfOtherSessions?: boolean }): Promise<User>
```

## Parameters

| Parameter                        | Type                                               | Description                                                                                                             |
| -------------------------------- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `userId`                         | `string`                                           | The ID of the user whose password to remove.                                                                            |
| `params`                         | `{ signOutOfOtherSessions?: boolean; }` | Options for the request.                                                                                                |
| `params.signOutOfOtherSessions?` | `boolean`                                          | When set to `true`, all of the user's active sessions are revoked after their password is removed. Defaults to `false`. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.removePassword(userId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/remove_password`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/remove_password){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
