# <RedirectToSignIn />

The `<RedirectToSignIn />` component will navigate to the sign in URL which has been configured in your application instance. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

## Example

> This component relies on React Router for navigation. Ensure that you have integrated React Router into your Chrome Extension application before using it. Learn how to [add React Router to your Chrome Extension](https://clerk.com/docs/guides/development/add-react-router.md?sdk=chrome-extension).

filename: src/routes/home.tsx
```jsx
import { Show, RedirectToSignIn, UserButton } from '@clerk/chrome-extension'

export default function Home() {
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
