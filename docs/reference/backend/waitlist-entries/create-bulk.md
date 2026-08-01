# createBulk()

> This endpoint is limited to a maximum of 50 waitlist entries per call. If you need to create more waitlist entries, make multiple requests, but keep in mind that this endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests).

Creates multiple waitlist entries for the given email addresses. If an email address is already on the waitlist, no new entry will be created and the existing waitlist entry will be returned.

Returns an array of created or existing [`WaitlistEntry`](https://clerk.com/docs/reference/backend/types/backend-waitlist-entry.md) objects.

```typescript
function createBulk(params: WaitlistEntryBulkCreateParams): Promise<WaitlistEntry[]>
```

## `WaitlistEntryBulkCreateParams`

| Property                                 | Type      | Description                                                                                                                                                          |
| ---------------------------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress` | `string`  | The email address to add to the waitlist.                                                                                                                            |
| <a id="notify"></a> `notify?`            | `boolean` | Whether to notify the user that their email address has been added to the waitlist. Notifies the user if the `emailAddress` is an email address. Defaults to `true`. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
// Each object in the array represents a single waitlist entry
const params = [
  {
    emailAddress: 'user1@example.com',
  },
  {
    emailAddress: 'user2@example.com',
    notify: true,
  },
]

const response = await clerkClient.waitlistEntries.createBulk(params)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/waitlist_entries/bulk`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/waitlist-entries/POST/waitlist_entries/bulk){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
