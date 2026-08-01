# <RedirectToCreateOrganization /> (deprecated)

> This feature is deprecated. Please use the [redirectToCreateOrganization() method](https://clerk.com/docs/tanstack-react-start/reference/objects/clerk.md#redirect-to-create-organization) instead.

The `<RedirectToCreateOrganization />` component will navigate to the create Organization flow which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: app/routes/index.tsx
```tsx
import { Show, RedirectToCreateOrganization } from '@clerk/tanstack-react-start'
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/')({
  component: Home,
})

function Home() {
  return (
    <div>
      <Show when="signed-in">
        <RedirectToCreateOrganization />
      </Show>
      <Show when="signed-out">
        <p>You need to sign in to create an Organization.</p>
      </Show>
    </div>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
