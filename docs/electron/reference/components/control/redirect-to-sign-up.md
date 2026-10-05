# <RedirectToSignUp /> component

The `<RedirectToSignUp />` component will navigate to the sign up URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

filename: src/App.tsx
```tsx
import { Show, RedirectToSignUp, UserButton } from '@clerk/electron/react'

export default function Page() {
  return (
    <>
      <Show when="signed-in">
        <UserButton />
      </Show>
      <Show when="signed-out">
        <RedirectToSignUp />
      </Show>
    </>
  )
}
```

> In Electron, `<RedirectToSignUp />` navigates to `signUpUrl`, which defaults to the Account Portal, and the Account Portal can't return to an Electron window. Set `signUpUrl` on [<ClerkProvider>](https://clerk.com/docs/electron/reference/components/clerk-provider.md) to a renderer route that renders `<SignUp />`. If you use a client-side router, pass `routerPush` and `routerReplace` too.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
