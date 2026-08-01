# getRedirectUrlList()

Gets a list of whitelisted redirect URLs for the instance. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`RedirectUrl`](https://clerk.com/docs/reference/backend/types/backend-redirect-url.md) objects and a `totalCount` property containing the total number of redirect URLs.

```typescript
function getRedirectUrlList(): Promise<PaginatedResourceResponse<RedirectUrl[]>>
```

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.redirectUrls.getRedirectUrlList()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/redirect_urls/{id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/redirect-urls/GET/redirect_urls){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
