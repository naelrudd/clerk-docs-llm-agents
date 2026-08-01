# BillingStatementTotals

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=expo) documentation.

The `BillingStatementTotals` type represents the total costs, taxes, and other pricing details for a statement.

## Properties

| Property                             | Type                                                                                      | Description                                                                                                               |
| ------------------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| <a id="grandtotal"></a> `grandTotal` | [BillingMoneyAmount](https://clerk.com/docs/expo/reference/types/billing-money-amount.md) | The total amount for the checkout, including taxes and after credits/discounts are applied. This is the final amount due. |
| <a id="subtotal"></a> `subtotal`     | [BillingMoneyAmount](https://clerk.com/docs/expo/reference/types/billing-money-amount.md) | The price of the items or Plan before taxes, credits, or discounts are applied.                                           |
| <a id="taxtotal"></a> `taxTotal`     | [BillingMoneyAmount](https://clerk.com/docs/expo/reference/types/billing-money-amount.md) | The amount of tax included in the checkout.                                                                               |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
