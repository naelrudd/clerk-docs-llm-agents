# Bot protection

To protect your sign-ups from bots, Clerk leverages data from our CDN to determine whether a user attempting to sign up might be a bot or not.

## Enable bot sign-up protection

1. In the Clerk Dashboard, navigate to the [**Attack protection**](https://dashboard.clerk.com/~/protect/attack-protection) page.
2. Enable the **Bot sign-up protection** toggle.
   - When enabled, users suspected of being a bot will be shown an interactive challenge (like clicking a checkbox) to verify they are human. The CAPTCHA widget will only be shown if the client is suspected to be a bot.

> If your application previously had the **Invisible** CAPTCHA type selected, it's highly recommended to switch to the **Smart** option, as the **Invisible** option is deprecated.
> For newer applications, CAPTCHA type options are no longer shown in the Dashboard. Bot protection uses the **Smart** option by default and is enabled by turning on the **Bot sign-up protection** toggle only.

## Limitations

### Native API and CAPTCHA

The [**Native API**](https://dashboard.clerk.com/~/native-applications) setting allows native applications and browser extensions to make requests to Clerk in environments that cannot always complete a browser-based CAPTCHA challenge. It enables a public request pathway through which CAPTCHA challenges are bypassed, even when **Bot sign-up protection** is enabled. Clerk's standard browser-based authentication flows continue to use CAPTCHA when a challenge is required.

Only enable the Native API when your native application or browser extension requires it. Because the pathway is public, it must not be treated as a secret or used as the only boundary protecting your application from automated traffic. Registering an application's bundle identifier or package name allows Clerk to validate callbacks for supported native authentication flows, but does not make the Native API pathway private.

### Custom sign-up flows

If you're building a custom sign-up flow using the Clerk API instead of using Clerk components, and you have enabled **Bot sign-up protection**, then you need to ensure you have added a DOM node to render the CAPTCHA widget. Refer to the [Add bot protection to your custom sign-up flow](https://clerk.com/docs/guides/development/custom-flows/authentication/bot-sign-up-protection.md) guide for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
