# updateEmailAddress()

Updates the given email address.

Returns the updated [`EmailAddress`](https://clerk.com/docs/reference/backend/types/backend-email-address.md) object.

```typescript
function updateEmailAddress(emailAddressId: string, params: { primary?: boolean; verified?: boolean }): Promise<EmailAddress>
```

## Parameters

| Parameter          | Type                                                    | Description                                                                                                                                 |
| ------------------ | ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `emailAddressId`   | `string`                                                | The ID of the email address to update.                                                                                                      |
| `params`           | `{ primary?: boolean; verified?: boolean; }` | The parameters to update the email address.                                                                                                 |
| `params.primary?`  | `boolean`                                               | Whether the email address should be the primary email address. Defaults to `false`, unless it is the first email address added to the user. |
| `params.verified?` | `boolean`                                               | Whether the email address should be verified. Defaults to `false`.                                                                          |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const emailAddressId = 'idn_123'

const params = { verified: false }

const response = await clerkClient.emailAddresses.updateEmailAddress(emailAddressId, params)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/email_addresses/{email_address_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/email-addresses/PATCH/email_addresses/%7Bemail_address_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
