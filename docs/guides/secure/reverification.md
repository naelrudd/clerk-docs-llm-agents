# Add reverification for sensitive actions

> This feature requires one of the following SDKS:
>
> - `@clerk/nextjs@6.12.7` or later
> - `@clerk/react`, or `@clerk/react@5.25.1` or later
> - `@clerk/clerk-js@5.57.1` or later
> - `@clerk/clerk-sdk-ruby@3.3.0` or later

Reverification allows you to prompt a user to verify their credentials before performing sensitive actions, even if they're already authenticated. For example, in a banking application, transferring money is considered a "sensitive action." Reverification can be used to confirm the user's identity.

Clerk's prebuilt components handle reverification for certain [sensitive actions](#sensitive-actions-that-require-reverification), out of the box. However, this guide will show you how to implement reverification for sensitive actions that are unique to your application.

## Sensitive actions that require reverification

The following table shows the sensitive actions that require reverification along with the required strategy and timeframe for each action. When using Clerk's prebuilt components, reverification is automatically handled for these actions.

| Action                                            | Strategy            | Timeframe |
| ------------------------------------------------- | ------------------- | --------- |
| Update username                                   | Strongest available | 10m       |
| Set/update password                               | Strongest available | 10m       |
| Add/remove email address                          | Strongest available | 10m       |
| Add/remove phone number                           | Strongest available | 10m       |
| Add/remove Web3 Wallet                            | Strongest available | 10m       |
| Add/remove passkey                                | Strongest available | 10m       |
| Set primary identification                        | Strongest available | 10m       |
| Connect/remove external account                   | Strongest available | 10m       |
| Add/remove MFA (TOTP, phone number, backup codes) | Strongest available | 10m       |
| Revoke session                                    | Strongest available | 10m       |
| Delete account                                    | Strongest available | 10m       |

## Caveats

Before enabling this feature, consider the following:

1. **Available factors for reverification**: Not all authentication factors are supported for reverification. Users can only reverify their credentials using the following factors:
   - First factors: password, email code, phone code
   - Second factors: phone code, authenticator app, backup code
2. **Graceful downgrade of verification level**: If you request a `second_factor` or `multi_factor` level of verification but the user lacks a second factor available, the utilities automatically downgrade the requested level to `first_factor`.
3. **Eligibility for sensitive actions**: Users without any of the above factors cannot reverify. This can be an issue for apps that don't require email addresses to sign up or have disabled email codes in favor of email links.

## How to require reverification

