# deleteDomain() (deprecated)

> This method is deprecated. Use the [`delete()`](https://clerk.com/docs/reference/backend/domains/delete.md) method instead.

Deletes a satellite domain for the instance. It is currently not possible to delete the instance's primary domain. Returns a [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md).

```ts
function deleteDomain(satelliteDomainId: string): Promise<DeletedObject>
```

## Parameters

| Name              | Type   | Description                               |
| ----------------- | ------ | ----------------------------------------- |
| satelliteDomainId | string | The ID of the satellite domain to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.domains.deleteDomain('domain_123')
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
