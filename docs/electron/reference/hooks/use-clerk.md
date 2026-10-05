# useClerk()

> This hook should only be used for advanced use cases, such as building a completely custom OAuth flow or as an escape hatch to access to the `Clerk` object.

The `useClerk()` hook provides access to the [Clerk](https://clerk.com/docs/electron/reference/objects/clerk.md) object, allowing you to build alternatives to any Clerk Component.

## Returns

[Clerk](https://clerk.com/docs/electron/reference/objects/clerk.md) — The `useClerk()` hook returns the `Clerk` object, which includes all the methods and properties listed in the [Clerk reference](https://clerk.com/docs/electron/reference/objects/clerk.md).

## Example

The following example uses the [useClerk()](https://clerk.com/docs/electron/reference/hooks/use-clerk.md) hook to access the `clerk` object. The `clerk` object is used to call the [openSignIn()](https://clerk.com/docs/electron/reference/objects/clerk.md#opensignin) method to open the sign-in modal.

filename: src/App.tsx
```tsx
import { useClerk } from '@clerk/electron/react'

export default function Example() {
  const clerk = useClerk()

  return <button onClick={() => clerk.openSignIn({})}>Sign in</button>
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
