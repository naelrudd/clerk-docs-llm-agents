# banUser()

Marks the given [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md) as banned, which means that all their sessions are revoked and they are not allowed to sign in again.

```typescript
function banUser(userId: string): Promise<User>
```

## Parameters

| Parameter | Type     | Description                |
| --------- | -------- | -------------------------- |
| `userId`  | `string` | The ID of the user to ban. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.banUser(userId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/ban`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/ban){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
