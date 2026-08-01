# getEnterpriseConnectionList()

Gets the list of enterprise connections for the instance. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`EnterpriseConnection`](https://clerk.com/docs/reference/backend/types/backend-enterprise-connection.md) objects and a `totalCount` property containing the total number of enterprise connections for the instance.

```typescript
function getEnterpriseConnectionList(params: EnterpriseConnectionListParams): Promise<PaginatedResourceResponse<EnterpriseConnection[]>>
```

## `EnterpriseConnectionListParams`

| Property                      | Type      | Description                                                                                                                                                                                     |
| ----------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `active?`                     | `boolean` | Filters enterprise connections by active status. If `true`, only active connections are returned. If `false`, only inactive connections are returned. If omitted, all connections are returned. |
| <a id="limit"></a> `limit?`   | `number`  | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`.          |
| <a id="offset"></a> `offset?` | `number`  | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                                        |
| `organizationId?`             | `string`  | Filters enterprise connections by Organization ID.                                                                                                                                              |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.enterpriseConnections.getEnterpriseConnectionList()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/enterprise_connections`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/enterprise-connections/GET/enterprise_connections){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
