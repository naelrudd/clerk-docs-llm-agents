# Build a custom waitlist form

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md?sdk=astro) or [prebuilt components](https://clerk.com/docs/astro/reference/components/overview.md).

Clerk's [<Waitlist />](https://clerk.com/docs/astro/reference/components/authentication/waitlist.md) component provides an out-of-the-box solution for allowing users to join your waitlist for early access to your app. However, if you're building a custom user interface, you can use the [useWaitlist()](https://clerk.com/docs/reference/hooks/use-waitlist.md) hook to build a custom waitlist form.

This guide demonstrates how to use the Clerk API to build a custom user interface for joining your app's waitlist.

## Before you start

Before using the `useWaitlist()` hook, you must enable **Waitlist** mode in the Clerk Dashboard:

1. In the Clerk Dashboard, navigate to the [**Waitlist**](https://dashboard.clerk.com/~/user-authentication/waitlist) page.
2. Toggle on **Enable waitlist** and select **Save**.

## Build the custom flow

The following example demonstrates how to use the `useWaitlist()` hook to create a custom waitlist form. Users can submit their email address to join the waitlist, and the component displays appropriate feedback based on the submission state.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
