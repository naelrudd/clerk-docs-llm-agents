# cancelSubscriptionItem()

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

Cancels the given Subscription Item.

Returns the cancelled [`BillingSubscriptionItem`](https://clerk.com/docs/reference/backend/types/billing-subscription-item.md) object.

```typescript
function cancelSubscriptionItem(subscriptionItemId: string, params?: { endNow?: boolean }): Promise<BillingSubscriptionItem>
```

## Parameters

| Parameter            | Type                               | Description                                                                                                                                                |
| -------------------- | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `subscriptionItemId` | `string`                           | The ID of the Subscription Item to cancel.                                                                                                                 |
| `params?`            | `{ endNow?: boolean; }` | The parameters for the request.                                                                                                                            |
| `params?.endNow?`    | `boolean`                          | Whether the Subscription Item should be canceled immediately. If `false`, the Subscription Item will be canceled at the end of the current billing period. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.billing.cancelSubscriptionItem('subi_123', { endNow: true })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE /billing/subscription_items/{id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/billing/DELETE/billing/subscription_items/%7Bsubscription_item_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
