# <RedirectToTasks />

The `<RedirectToTasks />` component will navigate to the tasks flow which has been configured in your application instance when users have pending session tasks. The behavior will be just like a server-side (3xx) redirect, and will override the current location in the history stack.

The prebuilt session task flow is hosted through Clerk's [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md?sdk=expo#sign-in). For example, if the user has a pending `choose-organization` task, they will be redirected to the `/tasks/choose-organization` Account Portal page. If you don't want to use the prebuilt components or Account Portal, you can build a [custom flow](https://clerk.com/docs/guides/development/custom-flows/authentication/session-tasks.md?sdk=expo).

## Example

Your sign-up/sign-in flow should handle session tasks, but if a user's authentication flow is interrupted and they aren't able to complete the tasks, you can use the `<RedirectToTasks />` component to redirect them to the appropriate task page.

With the default hash routing used by `<SignIn />` in Expo web, the `<RedirectToTasks />` component redirects to the `/sign-in#/tasks/<task-key>` URL, expecting [the `<SignIn />` component to be hosted on the `/sign-in` route](https://clerk.com/docs/guides/development/web-support/custom-sign-in-or-up-page.md?sdk=expo). If it is, then the `<SignIn />` component will handle the session task flows. However, if you want to customize the paths where specific tasks are redirected, you can use the [`taskUrls` option on `<ClerkProvider>`](https://clerk.com/docs/guides/configure/session-tasks.md?sdk=expo#using-the-task-urls-option).

> The `<RedirectToTasks />` component is only available in Expo web projects. It is not supported in native iOS and Android apps.

In the following example, the `<RedirectToTasks />` component is used to protect an Expo web page. Users can't access this page until they complete their pending session tasks. You can also render the component from a web-specific layout so that users can't access **any** of the web app until they complete their pending session tasks.

filename: src/app/index.web.tsx
```tsx
import { RedirectToTasks } from '@clerk/expo/web'

export default function Page() {
  return <RedirectToTasks />
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
