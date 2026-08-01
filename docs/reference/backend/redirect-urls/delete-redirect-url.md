# deleteRedirectUrl()

Deletes the given redirect URL.

Returns the deleted [`RedirectUrl`](https://clerk.com/docs/reference/backend/types/backend-redirect-url.md) object.

```typescript
function deleteRedirectUrl(redirectUrlId: string): Promise<RedirectUrl>
```

## Parameters

| Parameter       | Type     | Description                           |
| --------------- | -------- | ------------------------------------- |
| `redirectUrlId` | `string` | The ID of the redirect URL to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const redirectUrlId = 'ru_123'

const response = await clerkClient.redirectUrls.deleteRedirectUrl(redirectUrlId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/redirect_urls/{id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/redirect-urls/DELETE/redirect_urls/%7Bid%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
