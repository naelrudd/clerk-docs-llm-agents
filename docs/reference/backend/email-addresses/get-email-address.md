# getEmailAddress()

Gets the given [`EmailAddress`](https://clerk.com/docs/reference/backend/types/backend-email-address.md).

```typescript
function getEmailAddress(emailAddressId: string): Promise<EmailAddress>
```

## Parameters

| Parameter        | Type     | Description                         |
| ---------------- | -------- | ----------------------------------- |
| `emailAddressId` | `string` | The ID of the email address to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const emailAddressId = 'idn_123'

const response = await clerkClient.emailAddresses.getEmailAddress(emailAddressId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/email_addresses/{email_address_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/email-addresses/GET/email_addresses/%7Bemail_address_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
