# unlockUser()

Removes a sign-in lock from the given [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md), allowing them to sign in again. See the [guide on user locks](https://clerk.com/docs/guides/secure/user-lockout.md).

```typescript
function unlockUser(userId: string): Promise<User>
```

## Parameters

| Parameter | Type     | Description                   |
| --------- | -------- | ----------------------------- |
| `userId`  | `string` | The ID of the user to unlock. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.unlockUser(userId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/unlock`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/unlock){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
