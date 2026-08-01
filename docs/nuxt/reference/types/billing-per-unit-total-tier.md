# BillingPerUnitTotalTier

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=nuxt) documentation.

The `BillingPerUnitTotalTier` type represents the cost breakdown for a single tier in checkout totals.

## Properties

| Property                               | Type                                                                                      | Description                                                   |
| -------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| <a id="feeperblock"></a> `feePerBlock` | [BillingMoneyAmount](https://clerk.com/docs/nuxt/reference/types/billing-money-amount.md) | The fee charged per block for this tier.                      |
| <a id="quantity"></a> `quantity`       | `null | number`                                                                | The quantity billed within this tier. `null` means unlimited. |
| <a id="total"></a> `total`             | [BillingMoneyAmount](https://clerk.com/docs/nuxt/reference/types/billing-money-amount.md) | The total billed amount for this tier.                        |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
