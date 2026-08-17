# BillingProrationCreditDetail

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=expo) documentation.

Contains details about a proration credit, including the remaining portion of the billing cycle.

## Properties

| Property                                                   | Type                                                                                      | Description                                                |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| <a id="amount"></a> `amount`                               | [BillingMoneyAmount](https://clerk.com/docs/expo/reference/types/billing-money-amount.md) | The monetary value of the proration credit.                |
| <a id="cycledaysremaining"></a> `cycleDaysRemaining`       | `number`                                                                                  | The number of days remaining in the current billing cycle. |
| <a id="cycledaystotal"></a> `cycleDaysTotal`               | `number`                                                                                  | The total number of days in the billing cycle.             |
| <a id="cycleremainingpercent"></a> `cycleRemainingPercent` | `number`                                                                                  | The percentage of the billing cycle that remains.          |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
