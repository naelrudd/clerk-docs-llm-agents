# verifyTOTP()

Verify that the provided TOTP or backup code is valid for the user. Verifying a backup code will result it in being consumed (i.e., it will become invalid). Useful for custom auth flows and re-verification.

```typescript
function verifyTOTP(params: VerifyTOTPParams): Promise<{ code_type: "totp"; verified: true }>
```

## `VerifyTOTPParams`

| Property                     | Type     | Description                                |
| ---------------------------- | -------- | ------------------------------------------ |
| <a id="code"></a> `code`     | `string` | The TOTP or backup code to verify.         |
| <a id="userid"></a> `userId` | `string` | The ID of the user to verify the TOTP for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const code = '123456'

const response = await clerkClient.users.verifyTOTP({
  userId,
  code,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/verify_totp`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/verify_totp){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
