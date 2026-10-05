# <RedirectToSignIn /> component

The `<RedirectToSignIn />` component will navigate to the sign in URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: src/App.tsx
```tsx
import { Show, RedirectToSignIn, UserButton } from '@clerk/electron/react'

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

> In Electron, `<RedirectToSignIn />` navigates to `signInUrl`, which defaults to the Account Portal, and the Account Portal can't return to an Electron window. Set `signInUrl` on [<ClerkProvider>](https://clerk.com/docs/electron/reference/components/clerk-provider.md) to a renderer route that renders `<SignIn />`. If you use a client-side router, pass `routerPush` and `routerReplace` too.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
