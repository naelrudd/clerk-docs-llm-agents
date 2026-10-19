# Clerk Protect

Clerk Protect uses [system protections](#available-system-protections) to block or challenge abusive sign-ups inside Clerk's authentication flows. You can turn on these protections from the [**Protections**](https://dashboard.clerk.com/~/protect/rules) page in the Clerk Dashboard, and Clerk enforces them. See [Set up Protect](https://clerk.com/docs/guides/protect/setup.md) for more information.

Clerk Protect also includes features such as [Device Trust](https://clerk.com/docs/guides/secure/device-trust.md), which can require a second factor during password sign-in.

## How system protections work

For a sign-up, an enabled system protection takes one of three actions:

- **Allow**: The attempt continues.
- **Challenge**: The user completes a verification step, then continues. Most people pass it without doing anything.
- **Block**: Clerk rejects the attempt.

Each system protection decides when to challenge or block. Every challenge and block appears as a Protect event in [Application Logs](https://clerk.com/docs/guides/dashboard/logs/application-logs.md#protect-events).

## Available system protections

Clerk builds and maintains the following system protections. The **Action** column shows what each protection does when its criteria are met; otherwise, that protection allows the sign-up to continue.

| Protection                                                                                                                    | What it does                                                                           | Action    |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | --------- |
| [Challenge suspicious sign-ups](https://clerk.com/docs/guides/secure/bot-protection.md)                                       | Challenges sign-ups that look automated or come through VPNs, Tor, or proxies.         | Challenge |
| [Require Device Intelligence checks](https://clerk.com/docs/guides/protect/system-protections/require-device-intelligence.md) | Blocks a sign-up created by a browser that has no verified Device Intelligence result. | Block     |

> [Device Intelligence](https://clerk.com/docs/guides/protect/device-intelligence.md) runs background checks in browsers without adding a visible step. It doesn't block sign-ups on its own; **Require Device Intelligence checks** uses the result when enabled.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
