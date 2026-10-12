# Authorization checks

It's best practice to always verify whether or not a user is **authorized** to access sensitive information, important content, or exclusive features. **Authorization** is the process of determining the access rights and privileges of a user, ensuring they have the necessary permissions to perform specific actions.

Clerk provides two main features that can be used to implement authorization checks:

- [Organizations](https://clerk.com/docs/guides/organizations/overview.md?sdk=android)
  - Users can be assigned [Roles and Permissions](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=android#permissions)
  - Useful for Role-based and Permission-based access control
- [Billing](https://clerk.com/docs/guides/billing/overview.md?sdk=android)
  - Users can subscribe to Plans and Features
  - Useful for Subscription-based and Feature-based access control

In your Android application, use `Clerk.has()` to check whether the signed-in user is authorized. It returns `false` when no user is signed in, and when the session isn't active, for example while the user still has [session tasks](https://clerk.com/docs/guides/configure/session-tasks.md?sdk=android) to complete.

## Important considerations

- When doing authorization checks, it's recommended to use Permission-based over Role-based, and Feature-based over Plan-based authorization, as these approaches are more granular, flexible, and more secure.
- Checking for a Role or Permission depends on the user having an Active Organization. Without an Active Organization, Role and Permission checks return `false`.
- `has()` runs on the device and only controls what your app shows. Always check authorization again on your backend before returning protected data or performing a protected action. See the Backend [`has()`](https://clerk.com/docs/reference/backend/types/auth-object.md?sdk=android#has) helper.

## Check Roles and Permissions

```kotlin
if (Clerk.has(permission = "org:invoices:create")) {
    // Create the invoice.
}

if (Clerk.has(role = "org:admin")) {
    // Show admin actions.
}
```

`Clerk.has()` reads the session at the moment you call it. In a composable, collect `Clerk.sessionFlow` and call [checkAuthorization()](https://clerk.com/docs/android/reference/native-mobile/auth.md#check-authorization) on the session so the UI updates when the session changes. `checkAuthorization()` doesn't check the session's status, so only call it on an active session to match `Clerk.has()`.

```kotlin
@Composable
fun InvoiceActions() {
    val session by Clerk.sessionFlow.collectAsState()
    val activeSession = session?.takeIf { it.status == Session.SessionStatus.ACTIVE }

    if (activeSession?.checkAuthorization(permission = "org:invoices:create") == true) {
        Button(onClick = { /* Create the invoice. */ }) {
            Text("Create invoice")
        }
    }
}
```

## Check Plans and Features

A Plan or Feature slug without a prefix matches either the user's or the Active Organization's Subscription. Prefix it with `user:` or `org:` to check only one of them.

```kotlin
if (Clerk.has(feature = "widgets")) {
    // Show the widgets Feature.
}

if (Clerk.has(plan = "org:gold")) {
    // Show content for Organizations on the Gold Plan.
}
```

Plan and Feature checks read the current session token, so a Subscription change is reflected after the session token refreshes. To read Subscription details, use the [Billing APIs](https://clerk.com/docs/android/reference/native-mobile/billing.md).

## Require recent reverification

Pass a `reverification` requirement to check whether the user has [reverified](https://clerk.com/docs/guides/secure/reverification.md?sdk=android) recently. You can check it on its own, or together with other conditions. When you pass more than one condition, `has()` returns `true` only if all of them pass.

```kotlin
if (Clerk.has(reverification = ReverificationConfig.Strict)) {
    // The user reverified in the last 10 minutes.
}

if (Clerk.has(permission = "org:invoices:delete", reverification = ReverificationConfig.Moderate)) {
    // Show the Delete invoice button.
}

val recentlyVerified =
    Clerk.has(
        reverification = ReverificationConfig.Custom(
            level = SessionVerification.Level.FIRST_FACTOR,
            afterMinutes = 30,
        ),
    )
```

The reverification presets are:

| Preset                           | Level         | Maximum age |
| -------------------------------- | ------------- | ----------- |
| `ReverificationConfig.StrictMfa` | Multi-factor  | 10 minutes  |
| `ReverificationConfig.Strict`    | Second factor | 10 minutes  |
| `ReverificationConfig.Moderate`  | Second factor | 1 hour      |
| `ReverificationConfig.Lax`       | Second factor | 1 day       |

For a user who hasn't set up a second factor, the second-factor and multi-factor presets accept a recent first factor instead.

## Check a specific session

`Clerk.has()` checks the current session, and only when it's active. To check another session, for example in an app that supports [multiple sessions](https://clerk.com/docs/guides/secure/session-options.md?sdk=android#multi-session-applications), call [checkAuthorization()](https://clerk.com/docs/android/reference/native-mobile/auth.md#check-authorization) on that `Session` with the same arguments.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
