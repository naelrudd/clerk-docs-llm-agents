# invite()

Invites the given waitlist entry.

Returns the invited [`WaitlistEntry`](https://clerk.com/docs/reference/backend/types/backend-waitlist-entry.md) object.

```typescript
function invite(id: string, params: { ignoreExisting?: boolean }): Promise<WaitlistEntry>
```

## Parameters

| Parameter                | Type                                       | Description                                                    |
| ------------------------ | ------------------------------------------ | -------------------------------------------------------------- |
| `id`                     | `string`                                   | The waitlist entry ID.                                         |
| `params`                 | `{ ignoreExisting?: boolean; }` | Optional parameters for inviting the waitlist entry.           |
| `params.ignoreExisting?` | `boolean`                                  | Whether to ignore an existing invitation. Defaults to `false`. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const waitlistId = 'waitlist_123'

const response = await clerkClient.waitlistEntries.invite(waitlistId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/waitlist_entries/{waitlist_entry_id}/invite`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/waitlist-entries/POST/waitlist_entries/%7Bwaitlist_entry_id%7D/invite){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
