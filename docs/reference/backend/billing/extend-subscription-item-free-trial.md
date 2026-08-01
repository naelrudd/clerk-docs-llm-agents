# extendSubscriptionItemFreeTrial()

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

Extends the free trial for the given Subscription Item.

Returns the updated [`BillingSubscriptionItem`](https://clerk.com/docs/reference/backend/types/billing-subscription-item.md) object.

```typescript
function extendSubscriptionItemFreeTrial(subscriptionItemId: string, params: { extendTo: Date }): Promise<BillingSubscriptionItem>
```

## Parameters

| Parameter            | Type                             | Description                                                                                                             |
| -------------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| `subscriptionItemId` | `string`                         | The ID of the Subscription Item to extend the free trial for.                                                           |
| `params`             | `{ extendTo: Date; }` | The parameters for the request.                                                                                         |
| `params.extendTo`    | `Date`                           | The date to extend the free trial to. Must be in the future and not more than 365 days from the current trial end date. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.billing.extendSubscriptionItemFreeTrial('subi_123', {
  extendTo: new Date('2026-12-31'),
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST /billing/subscription_items/{subscription_item_id}/extend_free_trial`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/billing/POST/billing/subscription_items/%7Bsubscription_item_id%7D/extend_free_trial){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
