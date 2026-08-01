# BillingPlanUnitPrice

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=astro) documentation.

The `BillingPlanUnitPrice` type represents unit pricing for a specific unit type (e.g., seats) on a plan.

## Properties

| Property                           | Type                                                                                                                               | Description                                        |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| <a id="blocksize"></a> `blockSize` | `number`                                                                                                                           | Number of units represented by one billable block. |
| <a id="name"></a> `name`           | `string`                                                                                                                           | The unit name, for example `seats`.                |
| <a id="tiers"></a> `tiers`         | <code><a href="https://clerk.com/docs/astro/reference/types/billing-plan-unit-price-tier.md">BillingPlanUnitPriceTier</a>[]</code> | Tiers that define how each block range is priced.  |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
