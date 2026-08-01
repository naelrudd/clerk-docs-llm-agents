# getUser()

Gets a [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md) for the specified user ID.

```typescript
function getUser(userId: string): Promise<User>
```

## Parameters

| Parameter | Type     | Description                     |
| --------- | -------- | ------------------------------- |
| `userId`  | `string` | The ID of the user to retrieve. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.getUser(userId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/users/{user_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/GET/users/%7Buser_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
