# getClient()

Gets the given [`Client`](https://clerk.com/docs/reference/backend/types/backend-client.md).

```typescript
function getClient(clientId: string): Promise<Client>
```

## Parameters

| Parameter  | Type     | Description                  |
| ---------- | -------- | ---------------------------- |
| `clientId` | `string` | The ID of the client to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const clientId = 'client_123'

const response = await clerkClient.clients.getClient(clientId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/clients/{client_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/clients/GET/clients/%7Bclient_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
