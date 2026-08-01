# rotateSecret()

Rotates the secret of the given OAuth application. When the client secret is rotated, ensure that you update it in your authorized OAuth clients.

Returns the [`OAuthApplication`](https://clerk.com/docs/reference/backend/types/backend-oauth-application.md) object.

```typescript
function rotateSecret(oauthApplicationId: string): Promise<OAuthApplication>
```

## Parameters

| Parameter            | Type     | Description                                              |
| -------------------- | -------- | -------------------------------------------------------- |
| `oauthApplicationId` | `string` | The ID of the OAuth application to rotate the secret of. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const oauthApplicationId = 'oauthapp_123'

const response = await clerkClient.oauthApplications.rotateSecret(oauthApplicationId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/oauth_applications/{oauth_application_id}/rotate_secret`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/oauth-applications/POST/oauth_applications/%7Boauth_application_id%7D/rotate_secret){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
