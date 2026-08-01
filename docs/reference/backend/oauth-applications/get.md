# get()

Gets the given OAuth application.

Returns the [`OAuthApplication`](https://clerk.com/docs/reference/backend/types/backend-oauth-application.md) object.

```typescript
function get(oauthApplicationId: string): Promise<OAuthApplication>
```

## Parameters

| Parameter            | Type     | Description                             |
| -------------------- | -------- | --------------------------------------- |
| `oauthApplicationId` | `string` | The ID of the OAuth application to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const oauthApplicationId = 'oauthapp_123'

const response = await clerkClient.oauthApplications.get(oauthApplicationId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/oauth_applications/{oauth_application_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/oauth-applications/GET/oauth_applications/%7Boauth_application_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
