# Billing object

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=js-frontend) documentation.

The `Billing` object provides methods for managing billing for a user or Organization.

> If an `orgId` parameter is not provided, the methods will automatically use the current user's ID.

## Methods

### `getCreditBalance()`

Gets the credit balance for the current payer.

Returns a [BillingCreditBalanceResource](https://clerk.com/docs/js-frontend/reference/types/billing-credit-balance-resource.md) object.

```typescript
function getCreditBalance(params: GetCreditBalanceParams): Promise<BillingCreditBalanceResource>
```

#### `GetCreditBalanceParams`

| Property                    | Type     | Description                                               |
| --------------------------- | -------- | --------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string` | The ID of the Organization to get the credit balance for. |

### `getCreditHistory()`

Gets the credit history for the current payer.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/js-frontend/reference/types/clerk-paginated-response.md) of [BillingCreditLedgerResource](https://clerk.com/docs/js-frontend/reference/types/billing-credit-ledger-resource.md) objects.

```typescript
function getCreditHistory(params: GetCreditHistoryParams): Promise<ClerkPaginatedResponse<BillingCreditLedgerResource>>
```

#### `GetCreditHistoryParams`

| Property                    | Type     | Description                                               |
| --------------------------- | -------- | --------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string` | The ID of the Organization to get the credit history for. |

### `getPaymentAttempt()`

Gets details of a specific payment attempt for the current user or supplied Organization.

Returns a [BillingPaymentResource](https://clerk.com/docs/js-frontend/reference/types/billing-payment-resource.md) object.

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

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getPaymentAttempt() method
await clerk.billing.getPaymentAttempt({
  id: 'payment_attempt_123',
})
```

### `getPaymentAttempts()`

Gets a list of payment attempts for the current user or supplied Organization.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/js-frontend/reference/types/clerk-paginated-response.md) of [BillingPaymentResource](https://clerk.com/docs/js-frontend/reference/types/billing-payment-resource.md) objects.

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

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getPaymentAttempts() method
await clerk.billing.getPaymentAttempts()
```

### `getPlan()`

Gets a given Billing Plan.

Returns a [BillingPlanResource](https://clerk.com/docs/js-frontend/reference/types/billing-plan-resource.md) object.

```typescript
function getPlan(params: GetPlanParams): Promise<BillingPlanResource>
```

#### `GetPlanParams`

| Property             | Type     | Description                        |
| -------------------- | -------- | ---------------------------------- |
| <a id="id"></a> `id` | `string` | The ID of the Billing Plan to get. |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getPlan() method
await clerk.billing.getPlan({
  id: 'plan_123',
})
```

### `getPlans()`

Gets a list of all publically visible Billing Plans.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/js-frontend/reference/types/clerk-paginated-response.md) of [BillingPlanResource](https://clerk.com/docs/js-frontend/reference/types/billing-plan-resource.md) objects.

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

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getPlans() method
await clerk.billing.getPlans()
```

### `getStatement()`

Gets a given Billing Statement.

Returns a [BillingStatementResource](https://clerk.com/docs/js-frontend/reference/types/billing-statement-resource.md) object.

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

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getStatement() method
await clerk.billing.getStatement({
  id: 'statement_123',
})
```

### `getStatements()`

Gets a list of Billing Statements for the current user or supplied Organization.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/js-frontend/reference/types/clerk-paginated-response.md) of [BillingStatementResource](https://clerk.com/docs/js-frontend/reference/types/billing-statement-resource.md) objects.

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

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getStatements() method
await clerk.billing.getStatements()
```

### `getSubscription()`

Gets the main Billing Subscription for the current user or supplied Organization.

Returns a [BillingSubscriptionResource](https://clerk.com/docs/js-frontend/reference/types/billing-subscription-resource.md) object.

```typescript
function getSubscription(params: GetSubscriptionParams): Promise<BillingSubscriptionResource>
```

#### `GetSubscriptionParams`

| Property                    | Type     | Description                                                             |
| --------------------------- | -------- | ----------------------------------------------------------------------- |
| <a id="orgid"></a> `orgId?` | `string` | The unique identifier for the Organization to get the subscription for. |

#### Example

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the getSubscription() method
await clerk.billing.getSubscription({
  orgId: 'org_123',
})
```

### `startCheckout()`

Creates a new Billing checkout for the current user or supplied Organization.

Returns a [BillingCheckoutResource](https://clerk.com/docs/js-frontend/reference/types/billing-checkout-resource.md) object.

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

The `Billing` object is available on the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) object.

filename: src/main.js
```js
import { Clerk } from '@clerk/clerk-js'

const publishableKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk(publishableKey)

// Load Clerk
await clerk.load()

// Call the startCheckout() method
await clerk.billing.startCheckout({
  planId: 'plan_123',
  planPeriod: 'month',
})
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
