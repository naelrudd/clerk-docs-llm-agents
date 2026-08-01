# <Waitlist /> component

The `<Waitlist />` component renders a form that allows users to join for early access to your app. Users receive an email confirming their request to join the waitlist. Once [approved](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=js-frontend#manage-users-on-your-waitlist), users receive an email with instructions on how to join your app.

Learn more about [using and customizing **Waitlist** mode](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=js-frontend#waitlist).

## Enable Waitlist mode

Before using the `<Waitlist />` component, you must enable **Waitlist** mode in the Clerk Dashboard.

In [**Waitlist** mode](https://clerk.com/docs/guides/secure/restricting-access.md?sdk=js-frontend#waitlist), users can register their interest in your app by joining a waitlist. Existing users and users who have been approved from the waitlist will be able to sign in to your app, while new users will need to join the waitlist to access your app. This mode is ideal for apps in early development stages or those wanting to generate interest before launch.

> [**Email** must be enabled in the Clerk Dashboard](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=js-frontend#email) to allow waitlist invitation emails to be sent to users after they are approved. Support for sending waitlist invitations when **Email** is disabled is actively being worked on.

To enable **Waitlist** mode:

1. In the Clerk Dashboard, navigate to the [**Waitlist**](https://dashboard.clerk.com/~/user-authentication/waitlist) page.
2. Toggle on **Enable waitlist** and select **Save**.

## Usage with JavaScript

The following methods available on an instance of the [Clerk](https://clerk.com/docs/js-frontend/reference/objects/clerk.md) class are used to render and control the `<Waitlist />` component:

- [mountWaitlist()](https://clerk.com/docs/js-frontend/reference/components/authentication/waitlist.md#mount-waitlist)
- [unmountWaitlist()](https://clerk.com/docs/js-frontend/reference/components/authentication/waitlist.md#unmount-waitlist)
- [openWaitlist()](https://clerk.com/docs/js-frontend/reference/components/authentication/waitlist.md#open-waitlist)
- [closeWaitlist()](https://clerk.com/docs/js-frontend/reference/components/authentication/waitlist.md#close-waitlist)

The following examples assume that you followed the [quickstart](https://clerk.com/docs/js-frontend/getting-started/quickstart.md) to add Clerk to your JavaScript app.

### <code>mount<wbr />Waitlist()</code>

Render the `<Waitlist />` component to an HTML `<div>` element.

```typescript
function mountWaitlist(node: HTMLDivElement, props?: WaitlistProps): void
```

### <code>mount<wbr />Waitlist()</code> params

| Name   | Type           | Description                                                      |
| ------ | -------------- | ---------------------------------------------------------------- |
| node   | HTMLDivElement | The <div> element used to render in the <Waitlist /> component |
| props? | WaitlistProps  | The properties to pass to the <Waitlist /> component            |

#### `mountWaitlist()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk('{{pub_key}}')
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="waitlist"></div>
`

const waitlistDiv = document.getElementById('waitlist')

clerk.mountWaitlist(waitlistDiv)
```

### <code>unmount<wbr />Waitlist()</code>

Unmount and run cleanup on an existing `<Waitlist />` component instance.

```typescript
function unmountWaitlist(node: HTMLDivElement): void
```

#### `unmountWaitlist()` params

| Name | Type           | Description                                                                   |
| ---- | -------------- | ----------------------------------------------------------------------------- |
| node | HTMLDivElement | The container <div> element with a rendered <Waitlist /> component instance |

#### `unmountWaitlist()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk('{{pub_key}}')
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="waitlist"></div>
`

const waitlistDiv = document.getElementById('waitlist')

clerk.mountWaitlist(waitlistDiv)

// ...

clerk.unmountWaitlist(waitlistDiv)
```

### `openWaitlist()`

Opens the `<Waitlist />` component as an overlay at the root of your HTML `body` element.

```typescript
function openWaitlist(props?: WaitlistProps): void
```

#### `openWaitlist()` params

| Name   | Type          | Description                                           |
| ------ | ------------- | ----------------------------------------------------- |
| props? | WaitlistProps | The properties to pass to the <Waitlist /> component |

#### `openWaitlist()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk('{{pub_key}}')
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="waitlist"></div>
`

const waitlistDiv = document.getElementById('waitlist')

clerk.openWaitlist(waitlistDiv)
```

### `closeWaitlist()`

Closes the waitlist overlay.

```typescript
function closeWaitlist(): void
```

#### `closeWaitlist()` usage

filename: main.js
```js
import { Clerk } from '@clerk/clerk-js'

// Initialize Clerk with your Clerk Publishable Key
const clerk = new Clerk('{{pub_key}}')
await clerk.load()

document.getElementById('app').innerHTML = `
  <div id="waitlist"></div>
`

const waitlistDiv = document.getElementById('waitlist')

clerk.openWaitlist(waitlistDiv)

// ...

clerk.closeWaitlist(waitlistDiv)
```

## Properties

All props are optional.

| Name                  | Type                    | Description                                                                                                                                                               |
| --------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| afterJoinWaitlistUrl? | string                  | The full URL or path to navigate to after joining the waitlist.                                                                                                           |
| appearance?           | Appearance | undefined | An object to style your components. Will only affect Clerk components and not Account Portal pages.                                                                       |
| fallback?             | ReactNode               | An element to be rendered while the component is mounting.                                                                                                                |
| signInUrl?            | string                  | The full URL or path to the sign in page. Used for the 'Already have an account? Sign in' link that's rendered. It's recommended to use the environment variable instead. |

## Customization

To learn about how to customize Clerk components, see the [customization guide](https://clerk.com/docs/js-frontend/guides/customizing-clerk/appearance-prop/overview.md).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
