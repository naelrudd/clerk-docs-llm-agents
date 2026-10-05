# <RedirectToCreateOrganization /> component (Deprecated)

> **Deprecated:** This feature is deprecated. Please use the [redirectToCreateOrganization() method](https://clerk.com/docs/electron/reference/objects/clerk.md#redirecttocreateorganization) instead.

The `<RedirectToCreateOrganization />` component will navigate to the create Organization flow which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: src/App.tsx
```tsx
import { Show, RedirectToCreateOrganization } from '@clerk/electron/react'

export default function Page() {
  return (
    <>
      <Show when="signed-in">
        <RedirectToCreateOrganization />
      </Show>
      <Show when="signed-out">You need to sign in to create an Organization.</Show>
    </>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
