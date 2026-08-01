# getSamlConnectionList() (deprecated)

> This method is deprecated. Use [`getEnterpriseConnectionList()`](https://clerk.com/docs/reference/backend/enterprise-connections/get-enterprise-connection-list.md) instead.

Gets the list of SAML connections for an instance. Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property that contains an array of [`SamlConnection`](https://clerk.com/docs/reference/backend/types/backend-saml-connection.md) objects, and a `totalCount` property that indicates the total number of SAML connections for the instance.

```ts
function getSamlConnectionList(params: SamlConnectionListParams = {}): Promise<SamlConnection[]>
```

## `SamlConnectionListParams`

| Name    | Type   | Description                                                                                          |
| ------- | ------ | ---------------------------------------------------------------------------------------------------- |
| limit?  | number | The number of results to return. Must be an integer greater than zero and less than 501. Default: 10 |
| offset? | number | The number of results to skip. Default: 0                                                            |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Basic

```tsx
const response = await clerkClient.samlConnections.getSamlConnectionList()
```

### Limit the number of results

Gets the list of SAML connections, limited to the specified number of results.

```tsx
const { data, totalCount } = await clerkClient.samlConnections.getSamlConnectionList({
  // returns the first 10 results
  limit: 10,
})
```

### Skip results

Gets the list of SAML connections, skipping the specified number of results.

```tsx
const { data, totalCount } = await clerkClient.samlConnections.getSamlConnectionList({
  // skips the first 10 results
  offset: 10,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/saml_connections`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/saml-connections/GET/saml_connections){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
