# delete()

Deletes a satellite domain for the instance. It is currently not possible to delete the instance's primary domain.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md).

```typescript
function delete(satelliteDomainId: string): Promise<DeletedObject>
```

## Parameters

| Parameter           | Type     | Description                               |
| ------------------- | -------- | ----------------------------------------- |
| `satelliteDomainId` | `string` | The ID of the satellite domain to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.domains.delete('domain_123')
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/domains/{domain_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/domains/DELETE/domains/%7Bdomain_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
