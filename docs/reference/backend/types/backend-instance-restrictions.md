# The Backend InstanceRestrictions object

The `InstanceRestrictions` object represents the [restrictions](https://clerk.com/docs/guides/secure/restricting-access.md) settings for the current instance.

## Properties

| Property                                                               | Type      | Description                                                                                                                                                                                             |
| ---------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="allowlist"></a> `allowlist`                                     | `boolean` | Whether the instance has [**Allowlist**](https://clerk.com/docs/guides/secure/restricting-access.md#allowlist) enabled.                                                                                 |
| <a id="blockdisposableemaildomains"></a> `blockDisposableEmailDomains` | `boolean` | Whether the instance has [**Block sign-ups that use disposable email domains**](https://clerk.com/docs/guides/secure/restricting-access.md#block-sign-ups-that-use-disposable-email-addresses) enabled. |
| <a id="blockemailsubaddresses"></a> `blockEmailSubaddresses`           | `boolean` | Whether the instance has [**Block email subaddresses**](https://clerk.com/docs/guides/secure/restricting-access.md#block-email-subaddresses) enabled.                                                   |
| <a id="blocklist"></a> `blocklist`                                     | `boolean` | Whether the instance has [**Blocklist**](https://clerk.com/docs/guides/secure/restricting-access.md#blocklist) enabled.                                                                                 |
| <a id="ignoredotsforgmailaddresses"></a> `ignoreDotsForGmailAddresses` | `boolean` | Whether the instance has [**Ignore dots for Gmail addresses**](https://clerk.com/docs/guides/secure/restricting-access.md#block-email-subaddresses) enabled.                                            |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
