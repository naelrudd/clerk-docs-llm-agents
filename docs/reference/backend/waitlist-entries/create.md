# create()

Create a waitlist entry for the given email address. If the email address is already on the waitlist, no new entry will be created and the existing waitlist entry will be returned.

Returns the created or existing [`WaitlistEntry`](https://clerk.com/docs/reference/backend/types/backend-waitlist-entry.md) object.

```typescript
function create(params: WaitlistEntryCreateParams): Promise<WaitlistEntry>
```

## `WaitlistEntryCreateParams`

| Property                                 | Type      | Description                                                                                                                                                          |
| ---------------------------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress` | `string`  | The email address to add to the waitlist.                                                                                                                            |
| <a id="notify"></a> `notify?`            | `boolean` | Whether to notify the user that their email address has been added to the waitlist. Notifies the user if the `emailAddress` is an email address. Defaults to `true`. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const params = {
  emailAddress: 'user2@example.com',
  notify: true,
}

const response = await clerkClient.waitlistEntries.create(params)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/waitlist_entries`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/waitlist-entries/POST/waitlist_entries){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
