# The Backend EnterpriseAccount object

The Backend `EnterpriseAccount` object represents an identification obtained via enterprise SSO (SAML or OIDC).

## Properties

| Property                                                     | Type                                                                                                                                                  | Description                                                                                               |
| ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| <a id="active"></a> `active`                                 | `boolean`                                                                                                                                             | Whether this enterprise account is currently active.                                                      |
| <a id="emailaddress"></a> `emailAddress`                     | `string`                                                                                                                                              | The email address associated with this enterprise account.                                                |
| <a id="enterpriseconnection"></a> `enterpriseConnection`     | <code>null | <a href="https://clerk.com/docs/reference/backend/types/backend-enterprise-account-connection.md">EnterpriseAccountConnection</a></code> | The enterprise connection through which this account was authenticated.                                   |
| <a id="enterpriseconnectionid"></a> `enterpriseConnectionId` | `null | string`                                                                                                                            | The ID of the enterprise connection associated with this account.                                         |
| <a id="firstname"></a> `firstName`                           | `null | string`                                                                                                                            | The user's first name as provided by the IdP.                                                             |
| <a id="id"></a> `id`                                         | `string`                                                                                                                                              | The unique identifier for this enterprise account.                                                        |
| <a id="lastauthenticatedat"></a> `lastAuthenticatedAt`       | `null | number`                                                                                                                            | The date when the user last authenticated via this enterprise account.                                    |
| <a id="lastname"></a> `lastName`                             | `null | string`                                                                                                                            | The user's last name as provided by the IdP.                                                              |
| <a id="protocol"></a> `protocol`                             | `string`                                                                                                                                              | The SSO protocol used (e.g., `saml` or `oauth`).                                                          |
| <a id="provider"></a> `provider`                             | `string`                                                                                                                                              | The SSO provider (e.g., `saml_custom`, `saml_okta`).                                                      |
| <a id="provideruserid"></a> `providerUserId`                 | `null | string`                                                                                                                            | The unique ID of the user in the provider.                                                                |
| <a id="publicmetadata"></a> `publicMetadata`                 | `Record`<`string`, `unknown`>                                                                                                                        | Metadata that can be read from the Frontend API and Backend API and can be set only from the Backend API. |
| <a id="verification"></a> `verification`                     | <code>null | <a href="https://clerk.com/docs/reference/backend/types/backend-verification.md">Verification</a></code>                                 | An object holding information on the verification of this enterprise account.                             |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