If you are performing a sensitive action on the client-side, the [useReverification()](https://clerk.com/docs/reference/hooks/use-reverification.md) hook will check if the user has verified their credentials within 10 minutes (the default) and if not, displays a modal that prompts the user to verify their credentials. See the [reference doc](https://clerk.com/docs/reference/hooks/use-reverification.md) for detailed examples.

If you are performing a sensitive action on the server side, use the [`auth.has()`](https://clerk.com/docs/reference/backend/types/auth-object.md#has) helper to check if the user has verified their credentials within a specific time period. This only does the check on the server side, so **you still need to handle reverification on the client side** in order for your users to be able to verify their credentials.

### Example: Reverification in an API endpoint

> This example is written for Next.js App Router, but can be adapted for any framework/language.

To handle reverification on the server-side, use the [`auth.has()`](https://clerk.com/docs/reference/backend/types/auth-object.md#has) helper to check if the user has verified their credentials within a specific time period. Pass a configuration to set the time period you would like. You can pass one of the following configurations: `strict_mfa`, `strict`, `moderate`, and `lax`. See the [reference doc](https://clerk.com/docs/reference/backend/types/auth-object.md#has) for details on each configuration.

If the user hasn't verified their credentials within that time period, return `reverificationErrorResponse` to trigger the reverification flow.

In the following example, your `/api/reverification-example` endpoint will check if a user has verified their credentials within the past 10 minutes. If they haven't, the endpoint returns the `reverificationErrorResponse` error, which is a `403 Forbidden` error.

filename: app/api/reverification-example/route.ts
```ts
import { auth, reverificationErrorResponse } from '@clerk/nextjs/server'
// If your SDK doesn't export `reverificationErrorResponse`, import it from `@clerk/shared/authorization-errors`
import { NextResponse } from 'next/server'

export const POST = async () => {
  // The `Auth` object gives you access to properties like `isAuthenticated` and `userId`
  // Accessing the `Auth` object differs depending on the SDK you're using
  // https://clerk.com/docs/reference/backend/types/auth-object#how-to-access-the-auth-object
  const { has } = await auth()

  // Check if the user has *not* verified their credentials within the past 10 minutes.
  const shouldUserRevalidate = !has({ reverification: 'strict' })

  // If the user hasn't reverified, return an error with the matching configuration (e.g., `strict`)
  if (shouldUserRevalidate) {
    return reverificationErrorResponse('strict')
  }

  // If the user has verified credentials, return a successful response
  return NextResponse.json({ success: true })
}
```

After setting up reverification on the server-side, you must handle reverification on the client-side so that your users can verify their credentials. Wrap your call to the endpoint in the [useReverification()](https://clerk.com/docs/reference/hooks/use-reverification.md) hook to detect the `reverificationErrorResponse` error and display a modal that allows the user to verify their identity. Upon successful verification, the previously failed request is automatically retried.

In the following example, when the user selects the **Transfer** button, the `transferMoney()` function is called, which in turn calls the API endpoint you set up earlier. In the endpoint, you set up reverification to check if the user has verified their credentials within the past 10 minutes. If they haven't, the endpoint returns a `403 forbidden` error to the client, triggering the `useReverification()` hook to display a modal that allows the user to verify their identity. Once the user completes the reverification in the modal, the previously failed request is automatically retried.

filename: app/transfer/page.tsx
```tsx
'use client'

import { useReverification } from '@clerk/nextjs'

export default function Page({ amount_in_cents }: { amount_in_cents: number }) {
  const transferMoney = useReverification(
    async () =>
      await fetch('/api/reverification-example', {
        method: 'POST',
        body: JSON.stringify({ amount_in_cents }),
      }),
  )

  return <button onClick={transferMoney}>Transfer</button>
}
```

### Example: Reverification in a Server Action

You can also perform a reverification check in a Server Action.

filename: app/actions.ts
```ts
'use server'

import { auth, reverificationError } from '@clerk/nextjs/server'

export const myAction = async () => {
  const { has } = await auth.protect()

  // Check if the user has *not* verified their credentials within the past 10 minutes
  const shouldUserRevalidate = !has({ reverification: 'strict' })

  // If the user hasn't reverified, return an error with the matching configuration (e.g., `strict`)
  if (shouldUserRevalidate) {
    return reverificationError('strict')
  }

  // If the user has verified credentials, return a successful response
  return { success: true }
}
```

Then, wrap your call to the Server Action in the [useReverification()](https://clerk.com/docs/reference/hooks/use-reverification.md) hook to detect the `reverificationError` error and display a modal that allows the user to verify their identity. Upon successful verification, the previously failed request is automatically retried.

filename: app/perform-action/page.tsx
```tsx
'use client'

import { useReverification } from '@clerk/nextjs'
import { myAction } from '../actions'

export default function Page() {
  const performAction = useReverification(myAction)

  const handleClick = async () => {
    const myData = await performAction()
    // If `myData` is null, the user cancelled the reverification process
    // You can choose how your app responds. This example returns null.
    if (!myData) return
  }

  return <button onClick={handleClick}>Perform action</button>
}
```

## Correlate a reverification with a specific action

Some use cases require proving that a single reverification corresponds to exactly one sensitive action — for example, [Strong Customer Authentication (SCA)](https://en.wikipedia.org/wiki/Strong_customer_authentication) for payments, where each payment must be backed by its own verification and a verification can't be replayed across payments. This pattern is useful in scenarios that require dynamic linking.

Clerk tracks every reverification with a unique ID. You can include this ID in your session token by adding the `{{session.reverification_id}}` shortcode as a custom claim. Combined with the default [`fva` (factor verification age)](https://clerk.com/docs/guides/sessions/session-tokens.md) claim, the token gives you two guarantees:

- `reverification_id` provides **uniqueness**: it identifies _which_ reverification the token reflects.
- `fva` provides **freshness**: it conveys how recently the user's factors were verified.

Each time a reverification starts, Clerk mints a new `reverification_id`. Because both claims are part of the signed session token, your backend can confirm `fva` reflects a recent verification and use `reverification_id` to correlate that reverification with a specific action. A typical flow:

1. Add `{{session.reverification_id}}` as a custom claim to your session token. See [Customize your session token](https://clerk.com/docs/guides/sessions/customize-session-tokens.md).
2. When the user initiates a sensitive action, [trigger a reverification](#how-to-require-reverification) so a new reverification ID is minted.
3. On your backend, verify the signed session token, confirm that `fva` is within your required window, and record the `reverification_id` alongside the action's specific details, such as the payment amount and payee.
4. Reject any action whose `reverification_id` has already been used, or whose recorded details don't match the action being performed, ensuring each reverification authorizes exactly one action.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
