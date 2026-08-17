# BillingSubscriptionItemNextPayment

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=js-frontend) documentation.

The `BillingSubscriptionItemNextPayment` type represents the upcoming payment details for a subscription item.

## Properties

| Property                                    | Type                                                                                                                          | Description                                                 |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| <a id="amount"></a> `amount`                | [BillingMoneyAmount](https://clerk.com/docs/js-frontend/reference/types/billing-money-amount.md)                              | The amount of the next payment.                             |
| <a id="date"></a> `date`                    | `Date`                                                                                                                        | The date when the next payment is due.                      |
| <a id="perunittotals"></a> `perUnitTotals?` | <code><a href="https://clerk.com/docs/js-frontend/reference/types/billing-per-unit-total.md">BillingPerUnitTotal</a>[]</code> | Per-unit cost breakdown for the next payment (e.g., seats). |
| <a id="totals"></a> `totals?`               | [BillingTotals](https://clerk.com/docs/js-frontend/reference/types/billing-totals.md)                                         | Full cost breakdown for the next payment.                   |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
