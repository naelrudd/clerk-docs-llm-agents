# updateRestrictions()

Updates the [restriction](https://clerk.com/docs/guides/secure/restricting-access.md) settings for the current instance.

Returns the updated [`InstanceRestrictions`](https://clerk.com/docs/reference/backend/types/backend-instance-restrictions.md) object.

```typescript
function updateRestrictions(params: UpdateRestrictionsParams): Promise<InstanceRestrictions>
```

## `UpdateRestrictionsParams`

| Property                                                                | Type                        | Description                                                                                                                                                                                                     |
| ----------------------------------------------------------------------- | --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="allowlist"></a> `allowlist?`                                     | `boolean | null` | Whether the instance should have [**Allowlist**](https://clerk.com/docs/guides/secure/restricting-access.md#allowlist) enabled.                                                                                 |
| <a id="blockdisposableemaildomains"></a> `blockDisposableEmailDomains?` | `boolean | null` | Whether the instance should have [**Block sign-ups that use disposable email domains**](https://clerk.com/docs/guides/secure/restricting-access.md#block-sign-ups-that-use-disposable-email-addresses) enabled. |
| <a id="blockemailsubaddresses"></a> `blockEmailSubaddresses?`           | `boolean | null` | Whether the instance should have [**Block email subaddresses**](https://clerk.com/docs/guides/secure/restricting-access.md#block-email-subaddresses) enabled.                                                   |
| <a id="blocklist"></a> `blocklist?`                                     | `boolean | null` | Whether the instance should have [**Blocklist**](https://clerk.com/docs/guides/secure/restricting-access.md#blocklist) enabled.                                                                                 |
| <a id="ignoredotsforgmailaddresses"></a> `ignoreDotsForGmailAddresses?` | `boolean | null` | Whether the instance should [ignore dots for Gmail addresses](https://clerk.com/docs/guides/secure/restricting-access.md#block-email-subaddresses).                                                             |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.instances.updateRestrictions({
  allowlist: true,
  blockEmailSubaddresses: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/instance/restrictions`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/instance-settings/PATCH/instance/restrictions){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
