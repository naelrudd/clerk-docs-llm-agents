# Backend Domain object

The `Domain` object represents a domain that is managed by the instance.

## Properties

| Property                                            | Type                       | Description                                                                                        |
| --------------------------------------------------- | -------------------------- | -------------------------------------------------------------------------------------------------- |
| <a id="accountsportalurl"></a> `accountsPortalUrl?` | `null | string` | The [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md) URL for the domain. |
| <a id="cnametargets"></a> `cnameTargets`            | `CnameTarget[]` | The CNAME targets for the domain.                                                                  |
| <a id="developmentorigin"></a> `developmentOrigin`  | `string`                   | The development origin for the domain.                                                             |
| <a id="frontendapiurl"></a> `frontendApiUrl`        | `string`                   | The Frontend API URL for the domain.                                                               |
| <a id="id"></a> `id`                                | `string`                   | The unique identifier of the domain.                                                               |
| <a id="issatellite"></a> `isSatellite`              | `boolean`                  | Whether the domain is a satellite domain.                                                          |
| <a id="name"></a> `name`                            | `string`                   | The name of the domain.                                                                            |
| <a id="proxyurl"></a> `proxyUrl?`                   | `null | string` | The [proxy URL](https://clerk.com/docs/guides/dashboard/dns-domains/proxy-fapi.md) for the domain. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
