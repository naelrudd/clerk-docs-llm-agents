# delete()

Deletes the given OAuth application.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md) object.

```typescript
function delete(oauthApplicationId: string): Promise<DeletedObject>
```

## Parameters

| Parameter            | Type     | Description                                |
| -------------------- | -------- | ------------------------------------------ |
| `oauthApplicationId` | `string` | The ID of the OAuth application to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const oauthApplicationId = 'oauthapp_123'

const response = await clerkClient.oauthApplications.delete(oauthApplicationId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/oauth_applications/{oauth_application_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/oauth-applications/DELETE/oauth_applications/%7Boauth_application_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
