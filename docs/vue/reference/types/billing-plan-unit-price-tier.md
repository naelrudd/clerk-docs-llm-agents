# BillingPlanUnitPriceTier

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=vue) documentation.

The `BillingPlanUnitPriceTier` type represents a single pricing tier for a unit type on a plan.

## Properties

| Property                                     | Type                                                                                     | Description                                                   |
| -------------------------------------------- | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| <a id="endsafterblock"></a> `endsAfterBlock` | `null | number`                                                               | The final block this tier applies to. `null` means unlimited. |
| <a id="feeperblock"></a> `feePerBlock`       | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md) | The fee charged for each block in this tier.                  |
| <a id="id"></a> `id`                         | `string`                                                                                 | The unique identifier of the unit price tier.                 |
| <a id="startsatblock"></a> `startsAtBlock`   | `number`                                                                                 | The first block number this tier applies to.                  |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
