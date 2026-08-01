# <RedirectToUserProfile /> (deprecated)

> This feature is deprecated. Please use the [redirectToUserProfile() method](https://clerk.com/docs/nextjs/reference/objects/clerk.md#redirect-to-user-profile) instead.

The `<RedirectToUserProfile />` component will navigate to the Account Portal User Profile URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

To find your User Profile URL:

1. In the Clerk Dashboard, navigate to the [**Account Portal**](https://dashboard.clerk.com/~/account-portal) page.
2. Under **User profile**, select the **Visit** icon.

## Example

filename: app/page.tsx
```tsx
import { Show, RedirectToUserProfile } from '@clerk/nextjs'

function Page() {
  return (
    <>
      <Show when="signed-in">
        <RedirectToUserProfile />
      </Show>
      <Show when="signed-out">
        <p>You need to sign in to view your user profile.</p>
      </Show>
    </>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
