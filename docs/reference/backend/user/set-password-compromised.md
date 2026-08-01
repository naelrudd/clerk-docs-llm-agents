# setPasswordCompromised()

Sets the given user's password as compromised. The user will be prompted to reset their password on their next sign-in. See the [guide on password protection and rules](https://clerk.com/docs/guides/secure/password-protection-and-rules.md#reject-compromised-passwords) for more information.

Returns the updated [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md).

```typescript
function setPasswordCompromised(userId: string, params: { revokeAllSessions?: boolean }): Promise<User>
```

## Parameters

| Parameter                   | Type                                          | Description                                                      |
| --------------------------- | --------------------------------------------- | ---------------------------------------------------------------- |
| `userId`                    | `string`                                      | The ID of the user to set the password as compromised for.       |
| `params`                    | `{ revokeAllSessions?: boolean; }` | Other parameters for the request.                                |
| `params.revokeAllSessions?` | `boolean`                                     | Whether to revoke all sessions of the user. Defaults to `false`. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.setPasswordCompromised(userId, {
  revokeAllSessions: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/password/set_compromised`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/password/set_compromised){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
