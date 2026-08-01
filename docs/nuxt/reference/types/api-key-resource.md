# APIKeyResource

An interface that describes an API key used to authenticate requests to your application's API endpoints on behalf of a user or organization.

## Properties

| Property                                         | Type                                    | Description                                                                                                                                                                            |
| ------------------------------------------------ | --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="claims"></a> `claims`                     | <code>null | Record<string, any></code> | Custom claims associated with the API key, or `null` if none.                                                                                                                          |
| <a id="createdat"></a> `createdAt`               | `Date`                                  | The date and time when the API key was created.                                                                                                                                        |
| <a id="createdby"></a> `createdBy`               | `null | string`              | The ID of the user that created the API key.                                                                                                                                           |
| <a id="description"></a> `description`           | `null | string`              | A description for the API key.                                                                                                                                                         |
| <a id="expiration"></a> `expiration`             | `null | Date`                | The expiration date and time for the API key, or `null` if the key never expires.                                                                                                      |
| <a id="expired"></a> `expired`                   | `boolean`                               | Indicates whether the API key has expired.                                                                                                                                             |
| <a id="id"></a> `id`                             | `string`                                | A unique identifier for the API key.                                                                                                                                                   |
| <a id="lastusedat"></a> `lastUsedAt`             | `null | Date`                | The date and time when the API key was last used to authenticate a request, or `null` if it has never been used.                                                                       |
| <a id="name"></a> `name`                         | `string`                                | The name of the API key.                                                                                                                                                               |
| <a id="revocationreason"></a> `revocationReason` | `null | string`              | The reason the API key was revoked, or `null` if not revoked.                                                                                                                          |
| <a id="revoked"></a> `revoked`                   | `boolean`                               | Indicates whether the API key has been revoked.                                                                                                                                        |
| <a id="scopes"></a> `scopes`                     | `string[]`                   | An array of scopes that define what the API key can access.                                                                                                                            |
| <a id="secret"></a> `secret?`                    | `string`                                | The API key secret. **This property is only present in the response from [create()](https://clerk.com/docs/nuxt/reference/objects/api-keys.md#create) and cannot be retrieved later.** |
| <a id="subject"></a> `subject`                   | `string`                                | The user or organization ID that the API key is associated with.                                                                                                                       |
| <a id="type"></a> `type`                         | `string`                                | The type of the API key.                                                                                                                                                               |
| <a id="updatedat"></a> `updatedAt`               | `Date`                                  | The date and time when the API key was last updated.                                                                                                                                   |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
