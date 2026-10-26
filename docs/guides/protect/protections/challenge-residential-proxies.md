# Challenge residential proxies

> This protection requires the [Business plan](https://clerk.com/pricing), and it's off by default.

Residential proxies route traffic through ordinary home internet connections, so automated sign-ups look like they come from real households. The people whose connections are used often don't know: a free app or a smart device on their network has enrolled them in a proxy network. Blocking that traffic would also turn away some of those people, so this protection challenges it instead. The challenge is an automatic check in the visitor's browser, so a real person has nothing to solve. Every automated sign-up through one of these proxies has to complete it too, and each one costs whoever is renting the proxy.

## What it challenges

A sign-up is challenged when it comes from an IP address that's a known residential proxy, or that was used as a proxy recently. You choose how recently with the **Proxy activity window** setting.

This protection applies to sign-ups only. It never affects a sign-in.

## What happens when a sign-up is challenged

The visitor's browser completes an automatic check, and the sign-up then continues. There's nothing for the visitor to solve. The check takes from a few seconds on a fast connection to a minute or more on a slow one, and if it doesn't finish, the account isn't created.

Each challenged sign-up appears as a `protect.sign_up.challenged` event in [Application Logs](https://clerk.com/docs/guides/dashboard/logs/application-logs.md#protect-events).

## Settings

| Setting                   | Default     | Description                                                                                                                                                                |
| ------------------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Proxy activity window** | Last 7 days | How recently an IP address must have been used as a proxy for its sign-ups to be challenged. **Last 7 days** challenges more sign-ups; **Last 24 hours** challenges fewer. |

## How it works with other protections

[Block sign-ups from suspicious network types](https://clerk.com/docs/guides/protect/protections/block-suspicious-network-types.md) doesn't target residential proxies, so this protection is usually what decides what happens to them. A residential proxy on a hosting network is blocked if you block hosting and data center networks.

## Before you enable it

- **Make sure challenges can run.** See the [requirements](https://clerk.com/docs/guides/protect/getting-started.md#requirements).
- **Check that Protect sees your visitors' IP addresses.** See [If you proxy Clerk's Frontend API](https://clerk.com/docs/guides/protect/protections/overview.md#if-you-proxy-clerks-frontend-api).
- **Some real people are checked too.** People whose home connections are part of a proxy network get the check like anyone else. It takes longer on a slow connection, and a sign-up whose check doesn't finish isn't created.
- **Expect a cost, not a wall.** Residential proxy networks change constantly, and the challenge makes automated sign-ups through them more expensive rather than stopping all of them. Use it alongside other protections.
- **Native apps aren't challenged.** See [Native API considerations](https://clerk.com/docs/guides/protect/getting-started.md#native-api-considerations).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
