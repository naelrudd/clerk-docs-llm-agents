# Billing object

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=react) documentation.

The `Billing` object provides methods for managing billing for a user or Organization.

> If an `orgId` parameter is not provided, the methods will automatically use the current user's ID.

## Methods

### `getCreditBalance()`

Gets the credit balance for the current payer.

Returns a [BillingCreditBalanceResource](https://clerk.com/docs/react/reference/types/billing-credit-balance-resource.md) object.

```typescript
function getCreditBalance(params: GetCreditBalanceParams): Promise<BillingCreditBalanceResource>
```

#### `GetCreditBalanceParams`

| Property                    | Type     | Description                                               |
| --------------------------- | -------- | --------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string` | The ID of the Organization to get the credit balance for. |

### `getCreditHistory()`

Gets the credit history for the current payer.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [BillingCreditLedgerResource](https://clerk.com/docs/react/reference/types/billing-credit-ledger-resource.md) objects.

```typescript
function getCreditHistory(params: GetCreditHistoryParams): Promise<ClerkPaginatedResponse<BillingCreditLedgerResource>>
```

#### `GetCreditHistoryParams`

| Property                    | Type     | Description                                               |
| --------------------------- | -------- | --------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string` | The ID of the Organization to get the credit history for. |

### `getPaymentAttempt()`

Gets details of a specific payment attempt for the current user or supplied Organization.

Returns a [BillingPaymentResource](https://clerk.com/docs/react/reference/types/billing-payment-resource.md) object.

```typescript
function getPaymentAttempt(params: GetPaymentAttemptParams): Promise<BillingPaymentResource>
```

#### `GetPaymentAttemptParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                    | `string` | The unique identifier for the payment attempt to get.                                                                                                               |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="orgid"></a> `orgId?`             | `string` | The Organization ID to perform the request on.                                                                                                                      |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getPaymentAttempt()` method.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getPaymentAttempt() method
  const paymentAttempt = await clerk.billing.getPaymentAttempt({
    id: 'payment_attempt_123',
  })

  return <pre>{JSON.stringify(paymentAttempt, null, 2)}</pre>
}
```

### `getPaymentAttempts()`

Gets a list of payment attempts for the current user or supplied Organization.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [BillingPaymentResource](https://clerk.com/docs/react/reference/types/billing-payment-resource.md) objects.

```typescript
function getPaymentAttempts(params: GetPaymentAttemptsParams): Promise<ClerkPaginatedResponse<BillingPaymentResource>>
```

#### `GetPaymentAttemptsParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="orgid"></a> `orgId?`             | `string` | The Organization ID to perform the request on.                                                                                                                      |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getPaymentAttempts()` method.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getPaymentAttempts() method
  const paymentAttempts = await clerk.billing.getPaymentAttempts()

  return <pre>{JSON.stringify(paymentAttempts, null, 2)}</pre>
}
```

You can also use the `usePaymentAttempts()` hook for a simpler way to get the payment attempts.

filename: src/pages/billing/PaymentAttemptsList.tsx
```tsx
import { usePaymentAttempts } from '@clerk/react/experimental'

export default function PaymentAttemptsList() {
  const { data, isLoading } = usePaymentAttempts({
    for: 'user',
    pageSize: 10,
  })

  if (isLoading) {
    return <div>Loading payment attempts...</div>
  }

  if (!data || data.length === 0) {
    return <div>No payment attempts found.</div>
  }

  return (
    <ul>
      {data?.map((attempt) => (
        <li key={attempt.id}>
          Payment #{attempt.id} - {attempt.status}
          <br />
          Amount: {attempt.amount.amountFormatted} on {new Date(attempt.updatedAt).toLocaleString()}
        </li>
      ))}
    </ul>
  )
}
```

### `getPlan()`

Gets a given Billing Plan.

Returns a [BillingPlanResource](https://clerk.com/docs/react/reference/types/billing-plan-resource.md) object.

```typescript
function getPlan(params: GetPlanParams): Promise<BillingPlanResource>
```

#### `GetPlanParams`

| Property             | Type     | Description                        |
| -------------------- | -------- | ---------------------------------- |
| <a id="id"></a> `id` | `string` | The ID of the Billing Plan to get. |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getPlan()` method.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getPlan() method
  const plan = await clerk.billing.getPlan({
    id: 'plan_123',
  })

  return <pre>{JSON.stringify(plan, null, 2)}</pre>
}
```

### `getPlans()`

Gets a list of all publically visible Billing Plans.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [BillingPlanResource](https://clerk.com/docs/react/reference/types/billing-plan-resource.md) objects.

```typescript
function getPlans(params?: GetPlansParams): Promise<ClerkPaginatedResponse<BillingPlanResource>>
```

#### `GetPlansParams`

| Property                                | Type                                 | Description                                                                                                                                                                                                                          |
| --------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `for?`                                  | `"user" | "organization"` | The type of payer for the Plans.                                                                                                                                                                                                     |
| <a id="initialpage"></a> `initialPage?` | `number`                             | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`.                                                                  |
| `minSeats?`                             | `number`                             | The minimum number of seats that the returned plans needs to support.                                                                                                                                                                |
| `orgId?`                                | `string`                             | The organization ID to fetch plans for (needs to match the current Active Organization ID). Providing this parameter will populate the `availablePrices` field with the prices that are available to the authenticated organization. |
| <a id="pagesize"></a> `pageSize?`       | `number`                             | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                                                                                          |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getPlans()` method.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getPlans() method
  const plans = await clerk.billing.getPlans()

  return <pre>{JSON.stringify(plans, null, 2)}</pre>
}
```

You can also use the [usePlans()](https://clerk.com/docs/react/reference/hooks/use-plans.md) hook for a simpler way to get the Plans.

filename: src/pages/billing/PlansList.tsx
```tsx
import { usePlans } from '@clerk/react/experimental'

export default function PlansList() {
  const { data, isLoading, hasNextPage, fetchNext, hasPreviousPage, fetchPrevious } = usePlans({
    for: 'user',
    pageSize: 10,
  })

  if (isLoading) {
    return <div>Loading plans...</div>
  }

  return (
    <ul>
      {data?.map((plan) => (
        <li key={plan.id}>
          <h3>{plan.name}</h3>
          <p>{plan.description}</p>
          <p>Is free plan: {!plan.hasBaseFee ? 'Yes' : 'No'}</p>
          <p>
            Price per month: {plan.currency} {plan.amountFormatted}
          </p>
          <p>
            Price per year: {plan.currency} {plan.annualAmountFormatted} equivalent to{' '}
            {plan.currency} {plan.annualMonthlyAmountFormatted} per month
          </p>
          <h4>Features:</h4>
          <ul>
            {plan.features.map((feature) => (
              <li key={feature.id}>{feature.name}</li>
            ))}
          </ul>
        </li>
      ))}

      {hasNextPage && <button onClick={() => fetchNext()}>Next</button>}
      {hasPreviousPage && <button onClick={() => fetchPrevious()}>Previous</button>}
    </ul>
  )
}
```

### `getStatement()`

Gets a given Billing Statement.

Returns a [BillingStatementResource](https://clerk.com/docs/react/reference/types/billing-statement-resource.md) object.

```typescript
function getStatement(params: GetStatementParams): Promise<BillingStatementResource>
```

#### `GetStatementParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                                    | `string` | The ID of the statement to get.                                                                                                                                     |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="orgid"></a> `orgId?`             | `string` | The Organization ID to perform the request on.                                                                                                                      |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getStatement()` method.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getStatement() method
  const statement = await clerk.billing.getStatement({
    id: 'statement_123',
  })

  return <pre>{JSON.stringify(statement, null, 2)}</pre>
}
```

### `getStatements()`

Gets a list of Billing Statements for the current user or supplied Organization.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [BillingStatementResource](https://clerk.com/docs/react/reference/types/billing-statement-resource.md) objects.

```typescript
function getStatements(params: GetStatementsParams): Promise<ClerkPaginatedResponse<BillingStatementResource>>
```

#### `GetStatementsParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="orgid"></a> `orgId?`             | `string` | The Organization ID to perform the request on.                                                                                                                      |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getStatements()` method.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getStatements() method
  const statements = await clerk.billing.getStatements()

  return <pre>{JSON.stringify(statements, null, 2)}</pre>
}
```

You can also use the [useStatements()](https://clerk.com/docs/react/reference/hooks/use-statements.md) hook for a simpler way to get the statements.

filename: src/pages/billing/StatementsList.tsx
```tsx
import { useStatements } from '@clerk/react/experimental'

export default function StatementsList() {
  const { data, isLoading } = useStatements({
    for: 'user',
    pageSize: 10,
  })

  if (isLoading) {
    return <div>Loading statements...</div>
  }

  if (!data || data.length === 0) {
    return <div>No statements found.</div>
  }

  return (
    <ul>
      {data?.map((statement) => (
        <li key={statement.id}>
          Statement ID: {statement.id} - {statement.status}
          <br />
          Date: {statement.timestamp.toLocaleDateString()}
        </li>
      ))}
    </ul>
  )
}
```

### `getSubscription()`

Gets the main Billing Subscription for the current user or supplied Organization.

Returns a [BillingSubscriptionResource](https://clerk.com/docs/react/reference/types/billing-subscription-resource.md) object.

```typescript
function getSubscription(params: GetSubscriptionParams): Promise<BillingSubscriptionResource>
```

#### `GetSubscriptionParams`

| Property                    | Type     | Description                                                             |
| --------------------------- | -------- | ----------------------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string` | The unique identifier for the Organization to get the subscription for. |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `getSubscription()` method.

> You can also use the `useSubscription()` hook for a simpler way to manage subscriptions. See the [reference documentation](https://clerk.com/docs/react/reference/hooks/use-subscription.md) for more information.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the getSubscription() method
  const subscription = await clerk.billing.getSubscription({
    orgId: 'org_123',
  })

  return <pre>{JSON.stringify(subscription, null, 2)}</pre>
}
```

### `startCheckout()`

Creates a new Billing checkout for the current user or supplied Organization.

Returns a [BillingCheckoutResource](https://clerk.com/docs/react/reference/types/billing-checkout-resource.md) object.

```typescript
function startCheckout(params: CreateCheckoutParams): Promise<BillingCheckoutResource>
```

#### `CreateCheckoutParams`

| Property                    | Type                            | Description                                                                                             |
| --------------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string`                        | The Organization ID to perform the request on.                                                          |
| `planId`                    | `string`                        | The unique identifier for the Plan.                                                                     |
| `planPeriod`                | `"month" | "annual"` | The billing period for the Plan.                                                                        |
| `priceId?`                  | `string`                        | The specific price ID to check out for, used when the desired price ID is not the current default price |
| `seatsQuantity?`            | `number`                        | The number of total seats to check out for                                                              |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/react/reference/objects/clerk.md) object. Use the [useClerk()](https://clerk.com/docs/react/reference/hooks/use-clerk.md) hook to access the `clerk.billing` object, and then call the `startCheckout()` method.

> You can also use the `useCheckout()` hook for a simpler way to start a checkout. See the [reference documentation](https://clerk.com/docs/react/reference/hooks/use-checkout.md) for more information.

filename: src/pages/Example.tsx
```tsx
import { useClerk } from '@clerk/react'

export default async function Example() {
  // Use the useClerk hook to access the clerk object
  const clerk = useClerk()

  // Call the startCheckout() method
  const checkout = await clerk.billing.startCheckout({
    planId: 'plan_123',
    planPeriod: 'month',
  })

  return <pre>{JSON.stringify(checkout, null, 2)}</pre>
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
