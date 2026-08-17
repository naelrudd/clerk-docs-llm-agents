# BillingAppliedDiscount

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=expo) documentation.

A catalog discount applied to a checkout or payment.

## Properties

| Property                                          | Type                                                                                      | Description                                                                                                                                                                         |
| ------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="amount"></a> `amount`                      | [BillingMoneyAmount](https://clerk.com/docs/expo/reference/types/billing-money-amount.md) | The monetary value of the discount applied to the transaction.                                                                                                                      |
| <a id="amountoff"></a> `amountOff?`               | [BillingMoneyAmount](https://clerk.com/docs/expo/reference/types/billing-money-amount.md) | The configured fixed amount off when `effect` is `'fixed_amount'`. This is the discount's configured value, which can differ from the `amount` actually applied to the transaction. |
| <a id="cyclesremaining"></a> `cyclesRemaining`    | `null | number`                                                                | The number of billing cycles for which the discount remains active. `null` means the discount does not expire after a fixed number of cycles.                                       |
| <a id="discountid"></a> `discountId`              | `string`                                                                                  | The unique identifier of the discount.                                                                                                                                              |
| <a id="durationincycles"></a> `durationInCycles?` | `null | number`                                                                | The originally configured duration in billing cycles. `null` means the discount does not expire after a fixed number of cycles.                                                     |
| <a id="effect"></a> `effect`                      | `"percentage" | "fixed_amount"`                                                | Whether the discount subtracts a percentage or a fixed amount.                                                                                                                      |
| <a id="name"></a> `name`                          | `string`                                                                                  | The display name of the discount.                                                                                                                                                   |
| <a id="percentoff"></a> `percentOff?`             | `number`                                                                                  | The percentage deducted when `effect` is `'percentage'`.                                                                                                                            |
| <a id="promocode"></a> `promoCode?`               | `string`                                                                                  | The promotion code used to apply the discount.                                                                                                                                      |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
