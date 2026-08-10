# The Backend BillingSubscriptionItemStatus object

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

The possible lifecycle states of a Backend `BillingSubscriptionItem`.

## Properties

| Property                             | Type           | Description                                      |
| ------------------------------------ | -------------- | ------------------------------------------------ |
| <a id="abandoned"></a> `abandoned`   | `"abandoned"`  | The Subscription Item is in the abandoned state. |
| <a id="active"></a> `active`         | `"active"`     | The Subscription Item is active.                 |
| <a id="canceled"></a> `canceled`     | `"canceled"`   | The Subscription Item is canceled.               |
| <a id="ended"></a> `ended`           | `"ended"`      | The Subscription Item has ended.                 |
| <a id="expired"></a> `expired`       | `"expired"`    | The Subscription Item has expired.               |
| <a id="incomplete"></a> `incomplete` | `"incomplete"` | The Subscription Item is incomplete.             |
| <a id="pastdue"></a> `past_due`      | `"past_due"`   | The Subscription Item has a past-due payment.    |
| <a id="upcoming"></a> `upcoming`     | `"upcoming"`   | The Subscription Item is upcoming.               |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
