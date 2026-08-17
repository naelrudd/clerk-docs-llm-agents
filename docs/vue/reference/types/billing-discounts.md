# BillingDiscounts

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=vue) documentation.

Discounts applied to the checkout, such as prorated discounts for mid-cycle seat additions.

## Properties

| Property                           | Type                                                                                                                                | Description                                                                                                                                                                                                                                                                                                               |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="discount"></a> `discount?`  | [BillingAppliedDiscount](https://clerk.com/docs/vue/reference/types/billing-applied-discount.md)                                    | The catalog discount applied to the transaction. This field is omitted when no catalog discount applies.                                                                                                                                                                                                                  |
| <a id="proration"></a> `proration` | <code>null | <a href="https://clerk.com/docs/vue/reference/types/billing-proration-discount.md">BillingProrationDiscount</a></code> | The prorated discount for the part of the billing period that has already passed when adding a seat mid-cycle. Unlike the proration credit (which refunds the unused remainder of a plan you already paid for), this discount means you are not charged for the portion of the new seat's cycle that has already elapsed. |
| <a id="total"></a> `total`         | [BillingMoneyAmount](https://clerk.com/docs/vue/reference/types/billing-money-amount.md)                                            | The total of all discounts applied to the checkout.                                                                                                                                                                                                                                                                       |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
