# Device Intelligence

Device Intelligence is a set of background browser checks used by [Clerk Protect](https://clerk.com/docs/guides/protect/overview.md). ClerkJS runs the checks, and Clerk verifies the result. They add no visible step during sign-up.

## Requirements

- **ClerkJS 6.39.0 or later.** Clerk's Core 3 SDKs load it automatically. See [Set up Protect](https://clerk.com/docs/guides/protect/setup.md#requirements).
- **A Content Security Policy that allows Device Intelligence.** If your application sets a Content Security Policy, add the directives in [Configure Clerk Content-Security-Policy headers](https://clerk.com/docs/guides/secure/best-practices/csp-headers.md).

## How Device Intelligence works

Clerk enables Device Intelligence automatically when a new application is created or when an existing application passes or bypasses the Protect requirements check in the Clerk Dashboard. Device Intelligence has no Dashboard setting.

Device Intelligence doesn't block or challenge sign-ups on its own. [Require Device Intelligence checks](https://clerk.com/docs/guides/protect/system-protections/require-device-intelligence.md) is a separate protection. When enabled, it blocks a browser sign-up if Clerk has no verified Device Intelligence result when the sign-up is created.

To disable Device Intelligence, first disable **Require Device Intelligence checks**, then [contact support](https://clerk.com/contact/support). Without Device Intelligence, that protection blocks every browser sign-up.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
