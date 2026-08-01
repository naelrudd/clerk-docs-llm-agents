# createEmailAddress()

Creates a new email address for the given user.

Returns the created [`EmailAddress`](https://clerk.com/docs/reference/backend/types/backend-email-address.md) object.

```typescript
function createEmailAddress(params: CreateEmailAddressParams): Promise<EmailAddress>
```

## `CreateEmailAddressParams`

| Property                                 | Type      | Description                                                                                                                                 |
| ---------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress` | `string`  | The email address to create.                                                                                                                |
| <a id="primary"></a> `primary?`          | `boolean` | Whether the email address should be the primary email address. Defaults to `false`, unless it is the first email address added to the user. |
| <a id="userid"></a> `userId`             | `string`  | The ID of the user to create the email address for.                                                                                         |
| <a id="verified"></a> `verified?`        | `boolean` | Whether the email address should be verified. Defaults to `false`.                                                                          |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.emailAddresses.createEmailAddress({
  userId: 'user_123',
  emailAddress: 'testclerk123@gmail.com',
  primary: true,
  verified: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/email_addresses`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/email-addresses/POST/email_addresses){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
