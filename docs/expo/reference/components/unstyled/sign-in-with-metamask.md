# <SignInWithMetamaskButton>

The `<SignInWithMetamaskButton>` component is used to complete a one-click, cryptographically-secure sign-in flow using MetaMask.

## Usage

### Basic usage

> This component is for Expo web projects. For native iOS and Android apps, use the [native components](https://clerk.com/docs/expo/reference/expo/native-components/overview.md) from `@clerk/expo/native` instead.

filename: src/app/page.web.tsx
```jsx
import { SignInWithMetamaskButton } from '@clerk/expo/web'

export default function Home() {
  return <SignInWithMetamaskButton />
}
```

### Custom usage

In some cases, you will want to use your own button, or button text. You can do that by wrapping your button in the `<SignInWithMetamaskButton>` component.

> This component is for Expo web projects. For native iOS and Android apps, use the [native components](https://clerk.com/docs/expo/reference/expo/native-components/overview.md) from `@clerk/expo/native` instead.

filename: src/app/page.web.tsx
```jsx
import { SignInWithMetamaskButton } from '@clerk/expo/web'

export default function Home() {
  return (
    <SignInWithMetamaskButton mode="modal">
      <button>Custom sign in button</button>
    </SignInWithMetamaskButton>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
