# <RedirectToSignIn />

The `<RedirectToSignIn />` component will navigate to the sign in URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: pages/index.tsx
```tsx
import { Show, RedirectToSignIn, UserButton } from '@clerk/react'

export default function Page() {
  return (
    <>
      <Show when="signed-in">
        <UserButton />
      </Show>
      <Show when="signed-out">
        <RedirectToSignIn />
      </Show>
    </>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
