# BillingStatementGroup

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=astro) documentation.

The `BillingStatementGroup` type represents a group of payment items within a statement.

## Properties

| Property                           | Type                                                                                                                         | Description                                                                     |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| <a id="items"></a> `items`         | <code><a href="https://clerk.com/docs/astro/reference/types/billing-payment-resource.md">BillingPaymentResource</a>[]</code> | An array of payment resources that belong to this group.                        |
| <a id="timestamp"></a> `timestamp` | `Date`                                                                                                                       | The date and time when this group of payment items was created or last updated. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
