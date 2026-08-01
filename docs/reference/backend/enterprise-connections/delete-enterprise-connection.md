# deleteEnterpriseConnection()

Deletes the given enterprise connection.

Returns the deleted [`EnterpriseConnection`](https://clerk.com/docs/reference/backend/types/backend-enterprise-connection.md) object.

```typescript
function deleteEnterpriseConnection(enterpriseConnectionId: string): Promise<EnterpriseConnection>
```

## Parameters

| Parameter                | Type     | Description                                    |
| ------------------------ | -------- | ---------------------------------------------- |
| `enterpriseConnectionId` | `string` | The ID of the enterprise connection to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.enterpriseConnections.deleteEnterpriseConnection('ec_123')
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/enterprise_connections/{enterprise_connection_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/enterprise-connections/DELETE/enterprise_connections/%7Benterprise_connection_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
