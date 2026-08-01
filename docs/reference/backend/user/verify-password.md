# verifyPassword()

Check that the user's password matches the supplied input. Useful for custom auth flows and re-verification.

```typescript
function verifyPassword(params: VerifyPasswordParams): Promise<{ verified: true }>
```

## `VerifyPasswordParams`

| Property                         | Type     | Description                                    |
| -------------------------------- | -------- | ---------------------------------------------- |
| <a id="password"></a> `password` | `string` | The password to verify.                        |
| <a id="userid"></a> `userId`     | `string` | The ID of the user to verify the password for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const password = 'testpassword123'

const response = await clerkClient.users.verifyPassword({
  userId,
  password,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/verify_password`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/verify_password){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
