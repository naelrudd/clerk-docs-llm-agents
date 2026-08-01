# <RedirectToSignIn />

The `<RedirectToSignIn />` component will navigate to the sign in URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: app/routes/index.tsx
```tsx
import { Show, RedirectToSignIn, UserButton } from '@clerk/tanstack-react-start'
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/')({
  component: Home,
})

function Home() {
  return (
    <div>
      <Show when="signed-in">
        <UserButton />
      </Show>
      <Show when="signed-out">
        <RedirectToSignIn />
      </Show>
    </div>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
