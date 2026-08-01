# deleteUser()

Deletes the given [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md).

```typescript
function deleteUser(userId: string): Promise<User>
```

## Parameters

| Parameter | Type     | Description                   |
| --------- | -------- | ----------------------------- |
| `userId`  | `string` | The ID of the user to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.deleteUser(userId)
```

## Example

filename: app/api/example/route.ts
```ts
import { auth, clerkClient } from '@clerk/nextjs/server'
import { NextResponse } from 'next/server'

export async function POST() {
  const { isAuthenticated, userId } = await auth()

  // Protect the route by checking if the user is signed in
  if (!isAuthenticated) {
    return new NextResponse('Unauthorized', { status: 401 })
  }

  // Initialize clerkClient
  const client = await clerkClient()

  // Use the `deleteUser()` method to delete the user
  await client.users.deleteUser(userId)

  // Return the success status
  return NextResponse.json({ success: true })
}
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/users/{user_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/DELETE/users/%7Buser_id%7D){{ target: '_blank' }} for more information.

Here's an example of making a request directly to the endpoint using cURL.

Replace `YOUR_SECRET_KEY` with your Clerk Secret Key.

filename: terminal
```bash
  curl 'https://api.clerk.com/v1/users/{user_id}' -X DELETE -H 'Authorization:Bearer {{secret}}' -H 'Content-Type:application/json'
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
