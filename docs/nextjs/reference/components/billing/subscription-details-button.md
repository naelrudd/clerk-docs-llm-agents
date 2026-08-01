# <SubscriptionDetailsButton /> component

![The <SubscriptionDetailsButton /> component renders a button that opens the Subscription details drawer.](https://clerk.com/docs/raw/_public/images/ui-components/subscription.svg)

The `<SubscriptionDetailsButton />` component renders a button that opens the Subscription details drawer when selected, allowing users to view and manage their Subscription details, whether for their Personal Account or Organization. It must be wrapped inside a [<Show when="signed-in">](https://clerk.com/docs/nextjs/reference/components/control/show.md) component to ensure the user is authenticated.

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md?sdk=nextjs) documentation.

## Usage

`<SubscriptionDetailsButton />` must be wrapped inside a [<Show when="signed-in">](https://clerk.com/docs/nextjs/reference/components/control/show.md) component to ensure the user is authenticated.

```tsx
<>
  // ❌ This will throw an error
  <SubscriptionDetailsButton />
  // ✅ Correct usage
  <Show when="signed-in">
    <SubscriptionDetailsButton />
  </Show>
</>
```

`<SubscriptionDetailsButton />` will throw an error if the `for` prop is set to `'organization'` and no Active Organization is set.

```tsx
<>
  // ❌ This will throw an error if no Organization is active
  <SubscriptionDetailsButton for="organization" />
  // ✅ Correct usage
  {auth.orgId ? <SubscriptionDetailsButton for="organization" /> : null}
</>
```

### Examples

filename: app/billing/page.tsx
```tsx
'use client'

import { Show } from '@clerk/nextjs'
import { SubscriptionDetailsButton } from '@clerk/nextjs/experimental'

export default function BillingPage() {
  return (
    <Show when="signed-in">
      {/* Basic usage */}
      <SubscriptionDetailsButton />

      {/* Customizes the appearance of the Subscription details drawer */}
      <SubscriptionDetailsButton
        subscriptionDetailsProps={{
          appearance: {
            /* custom theme */
          },
        }}
      />

      {/* Custom button */}
      <SubscriptionDetailsButton onSubscriptionCancel={() => console.log('Subscription canceled')}>
        <button className="custom-button">
          <Icon name="subscription" />
          Manage Subscription
        </button>
      </SubscriptionDetailsButton>
    </Show>
  )
}
```

## Properties

All props are optional.

| Name                                                                                                                                                    | Type                     | Description                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | --------------------------------------------------------------------------------------------------------- |
| for?                                                                                                                                                    | 'user' | 'organization' | Determines whether to show Subscription details for the current user or Organization. Defaults to 'user'. |
| children?                                                                                                                                               | React.ReactNode          | A custom button element. If not provided, defaults to a button with the text "Subscription details".      |
| onSubscriptionCancel?                                                                                                                                   | () => void               | A callback function that is called when a Subscription is cancelled.                                      |
| appearance: an object used to style your components. For example: <SubscriptionDetailsButton subscriptionDetailsProps={{ appearance: { ... } }} />. |                          |                                                                                                           |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
