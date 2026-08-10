# The Backend EnterpriseConnectionCustomAttribute object

A custom attribute mapping included on a Backend API [EnterpriseConnection](https://clerk.com/docs/reference/backend/types/backend-enterprise-connection.md) response.

## Properties

| Property                               | Type      | Description                                                   |
| -------------------------------------- | --------- | ------------------------------------------------------------- |
| <a id="key"></a> `key`                 | `string`  | The key the custom attribute is stored under.                 |
| <a id="multivalued"></a> `multiValued` | `boolean` | Whether the custom attribute holds multiple values.           |
| <a id="name"></a> `name`               | `string`  | The display name of the custom attribute.                     |
| <a id="scimpath"></a> `scimPath`       | `string`  | The SCIM attribute path the value is read from.               |
| <a id="ssopath"></a> `ssoPath`         | `string`  | The SSO (SAML or OIDC) attribute path the value is read from. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
