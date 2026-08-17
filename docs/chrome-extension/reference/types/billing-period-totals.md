# BillingPeriodTotals

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=chrome-extension) documentation.

Per-period renewal totals, describing what the subscription renewal charge will look like after the current checkout.
Unlike the top-level checkout totals (which only reflect the items actively being purchased),
this object contains the full renewal breakdown including all seats and the base plan fee.

## Properties

| Property                                    | Type                                                                                                                               | Description                                                                                                                            |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="basefee"></a> `baseFee`              | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                              | The base fee for the billing period.                                                                                                   |
| <a id="grandtotal"></a> `grandTotal`        | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                              | The grand total for the billing period.                                                                                                |
| <a id="perunittotals"></a> `perUnitTotals?` | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/billing-per-unit-total.md">BillingPerUnitTotal</a>[]</code> | Per-unit cost breakdown for the renewal period, covering all units purchased to date (not just the ones being added in this checkout). |
| <a id="subtotal"></a> `subtotal`            | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                              | The subtotal for the billing period.                                                                                                   |
| <a id="taxtotal"></a> `taxTotal`            | [BillingMoneyAmount](https://clerk.com/docs/chrome-extension/reference/types/billing-money-amount.md)                              | The tax total for the billing period.                                                                                                  |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
