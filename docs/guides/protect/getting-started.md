# Get started with Protect

Before you can enable protections, your application must meet the following requirements.

## Requirements

- **ClerkJS 6.39.0 or later** - Clerk's SDKs load the latest version by default. If you bundle or host `@clerk/clerk-js` yourself, update it. To check your version, run `window.Clerk.version` in your browser's console.
- **Content Security Policy** - If your application sets one, add [Clerk's CSP headers](https://clerk.com/docs/guides/secure/best-practices/csp-headers.md).
- **Custom flows** - If your application uses custom authentication flows, they need to handle new error messages and [display challenges](https://clerk.com/docs/guides/development/custom-flows/authentication/bot-sign-up-protection.md).
- **Current bot protection** - Older applications might use legacy bot sign-up protection and need to [update to **Challenge suspicious sign-ups**](https://clerk.com/docs/guides/secure/legacy-bot-protection.md#update-to-challenge-suspicious-sign-ups).

## Enable protections

Navigate to the [**Protections**](https://dashboard.clerk.com/~/protect/protections) page in the Clerk Dashboard to configure each protection. See [Protections](https://clerk.com/docs/guides/protect/protections/overview.md) for a description of what each one does.

Each instance has separate protection settings. Test sign-ups in development without a [testing token](#bypass-protections-in-tests), review any Protect events in [Application Logs](https://clerk.com/docs/guides/dashboard/logs/application-logs.md#protect-events), then enable the same protections in your production instance.

## Native API considerations

Clerk's native SDKs for iOS, Android, and Expo require the Native API to be enabled and don't support challenges yet.

- **Protections configured to challenge** will allow attempts from native environments without a challenge.
- **Protections configured to block** still apply to native environments.
- **[Require Device Intelligence checks](https://clerk.com/docs/guides/protect/protections/require-device-intelligence.md)** applies to browsers only, so native environments skip it.

Because the Native API is public, attackers can also use it to bypass challenge-based protections. Only enable it if your application requires it. When the Native API is disabled, Clerk rejects requests from native applications with a `native_api_disabled` error.

## Bypass protections in tests

[Testing tokens](https://clerk.com/docs/guides/development/testing/overview.md#testing-tokens) let automated tests skip the protections that block or challenge. [Require Device Intelligence checks](https://clerk.com/docs/guides/protect/protections/require-device-intelligence.md) is the exception: it still checks a sign-up that carries a testing token, so browser tests need to meet the same [requirements](#requirements).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
