# verifyClient()

Verifies the client in the given token.

Returns the verified [`Client`](https://clerk.com/docs/reference/backend/types/backend-client.md).

```typescript
function verifyClient(token: string): Promise<Client>
```

## Parameters

| Parameter | Type     | Description          |
| --------- | -------- | -------------------- |
| `token`   | `string` | The token to verify. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const token = 'my-session-token'

const response = await clerkClient.clients.verifyClient(token)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/clients/verify`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/clients/POST/clients/verify){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
