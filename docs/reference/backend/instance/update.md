# update()

Updates the current instance.

```typescript
function update(params: UpdateParams): Promise<void>
```

## `UpdateParams`

| Property                                                                                                | Type                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------- | ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="allowedorigins"></a> `allowedOrigins?`                                                           | `string[]`                       | For browser-like stacks such as browser extensions, Electron, or Capacitor.js, the instance allowed origins need to be updated with the request origin value. For Chrome extensions popup, background, or service worker pages the origin is `chrome-extension://extension_uiid`. For Electron apps the default origin is `http://localhost:3000`. For Capacitor.js, the origin is `capacitor://localhost`. |
| <a id="clerkjsversion"></a> `clerkJsVersion?`                                                           | `string | null`                  | The npm version for `@clerk/clerk-js`.                                                                                                                                                                                                                                                                                                                                                                      |
| <a id="developmentorigin"></a> `developmentOrigin?`                                                     | `string | null`                  | The development origin for the instance.                                                                                                                                                                                                                                                                                                                                                                    |
| <a id="enhancedemaildeliverability"></a> `enhancedEmailDeliverability?`                                 | `boolean | null`                 | Whether the instance should send emails from "[verifications@clerk.dev](mailto:verifications@clerk.dev)" instead of your domain. This can be helpful if you do not have a high domain reputation.                                                                                                                                                                                                           |
| <a id="hibp"></a> `hibp?`                                                                               | `boolean | null`                 | Whether the instance should be using the Have I Been Pwned (HIBP) service to check passwords for breaches.                                                                                                                                                                                                                                                                                                  |
| <a id="preferredsigninstrategywhenpasswordrequired"></a> `preferredSignInStrategyWhenPasswordRequired?` | `"password" | "otp" | "" | null` | Overrides the sign-in strategy that is preferred when a password is required. The value is only consulted when a password is required, and is dormant otherwise. Pass an empty string to clear the override. Passing `null` or `undefined` leaves the current value unchanged.                                                                                                                              |
| <a id="supportemail"></a> `supportEmail?`                                                               | `string | null`                  | The support email for the instance.                                                                                                                                                                                                                                                                                                                                                                         |
| <a id="testmode"></a> `testMode?`                                                                       | `boolean | null`                 | Toggles [test mode](https://clerk.com/docs/guides/development/testing/test-emails-and-phones.md#set-up-test-mode) for this instance, allowing the use of test email addresses and phone numbers. Defaults to `true` for development instances.                                                                                                                                                              |
| <a id="urlbasedsessionsyncing"></a> `urlBasedSessionSyncing?`                                           | `boolean | null`                 | Whether the instance should use URL-based session syncing in development mode (i.e., without third-party cookies).                                                                                                                                                                                                                                                                                          |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.instances.update({
  testMode: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/instance`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/instance-settings/PATCH/instance){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
