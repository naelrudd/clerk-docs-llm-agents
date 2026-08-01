# create()

Creates a new OAuth application.

Returns the created [`OAuthApplication`](https://clerk.com/docs/reference/backend/types/backend-oauth-application.md) object.

```typescript
function create(params: CreateOAuthApplicationParams): Promise<OAuthApplication>
```

## `CreateOAuthApplicationParams`

| Property                                  | Type                         | Description                                                                                                                                                                                                                                    |
| ----------------------------------------- | ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="name"></a> `name`                  | `string`                     | A descriptive name for the OAuth application (e.g., "My Web App", "My Mobile App"). Maximum length: 256 characters.                                                                                                                            |
| <a id="public"></a> `public?`             | `boolean | null`  | Whether the OAuth application is public. If `true`, the Proof Key of Code Exchange (PKCE) flow can be used.                                                                                                                                    |
| <a id="redirecturis"></a> `redirectUris?` | `string[] | null` | An array of redirect URIs for the OAuth application.                                                                                                                                                                                           |
| <a id="scopes"></a> `scopes?`             | `string | null`   | Scopes for the OAuth application that dictate the user payload of the OAuth user info endpoint. Available scopes are `profile`, `email`, `public_metadata`, `private_metadata`. Provide the requested scopes as a string, separated by spaces. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.oauthApplications.create({
  name: 'oauthapp_123',
  redirect_uris: [''],
  scopes: 'profile email public_metadata',
  public: null,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/oauth_applications`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/oauth-applications/POST/oauth_applications){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
