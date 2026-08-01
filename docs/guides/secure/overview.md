# Securing your app

Your application faces security threats like credential stuffing, brute force attacks, and cross-site scripting. Clerk provides built-in protections and configurable features to defend against them.

This page maps common threats to the Clerk features that protect your application, so you can quickly find the right configuration for your security needs.

## Attack protection

Clerk provides several features to protect your application from common authentication attacks. These features are configurable in the [Clerk Dashboard](https://dashboard.clerk.com).

| Threat                                                                                 | Description                                                                      | Clerk feature                                                                                                                                                                      |
| -------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[Credential stuffing](https://owasp.org/www-community/attacks/Credential_stuffing)** | Attackers use lists of stolen passwords to gain unauthorized access to accounts. | [Client Trust](https://clerk.com/docs/guides/secure/client-trust.md) automatically requires a second factor on new devices.                                                        |
| **[Brute force attacks](https://owasp.org/www-community/attacks/Brute_force_attack)**  | Automated scripts try many passwords against a single account.                   | [User lockout](https://clerk.com/docs/guides/secure/user-lockout.md) locks accounts after repeated failed attempts.                                                                |
| **Bot attacks**                                                                        | Automated bots create fake accounts at scale.                                    | [Bot protection](https://clerk.com/docs/guides/secure/bot-protection.md) uses Cloudflare to challenge suspicious sign-ups.                                                         |
| **Account enumeration**                                                                | Attackers probe your application to discover which accounts exist.               | [User enumeration protection](https://clerk.com/docs/guides/secure/user-enumeration-protection.md) adds rate limiting and, in strict mode, hides whether an account exists.        |
| **Compromised passwords**                                                              | Users reuse passwords that have appeared in data breaches.                       | [Password protection and rules](https://clerk.com/docs/guides/secure/password-protection-and-rules.md) checks passwords against known breaches and enforces strength requirements. |
| **Spam and abuse accounts**                                                            | Attackers create throwaway accounts using disposable emails or blocked domains.  | [Restrictions](https://clerk.com/docs/guides/secure/restricting-access.md) provides allowlists, blocklists, and disposable email blocking.                                         |

## Web security best practices

Clerk provides recommended protections and configurable features to address common web security concerns.

| Threat                                                                                | Description                                                                         | How Clerk protects you                                                                                                                                                                                           |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[Cross-site scripting (XSS)](https://owasp.org/www-community/attacks/xss/)**        | Malicious scripts injected into trusted pages steal user data.                      | [XSS leak protection](https://clerk.com/docs/guides/secure/best-practices/xss-leak-protection.md) uses HttpOnly cookies for authenticated requests and limits token exposure with short-lived app-domain tokens. |
| **[Cross-site request forgery (CSRF)](https://owasp.org/www-community/attacks/csrf)** | Attackers trick users into submitting unintended requests.                          | [CSRF protection](https://clerk.com/docs/guides/secure/best-practices/csrf-protection.md) configures cookies with SameSite.                                                                                      |
| **Content injection**                                                                 | Attackers inject unauthorized scripts or styles into your pages.                    | Configure [CSP headers](https://clerk.com/docs/guides/secure/best-practices/csp-headers.md) to restrict which resources can load on your pages.                                                                  |
| **[Session fixation](https://owasp.org/www-community/attacks/Session_fixation)**      | Attackers hijack sessions by reusing session identifiers.                           | [Fixation protection](https://clerk.com/docs/guides/secure/best-practices/fixation-protection.md) resets session tokens on sign-in and sign-out.                                                                 |
| **Phishing via email links**                                                          | Attackers exploit email verification links to gain access.                          | If enabled, [Protecting email links](https://clerk.com/docs/guides/secure/best-practices/protect-email-links.md) enforces same-device and same-browser verification.                                             |
| **Unauthorized device access**                                                        | Someone signs in from an unrecognized device without the account owner's knowledge. | [Unauthorized sign-in notifications](https://clerk.com/docs/guides/secure/best-practices/unauthorized-sign-in.md) alert users and allow session revocation.                                                      |

## Additional security features

Beyond attack-specific protections, Clerk provides features that strengthen your overall security posture:

- **[Reverification (step-up authentication)](https://clerk.com/docs/guides/secure/reverification.md)** — Require users to re-verify their identity before performing sensitive actions like changing their password or accessing Billing settings.
- **[Session options](https://clerk.com/docs/guides/secure/session-options.md)** — Configure session lifetimes, inactivity timeouts, and single-session mode to control how long sessions stay active.
- **[Geo blocking](https://clerk.com/docs/guides/development/geo-blocking.md)** — Restrict access to your application based on geographic location.

## Next steps

- [Enable Client Trust](https://clerk.com/docs/guides/secure/client-trust.md): Protect your users from credential stuffing attacks with automatic second-factor verification on new devices.
- [Configure password protection](https://clerk.com/docs/guides/secure/password-protection-and-rules.md): Enforce password strength requirements and check passwords against known data breaches.
- [Set up bot protection](https://clerk.com/docs/guides/secure/bot-protection.md): Prevent automated bots from creating fake accounts in your application.
- [Review session options](https://clerk.com/docs/guides/secure/session-options.md): Configure session lifetimes and timeouts to balance security with user experience.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
