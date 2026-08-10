# The Backend EnterpriseConnectionSamlConnectionLoginHint object

The `login_hint` configuration included on a Backend API [EnterpriseConnectionSamlConnection](https://clerk.com/docs/reference/backend/types/backend-enterprise-connection-saml-connection.md) response.

## Properties

| Property                      | Type                                                      | Description                                                                                                                                                                                                                                       |
| ----------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="mode"></a> `mode`      | `"email_address" | "custom_attribute" | "off"` | How the SAML connection emits the `login_hint` sent to the IdP: `'email_address'` sends the typed identifier, `'custom_attribute'` sends the value stored at the user `publicMetadata` key named by `source`, and `'off'` omits the `login_hint`. |
| <a id="source"></a> `source?` | `string`                                                  | The user `publicMetadata` key the `login_hint` value is read from. Only set when `mode` is `'custom_attribute'`.                                                                                                                                  |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
