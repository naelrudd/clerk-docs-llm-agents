# updateUserProfileImage()

Updates the profile image for the given user. To remove the profile image, see [`deleteUserProfileImage()`](https://clerk.com/docs/reference/backend/user/delete-user-profile-image.md).

Returns the updated [`User`](https://clerk.com/docs/reference/backend/types/backend-user.md).

```typescript
function updateUserProfileImage(userId: string, params: { file: Blob | File }): Promise<User>
```

## Parameters

| Parameter | Type                                | Description                                         |
| --------- | ----------------------------------- | --------------------------------------------------- |
| `userId`  | `string`                            | The ID of the user to update the profile image for. |
| `params`  | `{ file: Blob | File; }` | The file to set as the user's profile image.        |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

> Using `clerkClient` methods can contribute towards rate limiting. To set a user's profile image, it's recommended to use the frontend [user.setProfileImage()](https://clerk.com/docs/reference/objects/user.md#set-profile-image) method instead.

```tsx
const userId = 'user_123'
const fileBits = ['profile-pic-content']
const fileName = 'profile-pic.png'
const file = new File(fileBits, fileName, { type: 'image/png' })

const params = {
  file,
}

const response = await clerkClient.users.updateUserProfileImage(userId, params)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/users/{user_id}/profile_image`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/POST/users/%7Buser_id%7D/profile_image){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
