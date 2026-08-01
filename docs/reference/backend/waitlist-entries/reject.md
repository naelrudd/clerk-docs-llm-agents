# reject()

Rejects the given waitlist entry.

Returns the rejected [`WaitlistEntry`](https://clerk.com/docs/reference/backend/types/backend-waitlist-entry.md) object.

```typescript
function reject(id: string): Promise<WaitlistEntry>
```

## Parameters

| Parameter | Type     | Description                             |
| --------- | -------- | --------------------------------------- |
| `id`      | `string` | The ID of the waitlist entry to reject. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const waitlistId = 'waitlist_123'

const response = await clerkClient.waitlistEntries.reject(waitlistId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/waitlist_entries/{waitlist_entry_id}/reject`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/waitlist-entries/POST/waitlist_entries/%7Bwaitlist_entry_id%7D/reject){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
