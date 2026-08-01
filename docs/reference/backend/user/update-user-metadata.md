# updateUserMetadata()

Updates the metadata for the given user, by merging existing values with the provided parameters.

A "deep" merge will be performed - "deep" means that any nested JSON objects will be merged as well. You can remove metadata keys at any level by setting their value to `null`.

> If you want to fully replace the existing metadata instead of merging, use [`replaceUserMetadata()`](https://clerk.com/docs/reference/backend/user/replace-user-metadata.md).

Returns the updated [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md).

```typescript
function updateUserMetadata(userId: string, params: { privateMetadata?: UserPrivateMetadata; publicMetadata?: UserPublicMetadata; unsafeMetadata?: UserUnsafeMetadata }): Promise<User>
```

## Parameters

| Parameter                 | Type                                                                                                                                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                     |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `userId`                  | `string`                                                                                                                                                                                                                                                                                                                                                                                             | The ID of the user to update.                                                                                                                                                   |
| `params`                  | <code>{ privateMetadata?: <a href="https://clerk.com/docs/reference/types/metadata.md#user-private-metadata">UserPrivateMetadata</a>; publicMetadata?: <a href="https://clerk.com/docs/reference/types/metadata.md#user-public-metadata">UserPublicMetadata</a>; unsafeMetadata?: <a href="https://clerk.com/docs/reference/types/metadata.md#user-unsafe-metadata">UserUnsafeMetadata</a>; }</code> | The metadata to update.                                                                                                                                                         |
| `params.privateMetadata?` | [UserPrivateMetadata](https://clerk.com/docs/reference/types/metadata.md#user-private-metadata)                                                                                                                                                                                                                                                                                                      | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.                                              |
| `params.publicMetadata?`  | [UserPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#user-public-metadata)                                                                                                                                                                                                                                                                                                        | Metadata that can be read from the Frontend API and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }} and can be set only from the Backend API. |
| `params.unsafeMetadata?`  | [UserUnsafeMetadata](https://clerk.com/docs/reference/types/metadata.md#user-unsafe-metadata)                                                                                                                                                                                                                                                                                                        | Metadata that can be read and set from the Frontend API. It's considered unsafe because it can be modified from the Frontend API.                                               |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const response = await clerkClient.users.updateUserMetadata(userId, {
  publicMetadata: {
    example: 'metadata',
  },
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/users/{user_id}/metadata`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/PATCH/users/%7Buser_id%7D/metadata){{ target: '_blank' }} for more information.

Here's an example of making a request directly to the endpoint using cURL.

Replace `YOUR_SECRET_KEY` with your Clerk Secret Key. You can find your Secret Key on the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

filename: curl.sh
```bash
curl -XPATCH -H 'Authorization: Bearer {{secret}}' -H "Content-type: application/json" -d '{
  "public_metadata": {
    "birthday": "1990-01-01"
  }
}' 'https://api.clerk.com/v1/users/{user_id}/metadata'
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
