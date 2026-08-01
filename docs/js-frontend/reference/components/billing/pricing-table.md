# <PricingTable />

The `<PricingTable />` component displays a table of Plans and Features that users can subscribe to.

## Usage with JavaScript

The following methods available on an instance of the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) class are used to render and control the `<PricingTable />` component:

- [mountPricingTable()](https://clerk.com/docs/js-frontend/reference/components/billing/pricing-table.md#mount-pricing-table)
- [unmountPricingTable()](https://clerk.com/docs/js-frontend/reference/components/billing/pricing-table.md#unmount-pricing-table)

The following examples assume that you followed the [quickstart](https://clerk.com/docs/js-frontend/getting-started/quickstart.md) to add Clerk to your JavaScript app.

### `mountPricingTable()`

```typescript
function mountPricingTable(node: HTMLDivElement, props?: PricingTableProps): void
```

#### `mountPricingTable()` params

| Name   | Type              | Description                                                                    |
| ------ | ----------------- | ------------------------------------------------------------------------------ |
| node   | HTMLDivElement    | The container <div> element used to render in the <PricingTable /> component |
| props? | PricingTableProps | The properties to pass to the <PricingTable /> component                      |

#### `mountPricingTable()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

// Initialize Clerk with your Clerk Publishable Key
const clerkPubKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

const clerk = new Clerk(clerkPubKey)
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="pricing-table"></div>
`

const pricingTableDiv = document.getElementById('pricing-table')

clerk.mountPricingTable(pricingTableDiv)
```

### `unmountPricingTable()`

```typescript
function unmountPricingTable(node: HTMLDivElement): void
```

#### `unmountPricingTable()` params

| Name | Type           | Description                                                                       |
| ---- | -------------- | --------------------------------------------------------------------------------- |
| node | HTMLDivElement | The container <div> element with a rendered <PricingTable /> component instance |

#### `unmountPricingTable()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

// Initialize Clerk with your Clerk Publishable Key
const clerkPubKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY

const clerk = new Clerk(clerkPubKey)
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="pricing-table"></div>
`

const pricingTableDiv = document.getElementById('pricing-table')

clerk.mountPricingTable(pricingTableDiv)

// ...

clerk.unmountPricingTable(pricingTableDiv)
```

## Properties

All props are optional.

| Name                                                                                                                 | Type                     | Description                                                                                                                                                                                                                                                                                                                  |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| appearance?                                                                                                          | Appearance | undefined  | An object to style your components. Will only affect Clerk components and not Account Portal pages.                                                                                                                                                                                                                          |
| appearance: an object used to style your components. Will only affect Clerk components and not Account Portal pages. |                          |                                                                                                                                                                                                                                                                                                                              |
| collapseFeatures?                                                                                                    | boolean                  | A boolean that indicates whether the Features are collapsed. Requires layout to be set to 'default'. Defaults to false.                                                                                                                                                                                                      |
| ctaPosition?                                                                                                         | 'top' | 'bottom'        | The placement of the CTA button. Requires layout to be set to 'default'. Defaults to 'bottom'.                                                                                                                                                                                                                               |
| fallback?                                                                                                            | JSX                      | An element to be rendered while the component is mounting.                                                                                                                                                                                                                                                                   |
| for?                                                                                                                 | 'user' | 'organization' | A string that indicates whether the pricing table is for users or Organizations. If 'user', the pricing table will display a list of Plans and Features that users can subscribe to. If 'organization', the pricing table will display a list of Plans and Features that Organizations can subscribe to. Defaults to 'user'. |
| highlightedPlan?                                                                                                     | string                   | The slug of the Plan to highlight. When set, the matching Plan card will display a "Popular" badge. If the Plan already has an active Subscription badge, the Subscription badge takes priority.                                                                                                                             |
| newSubscriptionRedirectUrl?                                                                                          | string                   | The URL to navigate to after the user completes the checkout and selects the "Continue" button.                                                                                                                                                                                                                              |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
