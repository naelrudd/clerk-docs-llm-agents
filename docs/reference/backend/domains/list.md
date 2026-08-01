# list()

Gets the list of domains for the instance. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`Domain`](https://clerk.com/docs/reference/backend/types/domain.md) objects and a `totalCount` property containing the total number of domains for the instance.

```typescript
function list(): Promise<PaginatedResourceResponse<Domain[]>>
```

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.domains.list()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/domains`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/domains/GET/domains){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
