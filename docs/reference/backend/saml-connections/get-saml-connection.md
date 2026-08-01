# getSamlConnection() (deprecated)

> This method is deprecated. Use [`getEnterpriseConnection()`](https://clerk.com/docs/reference/backend/enterprise-connections/get-enterprise-connection.md) instead.

Gets the given [`SamlConnection`](https://clerk.com/docs/reference/backend/types/backend-saml-connection.md).

```ts
function getSamlConnection(samlConnectionId: string): Promise<SamlConnection>
```

## `GetOrganizationParams`

| Name             | Type   | Description                                |
| ---------------- | ------ | ------------------------------------------ |
| samlConnectionId | string | The ID of the SAML connection to retrieve. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const samlConnectionId = 'samlc_123'

const response = await clerkClient.samlConnections.getSamlConnection(samlConnectionId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/saml_connections/{saml_connection_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/saml-connections/GET/saml_connections/%7Bsaml_connection_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
