# Build a custom multi-session flow

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md) or [prebuilt components](https://clerk.com/docs/reference/components/overview.md).

A multi-session application is an application that allows multiple accounts to be signed in from the same browser at the same time. The user can switch from one account to another seamlessly. Each account is independent from the rest and has access to different resources.

This guide provides you with the necessary information to build a custom multi-session flow using the Clerk API.

To implement the multi-session feature to your application, you need to handle the following scenarios:

- [Switching between different accounts](#switch-between-sessions)
- [Adding new accounts](#add-a-new-session)
- [Signing out from one account, while remaining signed in to the rest](#sign-out-active-session)
- [Signing out from all accounts](#sign-out-all-sessions)

## Enable multi-session in your application

To enable multi-session in your application, you need to configure it in the Clerk Dashboard.

1. In the Clerk Dashboard, navigate to the [**Sessions**](https://dashboard.clerk.com/~/sessions) page.
2. Toggle on **Multi-session handling**.
3. Select **Save changes**.

## Get the session and user

Use the [useClerk()](https://clerk.com/docs/reference/hooks/use-clerk.md) hook to access the current session and user.

```jsx
// Import the useClerk() hook from whatever SDK you're using
import { useClerk } from '@clerk/react'

// Get the session and user
const { session, user } = useClerk()
```

## Switch between sessions

Use the [useClerk()](https://clerk.com/docs/reference/hooks/use-clerk.md) hook to access the [Client](https://clerk.com/docs/reference/objects/client.md) object and the [setActive()](https://clerk.com/docs/reference/objects/clerk.md#set-active) method. You can use the `Client` object to access available sessions, and then use `setActive()` to set a specific session as active.

```jsx
// Import the useClerk() hook from whatever SDK you're using
import { useClerk } from '@clerk/react'

const { client, setActive } = useClerk()

// You can get all the available sessions through the client
const availableSessions = client.sessions
const currentSession = availableSessions[0].id

// Use setActive() to set the session as active
await setActive({
  session: currentSession.id,
  navigate: async ({ session, decorateUrl }) => {
    if (session?.currentTask) {
      //  Handle pending session tasks
      // See https://clerk.com/docs/guides/development/custom-flows/authentication/session-tasks
      console.log(session?.currentTask)
      return
    }

    const url = decorateUrl('/')
    if (url.startsWith('http')) {
      window.location.href = url
    } else {
      router.push(url)
    }
  },
})
```

## Add a new session

To add a new session, simply link to your existing sign-in flow. New sign-ins will automatically add to the list of available sessions on the client. To create a sign-in flow, see one of the following popular guides:

- [Email and password](https://clerk.com/docs/guides/development/custom-flows/authentication/email-password.md)
- [Passwordless authentication](https://clerk.com/docs/guides/development/custom-flows/authentication/email-sms-otp.md)
- [Social sign-in (OAuth)](https://clerk.com/docs/guides/configure/auth-strategies/social-connections/overview.md)

## Sign out all sessions

Use the [useClerk()](https://clerk.com/docs/reference/hooks/use-clerk.md) hook to access the [signOut()](https://clerk.com/docs/reference/objects/clerk.md#sign-out) method and sign out of all sessions on the current client.

```jsx
// Import the useClerk() hook from whatever SDK you're using
import { useClerk } from '@clerk/react'

const { signOut } = useClerk()

// Use signOut() to sign out all active sessions
await signOut()
```

## Sign out active session

Use the [useClerk()](https://clerk.com/docs/reference/hooks/use-clerk.md) hook to access the current session and the [signOut()](https://clerk.com/docs/reference/objects/clerk.md#sign-out) method. Sign out of the current active session by passing the session ID.

```jsx
import { useClerk } from '@clerk/react'

// Get the signOut() method and the active session
const { signOut, session } = useClerk()

// Use signOut() to sign out the active session
await signOut(session.id)
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
