# getPhoneNumber()

Gets the given [`PhoneNumber`](https://clerk.com/docs/reference/backend/types/backend-phone-number.md).

```typescript
function getPhoneNumber(phoneNumberId: string): Promise<PhoneNumber>
```

## Parameters

| Parameter       | Type     | Description                        |
| --------------- | -------- | ---------------------------------- |
| `phoneNumberId` | `string` | The ID of the phone number to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const phoneNumberId = 'idn_123'

const response = await clerkClient.phoneNumbers.getPhoneNumber(phoneNumberId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/phone_numbers/{phone_number_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/phone-numbers/GET/phone_numbers/%7Bphone_number_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
