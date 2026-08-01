# Backend BillingSubscriptionItem object

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

The `BillingSubscriptionItem` object is similar to the [BillingSubscriptionItemResource](https://clerk.com/docs/reference/types/billing-subscription-item-resource.md) object as it holds information about a subscription item, as well as methods for managing it. However, the `BillingSubscriptionItem` object is different in that it is used in the [Backend API](https://clerk.com/docs/reference/backend-api/tag/billing/GET/billing/subscription_items){{ target: '_blank' }} and is not directly accessible from the Frontend API.

## Properties

| Property                                  | Type                                                                                                                     | Description                                                                       |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------- |
| <a id="amount"></a> `amount`              | <code>undefined | <a href="https://clerk.com/docs/reference/types/billing-money-amount.md">BillingMoneyAmount</a></code> | The current amount for the Subscription Item.                                     |
| <a id="canceledat"></a> `canceledAt`      | `null | number`                                                                                               | The Unix timestamp (milliseconds) of when the Subscription Item was canceled.     |
| <a id="createdat"></a> `createdAt`        | `number`                                                                                                                 | The Unix timestamp (milliseconds) of when the Subscription Item was created.      |
| <a id="endedat"></a> `endedAt`            | `null | number`                                                                                               | The Unix timestamp (milliseconds) of when the Subscription Item ended.            |
| <a id="id"></a> `id`                      | `string`                                                                                                                 | The unique identifier for the Subscription Item.                                  |
| <a id="isfreetrial"></a> `isFreeTrial?`   | `boolean`                                                                                                                | Whether this Subscription Item is currently in a free trial period.               |
| <a id="lifetimepaid"></a> `lifetimePaid?` | [BillingMoneyAmount](https://clerk.com/docs/reference/types/billing-money-amount.md)                                     | The lifetime amount paid for this Subscription Item.                              |
| <a id="nextpayment"></a> `nextPayment`    | `undefined | null | { amount: number; date: number; }`                                                        | Information about the next scheduled payment for this Subscription Item.          |
| `nextPayment.amount`                      | `number`                                                                                                                 | The amount of the next payment.                                                   |
| `nextPayment.date`                        | `number`                                                                                                                 | The Unix timestamp (milliseconds) of when the next payment is scheduled.          |
| <a id="pastdueat"></a> `pastDueAt`        | `null | number`                                                                                               | The Unix timestamp (milliseconds) of when the Subscription Item became past due.  |
| <a id="payerid"></a> `payerId`            | `undefined | string`                                                                                          | The ID of the payer for this Subscription Item.                                   |
| <a id="periodend"></a> `periodEnd`        | `null | number`                                                                                               | The Unix timestamp (milliseconds) of when the current period ends.                |
| <a id="periodstart"></a> `periodStart`    | `number`                                                                                                                 | The Unix timestamp (milliseconds) of when the current period starts.              |
| <a id="plan"></a> `plan`                  | <code>null | <a href="billing-plan">BillingPlan</a></code>                                                               | The Plan associated with this Subscription Item.                                  |
| <a id="planid"></a> `planId`              | `null | string`                                                                                               | The ID of the Plan associated with this Subscription Item.                        |
| <a id="planperiod"></a> `planPeriod`      | `"month" | "annual"`                                                                                          | The period of the Plan associated with this Subscription Item.                    |
| <a id="status"></a> `status`              | `BillingSubscriptionItemStatus`                                                                                          | The status of the Subscription Item.                                              |
| <a id="updatedat"></a> `updatedAt`        | `number`                                                                                                                 | The Unix timestamp (milliseconds) of when the Subscription Item was last updated. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
