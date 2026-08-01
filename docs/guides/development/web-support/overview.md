# Web support

Expo provides a way to [develop web applications](https://docs.expo.dev/workflow/web/) using the same codebase as your iOS and Android apps. Clerk provides prebuilt components for Expo web projects through `@clerk/expo/web` and prebuilt native components for iOS and Android through `@clerk/expo/native`.

## Create a new project with web support

If you're starting from scratch, follow the [Expo quickstart](https://clerk.com/docs/expo/getting-started/quickstart.md), which shows the available Expo authentication approaches and how to choose the components that match each platform.

## Add web support to an existing project

If you already have an Expo project and want to add web support, you must first ensure that your existing Clerk [custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md) do not have any native-specific code. If you have any native-specific code you will have to either adjust your custom flows to also work on web by leveraging [platform-specific code](https://reactnative.dev/docs/platform-specific-code#platform-specific-extensions), if you are using Expo Router you can also take a look at the [platform-specific modules](https://docs.expo.dev/router/advanced/platform-specific-modules/) guide.

> Use the components that match the platform. Use [web components](https://clerk.com/docs/reference/components/overview.md) from `@clerk/expo/web` for Expo web projects, and use [native components](https://clerk.com/docs/reference/expo/native-components/overview.md) from `@clerk/expo/native` for iOS and Android.

## Next steps

Learn more about Clerk components, how to build custom flows, and how to use Clerk's client-side helpers using the following guides.

- [Create a custom sign-up page](https://clerk.com/docs/guides/development/web-support/custom-sign-up-page.md): Learn how to add a custom sign-up page to your app with Clerk's components.
- [Prebuilt components](https://clerk.com/docs/reference/components/overview.md): Learn how to quickly add authentication to your app using Clerk's suite of components.
- [Customization & localization](https://clerk.com/docs/guides/customizing-clerk/appearance-prop/overview.md): Learn how to customize and localize Clerk components.
- [Build custom flows](https://clerk.com/docs/guides/development/custom-flows/overview.md): Learn how to build custom user interfaces entirely from scratch using the Clerk API.
- [Client-side helpers](https://clerk.com/docs/reference/expo/overview.md#react-hooks): Learn more about Clerk's client-side helpers and how to use them.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
