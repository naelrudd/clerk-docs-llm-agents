# User profile

The user profile page in the Clerk Dashboard gives you a detailed view of an individual user's identity and data. To access a user's profile, navigate to the [**Users**](https://dashboard.clerk.com/~/users) page and select a user.

## User details

The user profile surfaces the user's profile information, including:

- Personal information (name, avatar, etc.)
- Identifiers (email addresses, phone numbers, connected accounts)
- Metadata (public, private, and unsafe metadata attached to the account)

You can also manage the user's account directly from this section, including updating their information, impersonating, banning, blocking, or deleting the user. For more information on impersonating users, including how to detect impersonated sessions in your application, see the [User impersonation](https://clerk.com/docs/guides/users/impersonation.md) guide.

## Organizations

If your application uses [Clerk Organizations](https://clerk.com/docs/guides/organizations/overview.md), this section shows which organizations the user is a member of.

## Billing

> Billing regularly introduces new features and UI changes to Clerk's components. If you'd like to remain on a specific version of Clerk's components or SDK, you can follow the steps in the [pinning](https://clerk.com/docs/pinning.md) documentation.

If your application uses [Clerk Billing](https://clerk.com/docs/guides/billing/overview.md), the user profile includes a **Billing** tab showing the user's subscription activity, statements, and payments. The following financial metrics are also surfaced on the user profile:

- **MRR** - The user's current monthly recurring revenue contribution.
- **Lifetime revenue** - The total amount of money the user has paid over their lifetime.
- **LTV** - Lifetime value, the estimated value of this user calculated as average MRR divided by churn rate.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
