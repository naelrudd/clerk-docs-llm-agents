# BillingTotals

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=vue) documentation.

The `BillingTotals` type represents a granular breakdown of the total amount that will be charged, either during
checkout or at renewal.

## Properties

| Property                                                      | Type                                                                                                                    | Description                                                |
| ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| <a id="basefee"></a> `baseFee`                                | <code>null | <a href="https://clerk.com/docs/vue/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | Base fee component before per-unit charges and adjustments |
| <a id="credit"></a> `credit?`                                 | <code>null | <a href="https://clerk.com/docs/vue/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | Credit amount                                              |
| <a id="credits"></a> `credits`                                | `null | BillingCredits`                                                                                      | Unified credits breakdown                                  |
| <a id="discounts"></a> `discounts`                            | <code>null | <a href="billing-discounts.mdx">BillingDiscounts</a></code>                                                | Information about the discounts applied to the payment     |
| <a id="grandtotal"></a> `grandTotal`                          | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md)                                | Grand total amount                                         |
| <a id="pastdue"></a> `pastDue?`                               | <code>null | <a href="https://clerk.com/docs/vue/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | Past due amount                                            |
| <a id="perunittotals"></a> `perUnitTotals?`                   | <code><a href="https://clerk.com/docs/vue/reference/types/billing-per-unit-total.md">BillingPerUnitTotal</a>[]</code>   | Per-unit total breakdown (e.g., seats)                     |
| <a id="subtotal"></a> `subtotal`                              | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md)                                | Subtotal before adjustments                                |
| <a id="taxtotal"></a> `taxTotal`                              | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md)                                | Total tax amount                                           |
| <a id="totaldueafterfreetrial"></a> `totalDueAfterFreeTrial?` | <code>null | <a href="https://clerk.com/docs/vue/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | Total amount due after free trial ends                     |
| <a id="totalduenow"></a> `totalDueNow?`                       | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md)                                | Total amount due now                                       |
| <a id="totaldueperperiod"></a> `totalDuePerPeriod?`           | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md)                                | The expected total payment for each future billing period  |
| <a id="totalsdueperperiod"></a> `totalsDuePerPeriod?`         | [`BillingPeriodTotals`](billing-period-totals.mdx)                                                                      | Per-period renewal totals, broken down granularly          |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
