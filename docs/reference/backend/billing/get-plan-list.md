# getPlanList()

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

Gets the list of Billing Plans for the instance. By default, the list is returned in descending order by creation date (newest first).

Returns a [`PaginatedResourceResponse`](https://clerk.com/docs/reference/backend/types/paginated-resource-response.md) object with a `data` property containing an array of [`BillingPlan`](https://clerk.com/docs/reference/backend/types/billing-plan.md) objects and a `totalCount` property containing the total number of Billing Plans for the instance.

```typescript
function getPlanList(params?: GetPlanListParams): Promise<PaginatedResourceResponse<BillingPlan[]>>
```

## `GetPlanListParams`

| Property                      | Type                        | Description                                                                                                                                                                            |
| ----------------------------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="limit"></a> `limit?`   | `number`                    | Maximum number of items returned per request. Must be an integer greater than zero and less than `501`. Can be used for paginating the results together with offset. Defaults to `10`. |
| <a id="offset"></a> `offset?` | `number`                    | Skip the first `offset` items when paginating. Needs to be an integer greater or equal to zero. To be used in conjunction with `limit`. Defaults to `0`.                               |
| `payerType`                   | `"org" | "user"` | Filters plans by the type of payer.                                                                                                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const { data, totalCount } = await clerkClient.billing.getPlanList({ payerType: 'org' })
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET /billing/plans`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/billing/GET/billing/plans){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
