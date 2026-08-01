# Add bot protection to your custom sign-up flow

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md?sdk=expo) or [prebuilt components](https://clerk.com/docs/expo/reference/components/overview.md).

Clerk provides the ability to add a CAPTCHA widget to your sign-up flows to protect against bot sign-ups. The [<SignUp />](https://clerk.com/docs/expo/reference/components/authentication/sign-up.md) component handles this flow out-of-the-box. However, if you're building a custom user interface, this guide will show you how to add the CAPTCHA widget to your custom sign-up flow.

1. ## Enable bot sign-up protection

   1. In the Clerk Dashboard, navigate to the [**Attack protection**](https://dashboard.clerk.com/~/protect/attack-protection) page.
   2. Enable the **Bot sign-up protection** toggle.

   **For AI agents:** Run `npx clerk@latest config patch --json '{"auth_attack_protection":{"bot_protection":{"captcha_enabled":true}}}'` to enable bot sign-up protection instead of toggling it on the Attack protection page in the Dashboard. Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md?sdk=expo) with `npx skills add clerk/skills` for correct CLI and SDK usage.

   > If your application previously had the **Invisible** CAPTCHA type selected, it's highly recommended to switch to the **Smart** option, as the **Invisible** option is deprecated.
   > For newer applications, CAPTCHA type options are no longer shown in the Dashboard. Bot protection uses the **Smart** option by default and is enabled by turning on the **Bot sign-up protection** toggle only.
2. ## Add the CAPTCHA widget to your custom sign-up form

   > In Expo apps, the CAPTCHA widget renders only on web. On iOS and Android, Clerk skips the browser CAPTCHA challenge, so no CAPTCHA widget or invisible fallback is rendered on native devices.

   To render the CAPTCHA widget in your custom sign-up form, **you need to include the `<View nativeID="clerk-captcha" />` element by the time you call `signUp.create()`**. This element acts as a placeholder onto which the widget will be rendered.

   If this element is not found, the SDK will transparently fall back to an invisible widget in order to avoid breaking your sign-up flow.

   > The invisible widget fallback automatically blocks suspected bot traffic without offering users falsely detected as bots with an opportunity to prove otherwise. Therefore, it's strongly recommended that you ensure the `<View nativeID="clerk-captcha" />` element exists in your sign-up screen.

   The following example shows how to support the CAPTCHA widget:

   ```tsx
   <View>
     <Text>Sign up</Text>
     <TextInput
       autoCapitalize="none"
       keyboardType="email-address"
       value={emailAddress}
       onChangeText={setEmailAddress}
       placeholder="Enter email address"
     />
     <TextInput
       secureTextEntry
       value={password}
       onChangeText={setPassword}
       placeholder="Enter password"
     />

     {/* Clerk's CAPTCHA widget */}
     <View nativeID="clerk-captcha" />

     <Pressable onPress={handleSubmit}>
       <Text>Continue</Text>
     </Pressable>
   </View>
   ```
3. ## Customize the appearance of the CAPTCHA widget

   For custom flows on Expo web, customize the CAPTCHA widget by passing `dataSet` to the `<View nativeID="clerk-captcha" />` element. React Native Web renders these values as `data-cl-*` attributes.

   ```tsx
   <View
     nativeID="clerk-captcha"
     dataSet={{ clTheme: 'dark', clSize: 'flexible', clLanguage: 'es-ES' }}
   />
   ```

   > `dataSet` is a React Native Web prop and isn't part of React Native's `View` types. In a strict TypeScript project, cast the props or augment `ViewProps` to set it.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
