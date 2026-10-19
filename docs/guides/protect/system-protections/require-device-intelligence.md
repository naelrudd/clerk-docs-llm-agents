# Require Device Intelligence checks

**Require Device Intelligence checks** blocks a sign-up created by a browser for which Clerk has no verified [Device Intelligence](https://clerk.com/docs/guides/protect/device-intelligence.md) result. ClerkJS runs Device Intelligence checks in the background; the checks don't block sign-ups on their own.

## What it blocks

A sign-up from a browser is blocked when Clerk has no verified Device Intelligence result for that browser at the moment the sign-up is created. Clerk checks once, at creation. Later steps, such as entering a verification code, aren't checked.

The protection applies to sign-ups from browsers only:

- It never checks a sign-in, so it doesn't stop existing users from signing in.
- Sign-ups from native apps built with Clerk iOS, Android, and Expo SDKs aren't affected.

Clerk rejects the sign-up, and the user can't continue. Each blocked attempt appears as a `protect.sign_up.blocked` event in [Application Logs](https://clerk.com/docs/guides/dashboard/logs/application-logs.md#protect-events).

[Testing Tokens](https://clerk.com/docs/guides/development/testing/overview.md#testing-tokens) don't skip this check. End-to-end tests that drive a real browser, such as Playwright or Cypress, run the check the same way your users' browsers do, so they need the same [requirements](#requirements).

## Requirements

- **ClerkJS 6.39.0 or later.** See [Set up Protect](https://clerk.com/docs/guides/protect/setup.md#requirements).
- **A Content Security Policy that allows Device Intelligence.** If your application sets a Content Security Policy, add the directives in [Configure Clerk Content-Security-Policy headers](https://clerk.com/docs/guides/secure/best-practices/csp-headers.md).
- **Device Intelligence enabled for your application.** Clerk enables it automatically for new applications and for existing applications that pass or bypass Protect's requirements check. See [How Device Intelligence works](https://clerk.com/docs/guides/protect/device-intelligence.md#how-device-intelligence-works).

> If Device Intelligence isn't enabled, or your Content Security Policy blocks it, this protection blocks every sign-up from a browser. Users on a ClerkJS too old to run Device Intelligence are blocked too. Enable it in your [development instance](https://clerk.com/docs/guides/development/managing-environments.md#development-instance) first, then sign up from a browser yourself before you enable it in production.

## Enable the protection

**Require Device Intelligence checks** is disabled by default. To enable or disable it:

1. In the Clerk Dashboard, under **Protect**, navigate to the [**Protections**](https://dashboard.clerk.com/~/protect/rules) page.
2. In the **Require Device Intelligence checks** row, check the **Status**.
   - If **Disabled**, select **Enable**. In the dialog, toggle on **Enable**, then select **Save**.
   - If **Enabled**, the protection is already active. To disable it, select **Manage**, toggle off **Enable**, then select **Save**.
   - If **Setup required**, select **Manage** and complete the setup. See [Set up Protect](https://clerk.com/docs/guides/protect/setup.md#enable-protections).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
