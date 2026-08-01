# Add React Router to your Clerk + React application

**Before you start**

- [Set up a React + Clerk application](https://clerk.com/docs/react/getting-started/quickstart.md)

> There are many routing libraries available for React, but Clerk Docs uses React Router as it's the most popular and well-supported routing library for React. If you're using a different routing library, use these guides as a starting point.

React Router supports three different routing strategies, or ["modes"](https://reactrouter.com/start/modes):

- **Declarative mode:** Enables basic routing features like matching URLs to components, navigating around the app, and providing active states with APIs like `<Link>`, `useNavigate()`, and `useLocation()`.
- **Data mode:** Adds data loading, actions, pending states and more with APIs like loader, action, and useFetcher. To use React Router in data mode, see the [demo repository](https://github.com/clerk/clerk-react-quickstart/blob/integrate-react-router-dom-using-data-router-method/src/main.tsx). A guide is coming soon.
- **Framework mode:** Use React Router as a framework to build your entire app. To use React Router as a framework instead, see the [React Router quickstart](https://clerk.com/docs/react-router/getting-started/quickstart.md).

This guide will cover how to add React Router in **declarative mode**, assuming you have followed the [React quickstart](https://clerk.com/docs/react/getting-started/quickstart.md).

1. ## Install `react-router` and `@clerk/clerk-react`

   Run the following command to install both React Router and the Clerk React Router SDK:

   ```npm
   npm install react-router @clerk/clerk-react
   ```
2. ## Update `<ClerkProvider>`

   Move `<ClerkProvider />` to its own component.

   > [!QUIZ]
   > Why do we need to move `<ClerkProvider />` to its own component?
   >
   > ***
   >
   > `createRoot(document.getElementById('root')!).render()` isn't a component, so you can't use a hook inside of it. In the next step, you'll use the `useNavigate()` hook with `<ClerkProvider>`, so you need to move it to its own component.

   filename: src/main.tsx

   ```tsx
   import { StrictMode } from 'react'
   import { createRoot } from 'react-dom/client'
   import { ClerkProvider } from '@clerk/clerk-react'
   import './index.css'
   import App from './App.tsx'

   function RootLayout() {
     return (
       <ClerkProvider>
         <App />
       </ClerkProvider>
     )
   }

   createRoot(document.getElementById('root')!).render(
     <StrictMode>
       <RootLayout />
     </StrictMode>,
   )
   ```
3. ## Set up React Router

   To use declarative mode, wrap your app in a `<BrowserRouter>`. To define your app's routes, add `<Routes>` and `<Route>` components. This example adds the `/` (home) route and renders the `<App />` component when the URL matches. Read more about routing in the [React Router docs](https://reactrouter.com/start/declarative/routing).

   The `useNavigate()` hook from `react-router` is used by Clerk components for navigation events. This will prevent flicker and app reloading.

   filename: src/main.tsx

   ```tsx
   import { StrictMode } from 'react'
   import { createRoot } from 'react-dom/client'
   import { BrowserRouter, Routes, Route, useNavigate } from 'react-router'
   import { ClerkProvider } from '@clerk/clerk-react'
   import './index.css'
   import App from './App.tsx'

   function RootLayout() {
     const navigate = useNavigate()

     return (
       <ClerkProvider
         routerPush={(to) => navigate(to)}
         routerReplace={(to) => navigate(to, { replace: true })}
       >
         <Routes>
           <Route path="/" element={<App />} />
         </Routes>
       </ClerkProvider>
     )
   }

   createRoot(document.getElementById('root')!).render(
     <StrictMode>
       <BrowserRouter>
         <RootLayout />
       </BrowserRouter>
     </StrictMode>,
   )
   ```

## Next steps

Learn more about Clerk components, how to use them to create custom pages, and how to use Clerk's client-side helpers using the following guides.

- [Create a custom sign-in-or-up page](https://clerk.com/docs/react/guides/development/custom-sign-in-or-up-page.md): Learn how to add a custom sign-in-or-up page to your React app with Clerk's components.
- [Read user data](https://clerk.com/docs/guides/users/reading.md?sdk=react): Learn how to use Clerk's hooks to read user data in your React app.
- [Client-side helpers](https://clerk.com/docs/react/reference/hooks/overview.md): Learn more about Clerk's client-side helpers and how to use them.
- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md?sdk=react): Learn how to quickly add authentication to your app using Clerk's suite of components.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
