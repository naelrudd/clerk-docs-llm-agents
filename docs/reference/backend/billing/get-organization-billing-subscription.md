# getOrganizationBillingSubscription()

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

Gets the [`BillingSubscription`](https://clerk.com/docs/reference/backend/types/billing-subscription.md) for the given Organization.

```typescript
function getOrganizationBillingSubscription(organizationId: string): Promise<BillingSubscription>
```

## Parameters

| Parameter        | Type     | Description                                                     |
| ---------------- | -------- | --------------------------------------------------------------- |
| `organizationId` | `string` | The ID of the Organization to get the Billing Subscription for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'

const subscription = await clerkClient.billing.getOrganizationBillingSubscription(organizationId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET /organizations/{organization_id}/billing/subscription`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/billing/GET/organizations/%7Borganization_id%7D/billing/subscription){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
