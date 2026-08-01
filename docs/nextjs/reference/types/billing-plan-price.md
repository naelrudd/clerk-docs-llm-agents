# BillingPlanPrice

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=nextjs) documentation.

The `BillingPlanPrice` type represents a specific possible price for a given Clerk Billing Plan.

## Properties

| Property                                         | Type                                                                                                                       | Description                                                                            |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| <a id="annualmonthlyfee"></a> `annualMonthlyFee` | <code>null | <a href="https://clerk.com/docs/nextjs/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | The effective monthly price when billed annually or `null` if the price is not annual. |
| <a id="fee"></a> `fee`                           | <code>null | <a href="https://clerk.com/docs/nextjs/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | The monthly price or `null` if the price is not monthly.                               |
| <a id="id"></a> `id`                             | `string`                                                                                                                   | The unique identifier of the price                                                     |
| <a id="isdefault"></a> `isDefault`               | `boolean`                                                                                                                  | Whether this price is the default price for the plan it's associated with.             |
| <a id="unitprices"></a> `unitPrices?`            | <code><a href="https://clerk.com/docs/nextjs/reference/types/billing-plan-unit-price.md">BillingPlanUnitPrice</a>[]</code> | The individual unit prices applicable to this price.                                   |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
