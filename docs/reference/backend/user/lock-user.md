# lockUser()

Locks the given [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md), which means that they are not allowed to sign in again until the lock expires or is manually unlocked. By default, lockout duration is 1 hour, but it can be configured in the application's [**Attack protection**](https://dashboard.clerk.com/~/protect/attack-protection) settings. See the [guide on user locks](https://clerk.com/docs/guides/secure/user-lockout.md).

```typescript
function lockUser(userId: string): Promise<User>
```

## Parameters

| Parameter | Type     | Description                 |
| --------- | -------- | --------------------------- |
| `userId`  | `string` | The ID of the user to lock. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.lockUser(userId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/lock`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/lock){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
