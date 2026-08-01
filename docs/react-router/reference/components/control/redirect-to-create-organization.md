# <RedirectToCreateOrganization /> (deprecated)

> This feature is deprecated. Please use the [redirectToCreateOrganization() method](https://clerk.com/docs/react-router/reference/objects/clerk.md#redirect-to-create-organization) instead.

The `<RedirectToCreateOrganization />` component will navigate to the create Organization flow which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: app/routes/home.tsx
```tsx
import { Show, RedirectToCreateOrganization } from '@clerk/react-router'

export default function Home() {
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
