# BillingProrationDiscount

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=vue) documentation.

Details about a prorated discount applied when adding a seat mid-cycle. The discount covers the part of the
billing period that has already passed, so the payer is only charged for the time remaining in the cycle.

## Properties

| Property                                             | Type                                                                                     | Description                                                                                            |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| <a id="amount"></a> `amount`                         | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md) | The amount of the proration discount.                                                                  |
| <a id="cycledayspassed"></a> `cycleDaysPassed`       | `number`                                                                                 | The number of days that have passed in the billing cycle for which this proration discount represents. |
| <a id="cycledaystotal"></a> `cycleDaysTotal`         | `number`                                                                                 | The total number of days in the billing cycle.                                                         |
| <a id="cyclepassedpercent"></a> `cyclePassedPercent` | `number`                                                                                 | The percentage of the billing cycle that has passed.                                                   |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
