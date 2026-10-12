# Bot sign-up protection (Legacy)

Legacy bot sign-up protection runs a CAPTCHA widget on every sign-up form, and the widget decides on its own whether to ask the user to interact with it. [Challenge suspicious sign-ups](https://clerk.com/docs/guides/secure/bot-protection.md) replaces it: Clerk decides which sign-ups to challenge, using more signals.

Applications that use legacy bot sign-up protection can keep using it, and can turn it on or off until they update. New applications use **Challenge suspicious sign-ups** instead. To check which one your application uses, open the [**Protections**](https://dashboard.clerk.com/~/protect/rules) page in the Clerk Dashboard. An application on the legacy version has a **Bot sign-up protection** row there.

> When enabled, users suspected of being a bot will be shown an interactive challenge (like clicking a checkbox) to verify they are human. The CAPTCHA widget will only be shown if the client is suspected to be a bot.

> **Deprecated:** If your application previously had the **Invisible** CAPTCHA type selected, it's highly recommended to switch to the **Smart** option, as the **Invisible** option is deprecated.
> If the Dashboard doesn't show CAPTCHA type options for your application, legacy bot sign-up protection uses the **Smart** option and is enabled from the **Bot sign-up protection** row on the **Protections** page.

## Update to Challenge suspicious sign-ups

When the update is available for your application, the [**Protections**](https://dashboard.clerk.com/~/protect/rules) page in the Clerk Dashboard shows an **Update available** banner.

### Why update

- **It looks at more signals.** Besides checking whether a sign-up looks automated, it treats sign-ups through VPNs, Tor, and residential or datacenter proxies as suspicious.
- **It keeps improving.** Clerk improves how it spots bots on its side, without you changing anything.

### Before you update

- **Check the requirements.** See [Requirements](https://clerk.com/docs/guides/secure/bot-protection.md#requirements).
- **Find out what your application uses for sign-ups.** The Dashboard can't tell whether your application uses Clerk's prebuilt sign-up form or a custom one, so it asks you. If you're not sure, ask the developer who built your sign-up form:
  - Clerk's [<SignUp />](https://clerk.com/docs/reference/components/authentication/sign-up.md) component is prebuilt, even if you've changed its appearance. So are the [Account Portal](https://clerk.com/docs/guides/account-portal/overview.md) pages.
  - A form built with Clerk's hooks or APIs is a custom flow.
  - If your application uses both, treat it as custom.
- **If it's custom, check your flow.** With **Challenge suspicious sign-ups**, ClerkJS shows the challenge itself, and only custom flows that meet [the custom flow requirements](https://clerk.com/docs/guides/development/custom-flows/authentication/bot-sign-up-protection.md#requirements) can show it. In a flow that doesn't meet them, users can't finish a sign-up that is challenged. Don't update until your flow meets them: the update can't be undone.
- **Native applications aren't affected.** Neither version challenges sign-ups from native applications while the [Native API](https://clerk.com/docs/guides/secure/bot-protection.md#native-api-and-captcha) is enabled, so the update doesn't change how those sign-ups are handled.

### Test in your development instance first

Update your [development instance](https://clerk.com/docs/guides/development/managing-environments.md#development-instance) before your production instance, especially if your application has a custom sign-up flow. Each instance updates separately, so updating development changes nothing in production, and you can watch your flow handle a challenged sign-up before your users meet one.

1. In the Clerk Dashboard, open your development instance and follow the steps in [How to update](#how-to-update).
   - The Dashboard's check can't load an application that runs on your machine, such as `http://localhost:3000`. If the check doesn't pass for that reason, confirm the [requirements](https://clerk.com/docs/guides/secure/bot-protection.md#requirements) yourself, then select **Bypass checks**. This applies to your development instance only.
2. Run your application against your development instance, and sign up in a way that gets challenged, such as while connected to a commercial VPN. See [What it challenges](https://clerk.com/docs/guides/secure/bot-protection.md#what-it-challenges). If your application supports OAuth or enterprise SSO, sign up through it, so the challenge runs on your SSO callback route.
   - Sign up by hand for this step. A sign-up that carries a [Testing Token](https://clerk.com/docs/guides/development/testing/overview.md#testing-tokens) isn't challenged, so end-to-end tests that use Testing Tokens keep passing after you update, but they can't show you the challenge.
3. Confirm that the challenge appears, and that the sign-up completes once it passes. If it doesn't, your flow misses one of [the custom flow requirements](https://clerk.com/docs/guides/development/custom-flows/authentication/bot-sign-up-protection.md#requirements), which also say how each missing one shows up.
4. Update your production instance.

### How to update

The update has two steps. First the Dashboard checks your application, then you tell it what your application uses for sign-ups.

1. In the Clerk Dashboard, navigate to the [**Protections**](https://dashboard.clerk.com/~/protect/rules) page under **Protect**.
2. In the **Update available** banner, select **Check your application**. If the banner shows **Update** instead, your application has already passed this check: select **Update** and skip the next step.
3. Select **Verify**. Clerk loads your application and checks it against the [requirements](https://clerk.com/docs/guides/secure/bot-protection.md#requirements). If a requirement fails, fix it in your application, then select **Verify** again. When the requirements pass, select **Continue update**.
4. Under **What does your application use for sign-ups?**, select the option that applies:
   - **Clerk's prebuilt sign-up form**: you don't need to do anything else.
   - **A custom sign-up form**: check your flow against [the custom flow requirements](https://clerk.com/docs/guides/development/custom-flows/authentication/bot-sign-up-protection.md#requirements), then select **I've checked that my custom sign-up flow meets the requirements.**
   - **I'm not sure**: the Dashboard doesn't update your application. Select **Close for now**, [find out what your application uses](#before-you-update), then start again. Your current protection stays as it is in the meantime.
5. Select **Update protection**.

The update replaces legacy bot sign-up protection with **Challenge suspicious sign-ups**, on its default settings, and keeps the state you had. If legacy bot sign-up protection was on, **Challenge suspicious sign-ups** is on. If it was off, **Challenge suspicious sign-ups** stays off until you [turn it on](https://clerk.com/docs/guides/secure/bot-protection.md#turn-on-the-protection). You can't switch back to legacy bot sign-up protection in the Dashboard.

## Manage legacy bot sign-up protection

Until you update, you can turn legacy bot sign-up protection on or off:

1. In the Clerk Dashboard, navigate to the [**Protections**](https://dashboard.clerk.com/~/protect/rules) page under **Protect**.
2. In the **Bot sign-up protection** row, check the **Status**. The row is tagged **Legacy** when the update is available for your application.
   - If **Disabled**, select **Enable**. In the dialog, toggle on **Enable**, then select **Save**.
   - If **Enabled**, legacy bot sign-up protection is already active. To turn it off, select **Manage**, toggle off **Enable**, then select **Save**.

## Custom sign-up flows

With legacy bot sign-up protection, a custom sign-up flow needs to provide an element for the CAPTCHA widget. See [Legacy bot sign-up protection in a custom flow](https://clerk.com/docs/guides/development/custom-flows/authentication/bot-sign-up-protection.md#legacy-bot-sign-up-protection).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
