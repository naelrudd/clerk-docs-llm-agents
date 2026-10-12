# The Backend SamlConnectionIdpCertificate object

One of the Identity Provider (IdP) signing certificates a SAML connection trusts.

## Properties

| Property                               | Type                       | Description                                                                                 |
| -------------------------------------- | -------------------------- | ------------------------------------------------------------------------------------------- |
| <a id="certificate"></a> `certificate` | `string`                   | The X.509 certificate, as base64-encoded DER without PEM armor.                             |
| <a id="expiresat"></a> `expiresAt`     | `null | number` | The Unix timestamp (milliseconds) when the certificate expires, or `null` if unknown.       |
| <a id="issuedat"></a> `issuedAt`       | `null | number` | The Unix timestamp (milliseconds) when the certificate becomes valid, or `null` if unknown. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
