# createRedirectUrl()

Creates a new redirect URL for the instance.

Returns the created [`RedirectUrl`](https://clerk.com/docs/reference/backend/types/backend-redirect-url.md) object.

```typescript
function createRedirectUrl(params: CreateRedirectUrlParams): Promise<RedirectUrl>
```

## `CreateRedirectUrlParams`

| Property               | Type     | Description                                                                                                                                    |
| ---------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="url"></a> `url` | `string` | The full URL value prefixed with `https://` or a custom scheme. For example, `https://my-app.com/oauth-callback` or `my-app://oauth-callback`. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.redirectUrls.createRedirectUrl({
  url: 'https://example.com',
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/redirect_urls`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/redirect-urls/POST/redirect_urls){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
