# Backend BillingSubscription object

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

The `BillingSubscription` object is similar to the [BillingSubscriptionResource](https://clerk.com/docs/reference/types/billing-subscription-resource.md) object as it holds information about a subscription, as well as methods for managing it. However, the `BillingSubscription` object is different in that it is used in the [Backend API](https://clerk.com/docs/reference/backend-api/tag/billing/GET/organizations/%7Borganization_id%7D/billing/subscription){{ target: '_blank' }} and is not directly accessible from the Frontend API.

## Properties

| Property                                                 | Type                                                                                                                                           | Description                                                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| <a id="activeat"></a> `activeAt`                         | `null | number`                                                                                                                     | The Unix timestamp (milliseconds) of when the Subscription became active.    |
| <a id="createdat"></a> `createdAt`                       | `number`                                                                                                                                       | The Unix timestamp (milliseconds) of when the Subscription was created.      |
| <a id="eligibleforfreetrial"></a> `eligibleForFreeTrial` | `boolean`                                                                                                                                      | Whether the payer is eligible for a free trial.                              |
| <a id="id"></a> `id`                                     | `string`                                                                                                                                       | The unique identifier for the Subscription.                                  |
| <a id="nextpayment"></a> `nextPayment`                   | <code>null | { amount: <a href="https://clerk.com/docs/reference/types/billing-money-amount.md">BillingMoneyAmount</a>; date: number; }</code> | Information about the next scheduled payment for this Subscription.          |
| `nextPayment.amount`                                     | [BillingMoneyAmount](https://clerk.com/docs/reference/types/billing-money-amount.md)                                                           | The amount of the next payment.                                              |
| `nextPayment.date`                                       | `number`                                                                                                                                       | The Unix timestamp (milliseconds) of when the next payment is scheduled.     |
| <a id="pastdueat"></a> `pastDueAt`                       | `null | number`                                                                                                                     | The Unix timestamp (milliseconds) of when the Subscription became past due.  |
| <a id="payerid"></a> `payerId`                           | `string`                                                                                                                                       | The ID of the payer for this Subscription.                                   |
| <a id="status"></a> `status`                             | `"abandoned" | "active" | "ended" | "canceled" | "incomplete" | "past_due"`                                                         | The current status of the Subscription.                                      |
| <a id="subscriptionitems"></a> `subscriptionItems`       | <code><a href="billing-subscription-item">BillingSubscriptionItem</a>[]</code>                                                                 | All of the Subscription Items in this Subscription.                          |
| <a id="updatedat"></a> `updatedAt`                       | `number`                                                                                                                                       | The Unix timestamp (milliseconds) of when the Subscription was last updated. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
