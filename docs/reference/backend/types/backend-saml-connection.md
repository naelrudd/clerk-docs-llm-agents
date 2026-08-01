# The Backend SamlConnection object

The Backend `SamlConnection` object holds information about a SAML connection for an organization.

## Deprecated

Use [`EnterpriseConnection`](https://clerk.com/docs/reference/backend/types/backend-enterprise-connection.md) instead.

## Properties

| Property                                                           | Type                       | Description                                                                                                                                             |
| ------------------------------------------------------------------ | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="acsurl"></a> ~~`acsUrl`~~                                   | `string`                   | The Assertion Consumer Service (ACS) URL of the connection.                                                                                             |
| <a id="active"></a> ~~`active`~~                                   | `boolean`                  | Whether the connection is active or not.                                                                                                                |
| <a id="allowidpinitiated"></a> ~~`allowIdpInitiated`~~             | `boolean`                  | Whether the connection allows Identity Provider (IdP) initiated flows or not.                                                                           |
| <a id="allowsubdomains"></a> ~~`allowSubdomains`~~                 | `boolean`                  | Whether users with an email address subdomain are allowed to use this connection in order to authenticate or not.                                       |
| <a id="attributemapping"></a> ~~`attributeMapping`~~               | `AttributeMapping`         | Defines the attribute name mapping between the Identity Provider (IdP) and Clerk's [User](https://clerk.com/docs/reference/objects/user.md) properties. |
| <a id="createdat"></a> ~~`createdAt`~~                             | `number`                   | The Unix timestamp when the connection was first created.                                                                                               |
| <a id="domain"></a> ~~`domain`~~                                   | `string`                   | The domain of your Organization. Sign in flows using an email with this domain will use the connection.                                                 |
| <a id="id"></a> ~~`id`~~                                           | `string`                   | The unique identifier for the connection.                                                                                                               |
| <a id="idpcertificate"></a> ~~`idpCertificate`~~                   | `null | string` | The X.509 certificate as provided by the Identity Provider (IdP).                                                                                       |
| <a id="idpcertificateexpiresat"></a> ~~`idpCertificateExpiresAt`~~ | `number`                   | The Unix timestamp when the Identity Provider (IdP) certificate expires.                                                                                |
| <a id="idpcertificateissuedat"></a> ~~`idpCertificateIssuedAt`~~   | `number`                   | The Unix timestamp when the Identity Provider (IdP) certificate was issued.                                                                             |
| <a id="idpentityid"></a> ~~`idpEntityId`~~                         | `null | string` | The Entity ID as provided by the Identity Provider (IdP).                                                                                               |
| <a id="idpmetadata"></a> ~~`idpMetadata`~~                         | `null | string` | The XML content of the Identity Provider (IdP) metadata file. If present, it takes priority over the corresponding individual properties.               |
| <a id="idpmetadataurl"></a> ~~`idpMetadataUrl`~~                   | `null | string` | The URL which serves the Identity Provider (IdP) metadata. If present, it takes priority over the corresponding individual properties.                  |
| <a id="idpssourl"></a> ~~`idpSsoUrl`~~                             | `null | string` | The Single-Sign On URL as provided by the Identity Provider (IdP).                                                                                      |
| <a id="name"></a> ~~`name`~~                                       | `string`                   | The name to use as a label for the connection.                                                                                                          |
| <a id="organizationid"></a> ~~`organizationId`~~                   | `null | string` | The Organization ID of the Organization.                                                                                                                |
| <a id="provider"></a> ~~`provider`~~                               | `string`                   | The Identity Provider (IdP) of the connection.                                                                                                          |
| <a id="spentityid"></a> ~~`spEntityId`~~                           | `string`                   | The Entity ID as provided by the Service Provider (Clerk).                                                                                              |
| <a id="spmetadataurl"></a> ~~`spMetadataUrl`~~                     | `string`                   | The metadata URL as provided by the Service Provider (Clerk).                                                                                           |
| <a id="syncuserattributes"></a> ~~`syncUserAttributes`~~           | `boolean`                  | Whether the connection syncs user attributes between the Service Provider (SP) and Identity Provider (IdP) or not.                                      |
| <a id="updatedat"></a> ~~`updatedAt`~~                             | `number`                   | The Unix timestamp when the connection was last updated.                                                                                                |
| <a id="usercount"></a> ~~`userCount`~~                             | `number`                   | The number of users associated with the connection.                                                                                                     |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
