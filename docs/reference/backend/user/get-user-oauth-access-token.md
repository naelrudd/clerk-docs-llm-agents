# getUserOauthAccessToken()

Gets the corresponding OAuth access token for a user that has previously authenticated with the given OAuth provider.

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property that contains an array of [`OauthAccessToken`](https://clerk.com/docs/reference/backend/types/backend-oauth-access-token.md) objects, and a `totalCount` property that indicates the total number of OAuth access tokens for the specified user and provider.

```typescript
function getUserOauthAccessToken(userId: string, provider: OAuthProvider): Promise<PaginatedResourceResponse<OauthAccessToken[]>>
```

## Parameters

| Parameter  | Type                                                                           | Description                                                                                                                                               |
| ---------- | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `userId`   | `string`                                                                       | The ID of the user to get the OAuth access tokens for.                                                                                                    |
| `provider` | [OAuthProvider](https://clerk.com/docs/reference/types/sso.md#o-auth-provider) | The OAuth provider to get the access tokens for. If using a custom OAuth provider, prefix the provider name with `custom_` (e.g., `oauth_custom_google`). |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'

const provider = 'google'

const response = await clerkClient.users.getUserOauthAccessToken(userId, provider)
```

You can also explore [the example](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/overview.md#get-an-o-auth-access-token-for-a-social-provider) that demonstrates how this method retrieves a social provider's OAuth access token, enabling access to user data from both the provider and Clerk.

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/users/{user_id}/oauth_access_tokens/{provider}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/GET/users/%7Buser_id%7D/oauth_access_tokens/%7Bprovider%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
