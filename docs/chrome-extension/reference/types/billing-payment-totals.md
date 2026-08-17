# BillingPaymentTotals

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=chrome-extension) documentation.

The `BillingPaymentTotals` type represents the per-payment cost breakdown, including any base fee
and per-unit (e.g., seats) subtotals.

## Properties

| Property                                    | Type                                                                                                                                 | Description                                                                                                  |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| <a id="basefee"></a> `baseFee?`             | <code>null | <a href="https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | The flat base fee charged on top of any per-unit fees.                                                       |
| <a id="discounts"></a> `discounts?`         | <code>null | <a href="https://clerk.com/docs/chrome-extension/reference/types/billing-discounts.md">BillingDiscounts</a></code>      | Discounts applied to this payment such as mid-cycle prorated seat discounts. `null` when no discounts apply. |
| <a id="grandtotal"></a> `grandTotal`        | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                                | The total amount for the payment, including taxes and after credits/discounts are applied.                   |
| <a id="perunittotals"></a> `perUnitTotals?` | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/billing-per-unit-total.md">BillingPerUnitTotal</a>[]</code>   | Per-unit cost breakdown for this payment (e.g., seats).                                                      |
| <a id="subtotal"></a> `subtotal`            | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                                | The price of the items before taxes, credits, or discounts are applied.                                      |
| <a id="taxtotal"></a> `taxTotal`            | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                                | The amount of tax included in the payment.                                                                   |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
