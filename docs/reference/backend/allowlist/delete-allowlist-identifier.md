# deleteAllowlistIdentifier()

Deletes an allowlist identifier.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md) object.

```typescript
function deleteAllowlistIdentifier(allowlistIdentifierId: string): Promise<DeletedObject>
```

## Parameters

| Parameter               | Type     | Description                                   |
| ----------------------- | -------- | --------------------------------------------- |
| `allowlistIdentifierId` | `string` | The ID of the allowlist identifier to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const allowlistIdentifierId = 'alid_123'

const response =
  await clerkClient.allowlistIdentifiers.deleteAllowlistIdentifier(allowlistIdentifierId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/allowlist-identifiers/{identifier_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/allow-list--block-list/DELETE/allowlist_identifiers/%7Bidentifier_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
