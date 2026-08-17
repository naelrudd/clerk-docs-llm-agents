# BillingCredits

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=react) documentation.

The `BillingCredits` type represents the credits applied to a checkout or payment.

## Properties

| Property                           | Type                                                                                                                                           | Description                                                                                              |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| <a id="payer"></a> `payer`         | <code>null | <a href="https://clerk.com/docs/react/reference/types/billing-payer-credit.md">BillingPayerCredit</a></code>                      | The payer credit applied to the transaction. `null` when no payer credit applies.                        |
| <a id="proration"></a> `proration` | <code>null | <a href="https://clerk.com/docs/react/reference/types/billing-proration-credit-detail.md">BillingProrationCreditDetail</a></code> | The credit for the unused portion of the current billing cycle. `null` when no proration credit applies. |
| <a id="total"></a> `total`         | [BillingMoneyAmount](https://clerk.com/docs/react/reference/types/billing-money-amount.md)                                                     | The total monetary value of all credits applied to the transaction.                                      |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
