# BillingSubscriptionItemSeats

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=js-frontend) documentation.

The `BillingSubscriptionItemSeats` type represents seat entitlements attached to a subscription item.

## Properties

| Property                         | Type                                                                                                                                   | Description                                                                                  |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| <a id="quantity"></a> `quantity` | `null | number`                                                                                                             | The seat limit active while the parent subscription item was active. `null` means unlimited. |
| <a id="tiers"></a> `tiers?`      | <code><a href="https://clerk.com/docs/js-frontend/reference/types/billing-per-unit-total-tier.md">BillingPerUnitTotalTier</a>[]</code> | The tier-level breakdown of seats for this subscription item.                                |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
