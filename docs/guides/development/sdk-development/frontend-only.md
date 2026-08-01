# Frontend-only SDK

While [ClerkJS](https://clerk.com/docs/reference/javascript/overview.md) can be used in any browser context and framework, realistically users expect to consume its features through the conventions and syntax of their framework of choice. For example, `@clerk/react` turns ClerkJS into React components, `@clerk/astro` into Astro components, and so on.

In non-browser environments, you’ll need to re-implement the [Clerk class](https://clerk.com/docs/reference/objects/clerk.md) in the SDK’s programming language, interacting with the [FAPI](https://clerk.com/docs/guides/development/sdk-development/terminology.md).

## Expected features

- User only needs to provide their [Publishable Key](https://clerk.com/docs/guides/development/sdk-development/terminology.md)
- User only needs to adjust one or two files to add Clerk to their app (e.g., adding Clerk to the configuration file of that framework)
- User can use [Clerk’s components](https://clerk.com/docs/reference/components/overview.md) in their choice of framework (e.g., in a React-based framework you import these components as React components)
- Give users access to [Client](https://clerk.com/docs/reference/objects/client.md){{ target: '_blank' }}, [Session](https://clerk.com/docs/reference/objects/session.md){{ target: '_blank' }}, [User](https://clerk.com/docs/reference/objects/user.md){{ target: '_blank' }}, and [Organization](https://clerk.com/docs/reference/objects/organization.md){{ target: '_blank' }} properties through the framework’s choice of state management
- User should be able to use [ClerkJS options](https://clerk.com/docs/reference/objects/clerk.md#clerk-options){{ target: '_blank' }}

## Implementation

While the implementation details will vary for each SDK, there are certain steps you'll have to go through in any case. Consider the steps below a rough guidance on what needs to be done, and also remember to follow the [conventions](https://clerk.com/docs/guides/development/sdk-development/conventions.md).

> The code blocks below will be written in pseudo-code. If you're looking for real-world examples, have a look at these repositories: [`@clerk/react`](https://github.com/clerk/javascript/tree/main/packages/react), [`@clerk/astro`](https://github.com/clerk/javascript/tree/main/packages/astro)

1. ### Create a Clerk instance

   Create a Clerk instance that will only be invoked once (e.g., following the [singleton pattern](https://www.patterns.dev/vanilla/singleton-pattern/)). During its initialization you'll execute the following steps.

   filename: create-clerk-instance.ts

   ```ts
   import { runOnce } from './utils'
   // States accessible to other parts of your SDK and/or its users
   import { $clerk, $state } from './stores'

   export const createClerkInstance = runOnce(createClerkInstanceInternal)

   async function createClerkInstanceInternal(options) {
     let clerkJSInstance = window.Clerk
   }
   ```
2. ### Hotload ClerkJS

   In order to make `Clerk` available on the `window` object, your SDK needs to load ClerkJS. Call `loadClerkJsScript()` from `@clerk/shared`.

   filename: create-clerk-instance.ts

   ```ts
   import { loadClerkJSScript } from '@clerk/shared/loadClerkJSScript'
   import { runOnce } from './utils'
   import { $clerk, $state } from './stores'

   export const createClerkInstance = runOnce(createClerkInstanceInternal)

   async function createClerkInstanceInternal(options) {
     let clerkJSInstance = window.Clerk

     if (!clerkJSInstance) {
       await loadClerkJSScript(options)

       if (!window.Clerk) {
         throw new Error('Failed to download latest ClerkJS.')
       }
       clerkJSInstance = window.Clerk
     }

     if (!$clerk.get()) {
       $clerk.set(clerkJSInstance)
     }
   }
   ```
3. ### Call `window.Clerk.load()`

   By calling [window.Clerk.load()](https://clerk.com/docs/reference/objects/clerk.md#load) the Clerk class is initialized and your SDK now has access to all its functionality.

   filename: create-clerk-instance.ts

   ```ts
   import { loadClerkJSScript } from '@clerk/shared/loadClerkJSScript'
   import { runOnce } from './utils'
   import { $clerk, $state } from './stores'

   export const createClerkInstance = runOnce(createClerkInstanceInternal)

   async function createClerkInstanceInternal(options) {
     let clerkJSInstance = window.Clerk

     if (!clerkJSInstance) {
       // loadClerkJSScript() codepath
     }

     if (!$clerk.get()) {
       $clerk.set(clerkJSInstance)
     }

     await clerkJSInstance.load(options)
   }
   ```
4. ### Add event listeners

   Expose properties to the internal state (e.g., a `useState` in React) through adding [event listeners](https://clerk.com/docs/reference/objects/clerk.md#add-listener).

   filename: create-clerk-instance.ts

   ```ts
   import { loadClerkJSScript } from '@clerk/shared/loadClerkJSScript'
   import { runOnce } from './utils'
   import { $clerk, $state } from './stores'

   export const createClerkInstance = runOnce(createClerkInstanceInternal)

   async function createClerkInstanceInternal(options) {
     let clerkJSInstance = window.Clerk

     if (!clerkJSInstance) {
       // loadClerkJSScript() codepath
     }

     await clerkJSInstance.load(options)

     if (!$clerk.get()) {
       $clerk.set(clerkJSInstance)
     }

     clerkJSInstance.addListener((resources) => {
       $state.setKey('client', resources.client)
       $state.setKey('session', resources.session)
       $state.setKey('user', resources.user)
       $state.setKey('organization', resources.organization)
     })
   }
   ```
5. ### Add UI components

   Build out the components that your users will utilize in their app. Call the `mount()` function when the component is in view/mounts and the `unmount()` function when the component is unmounted. These functions are described in the [Clerk class components](https://clerk.com/docs/reference/objects/clerk.md#components).

   Use the idiomatic way of your framework for doing this. If you can abstract these repetitions into a re-usable hook/directive, then do that.

   filename: SignIn.tsx

   ```tsx
   import { $clerk } from './stores'

   const SignInComponent = (props: SignInProps) => {
     const el = ref()

     function onMount() {
       $clerk.mountSignIn(el, props)
     }

     function onUnMount() {
       $clerk.unmountSignIn(el)
     }
   }
   ```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
