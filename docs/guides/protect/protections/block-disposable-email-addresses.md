# Block disposable email addresses

> This protection is included on every plan, and it's off by default.

Disposable email addresses are throwaway inboxes, commonly used to create spam accounts. This protection blocks email addresses that are known to be disposable.

## What it blocks

An email address is blocked when its domain is known to be disposable. This applies when someone signs up, and when a user adds an email address to an existing account. It doesn't affect sign-ins, so existing users with a disposable address can keep signing in.

Clerk checks the email address's domain and each of its parent domains. For example, an address at `mail.example.com` is blocked if `mail.example.com` or `example.com` is known to be disposable. If a domain that your users rely on is blocked by mistake, [contact support](https://clerk.com/contact/support).

## What happens when an address is blocked

The user sees an error that the email address isn't allowed, and can't continue with that address.

## Settings

This protection has no settings.

## How it works with other protections

- **Risky domains.** This protection blocks only domains already known to be disposable. To also block sign-ups from email domains that Clerk rates as risky, turn on [Block risky email domains](https://clerk.com/docs/guides/protect/protections/block-risky-email-domains.md), which requires the [Business plan](https://clerk.com/pricing).
- **Extra accounts from one inbox.** [Block email subaddresses](https://clerk.com/docs/guides/protect/protections/block-email-subaddresses.md) blocks variations of an email address that already has an account.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
