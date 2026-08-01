# The Backend M2MToken object

The Backend `M2MToken` object holds information about a [machine-to-machine token](https://clerk.com/docs/guides/development/machine-auth/m2m-tokens.md).

## Properties

| Property                                         | Type                                    | Description                                                               |
| ------------------------------------------------ | --------------------------------------- | ------------------------------------------------------------------------- |
| <a id="claims"></a> `claims`                     | <code>null | Record<string, any></code> | The claims of the M2M token.                                              |
| <a id="createdat"></a> `createdAt`               | `number`                                | The Unix timestamp (in milliseconds) when the M2M token was created.      |
| <a id="expiration"></a> `expiration`             | `null | number`              | The Unix timestamp (in milliseconds) when the M2M token expires.          |
| <a id="expired"></a> `expired`                   | `boolean`                               | Whether the M2M token has expired.                                        |
| <a id="id"></a> `id`                             | `string`                                | The ID of the M2M token.                                                  |
| <a id="revocationreason"></a> `revocationReason` | `null | string`              | The reason for revoking the M2M token.                                    |
| <a id="revoked"></a> `revoked`                   | `boolean`                               | Whether the M2M token has been revoked.                                   |
| <a id="scopes"></a> `scopes`                     | `string[]`                   | The scopes of the M2M token.                                              |
| <a id="subject"></a> `subject`                   | `string`                                | The subject of the M2M token.                                             |
| <a id="token"></a> `token?`                      | `string`                                | The token string.                                                         |
| <a id="updatedat"></a> `updatedAt`               | `number`                                | The Unix timestamp (in milliseconds) when the M2M token was last updated. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
