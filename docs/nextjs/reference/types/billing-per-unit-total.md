# BillingPerUnitTotal

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=nextjs) documentation.

The `BillingPerUnitTotal` type represents the per-unit cost breakdown in checkout totals.

## Properties

| Property                           | Type                                                                                                                              | Description                                            |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| <a id="blocksize"></a> `blockSize` | `number`                                                                                                                          | The number of units represented by one billable block. |
| <a id="name"></a> `name`           | `string`                                                                                                                          | The unit name, for example `seats`.                    |
| <a id="tiers"></a> `tiers`         | <code><a href="https://clerk.com/docs/nextjs/reference/types/billing-per-unit-total-tier.md">BillingPerUnitTotalTier</a>[]</code> | The tiers breakdown for this unit total.               |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
