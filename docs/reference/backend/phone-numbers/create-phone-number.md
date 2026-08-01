# createPhoneNumber()

Creates a new phone number for the given user.

Returns the created [`PhoneNumber`](https://clerk.com/docs/reference/backend/types/backend-phone-number.md) object.

```typescript
function createPhoneNumber(params: CreatePhoneNumberParams): Promise<PhoneNumber>
```

## `CreatePhoneNumberParams`

| Property                                                        | Type      | Description                                                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="phonenumber"></a> `phoneNumber`                          | `string`  | The phone number to assign to the specified user. Must be in [E.164 format](https://en.wikipedia.org/wiki/E.164).                                                                                                                                                                                                                                                     |
| <a id="primary"></a> `primary?`                                 | `boolean` | Whether the phone number should be the primary phone number. Defaults to `false`, unless it is the first phone number added to the user.                                                                                                                                                                                                                              |
| <a id="reservedforsecondfactor"></a> `reservedForSecondFactor?` | `boolean` | Whether the phone number should be reserved for [multi-factor authentication](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md#multi-factor-authentication). The phone number must also be verified. If there are no other reserved second factors, the phone number will be set as the default second factor. Defaults to `false`. |
| <a id="userid"></a> `userId`                                    | `string`  | The ID of the user to create the phone number for.                                                                                                                                                                                                                                                                                                                    |
| <a id="verified"></a> `verified?`                               | `boolean` | Whether the phone number should be verified. Defaults to `false`.                                                                                                                                                                                                                                                                                                     |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.phoneNumbers.createPhoneNumber({
  userId: 'user_123',
  phoneNumber: '15551234567',
  primary: true,
  verified: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/phone_numbers`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/phone-numbers/POST/phone_numbers){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
