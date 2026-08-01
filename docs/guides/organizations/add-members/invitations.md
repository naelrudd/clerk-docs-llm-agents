# Invite users to your Organization

Organization invitations let you add new members to your Organization. When you send an invitation, Clerk sends an email to the invited user with a unique invitation link. When the user visits the Organization invitation link, Clerk redirects them to the [Account Portal sign-in page](https://clerk.com/docs/guides/account-portal/overview.md#sign-in). If the user is already signed in, Clerk redirects them to your application's homepage (`/`). If you want to redirect the user to a specific page in your application, you can [specify a redirect URL when creating the invitation](#redirect-url).

By default, only [admins](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md#default-roles) can invite users to an Organization.

This feature requires that [**Email** is enabled](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md#email), as Clerk uses the user's email address to send the invitation. If you don't want to enable **Email** for your application, you can bypass the invitation flow completely and add existing users directly to the Organization with the [`createOrganizationMembership()`](https://clerk.com/docs/reference/backend/organization/create-organization-membership.md) method. Because this method requires the user's ID, the user must already have a Clerk account.

**For AI agents:** Instead of hand-writing cURL requests to the Backend API, send an invitation with the CLI: `npx clerk@latest api organizations/<org_id>/invitations -d '{"email_address":"email@example.com","role":"org:member"}'` (discover related endpoints, like bulk create and revoke, via `npx clerk@latest api ls invitations`). Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md) with `npx skills add clerk/skills` for correct CLI and SDK usage.

## When to use invitations

Invitations work well when you need precise control over who joins your Organization and which Role they receive. This approach fits scenarios where:

- Teams are small and members are known in advance.
- Onboarding requires manual approval or review.
- Specific Roles need to be assigned during the invitation.

If you want to streamline enrollment for users with company email addresses, consider [Verified Domains](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md), which can automatically invite users based on their email domain. If customers require centralized authentication through their Identity Provider, use [Enterprise SSO](https://clerk.com/docs/guides/organizations/add-members/sso.md).

## Create an invitation

Clerk's [prebuilt components](https://clerk.com/docs/reference/components/overview.md) and [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md) manage all Organization invitation flows, including creating, managing, and accepting invitations.

However, if you want to build custom flows, see the following sections.

### Client-side

To create an Organization invitation on the client-side, see the [dedicated guide](https://clerk.com/docs/guides/development/custom-flows/organizations/manage-organization-invitations.md). Note that this uses the [organizations.inviteMember()](https://clerk.com/docs/reference/objects/organization.md#invite-member) method, which does not let you specify a redirect URL; the invitation links will always redirect to the Account Portal sign-in page. If you want to specify a redirect URL, you must create the invitation on the server-side.

### Server-side

To create Organization invitations on the server-side, use the Backend API by either calling the endpoint directly or using [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md). `clerkClient` is a wrapper around the Backend API that makes it easier to interact with the API. If you receive a `429` response, respect the `Retry-After` header before retrying.

Use the following tabs to see examples for each method.

**cURL**

The following example demonstrates how to send a single Organization invitation using the [`POST /v1/organizations/{organization_id}/invitations` endpoint](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/POST/organizations/%7Borganization_id%7D/invitations){{ target: '_blank' }}. This endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests) to **250 requests per hour** per application instance.

- Your Secret Key is already injected into the code snippet.
- Replace the `org_123` with the ID of the Organization you want to invite the user to.
- Replace the `user_123` with the ID of the user who is inviting the other user.
- Replace the email address with the email address you want to invite.
- Replace the `role` with the role you want to assign to the invited user.

* Replace `YOUR_SECRET_KEY` with your Clerk Secret Key.
* Replace the `org_123` with the ID of the Organization you want to invite the user to.
* Replace the `user_123` with the ID of the user who is inviting the other user.
* Replace the email address with the email address you want to invite.
* Replace the `role` with the Role you want to assign to the invited user.

filename: terminal
```bash
curl 'https://api.clerk.com/v1/organizations/{org_123}/invitations' \
-X POST \
-H 'Authorization: Bearer {{secret}}' \
-H 'Content-Type: application/json' \
-d '{ "inviter_user_id": "user_123", "email_address": "email@example.com", "role": "org:member" }'
```

The following example demonstrates how to send multiple Organization invitations in one request using the [`POST /v1/organizations/{organization_id}/invitations/bulk` endpoint](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/POST/organizations/%7Borganization_id%7D/invitations/bulk){{ target: '_blank' }}. This endpoint is **limited to a maximum of 10 invitations per API call**. If you need to send more invitations, please make multiple requests. This endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests) to **50 requests per hour** per application instance.

filename: terminal
```bash
curl 'https://api.clerk.com/v1/organizations/{org_123}/invitations/bulk' \
-X POST \
-H 'Authorization: Bearer {{secret}}' \
-H 'Content-Type: application/json' \
-d '[{ "inviter_user_id": "user_123", "email_address": "email123@example.com", "role": "org:member" }, { "inviter_user_id": "user_456", "email_address": "email456@example.com", "role": "org:member" }]'
```

**clerkClient**

To use [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md) to send a single invitation, see the [`createOrganizationInvitation()`](https://clerk.com/docs/reference/backend/organization/create-organization-invitation.md) reference documentation. To invite multiple users in one request, see the [`createOrganizationInvitationBulk()`](https://clerk.com/docs/reference/backend/organization/create-organization-invitation-bulk.md) reference documentation.

### Redirect URL

When you create an invitation, you can specify a `redirect_url` parameter. This parameter tells Clerk where to redirect the user when they visit the invitation link.

**cURL**

The following example demonstrates how to set the `redirect_url` parameter on the `POST /v1/organizations/{organization_id}/invitations` endpoint.

filename: terminal
```bash
curl 'https://api.clerk.com/v1/organizations/{org_123}/invitations' \
  -X POST \
  -H 'Authorization: Bearer {{secret}}' \
  -H 'Content-Type: application/json' \
  -d '{ "inviter_user_id": "user_123", "email_address": "email@example.com", "role": "org:member", "redirect_url": "https://www.example.com/accept-invitation" }'
```

**clerkClient**

[`createOrganizationInvitation()`](https://clerk.com/docs/reference/backend/organization/create-organization-invitation.md) accepts a `redirectUrl` parameter. For [`createOrganizationInvitationBulk()`](https://clerk.com/docs/reference/backend/organization/create-organization-invitation-bulk.md), set `redirectUrl` on each invitation object in the `params` array.

Once the user visits the invitation link, they will be redirected to the page you specified. On that page, you must handle the authentication flow in your code. You can either embed the [<SignIn />](https://clerk.com/docs/reference/components/authentication/sign-in.md) component or, if the prebuilt component doesn't meet your needs or you require more control over the logic, you can build a [custom flow](https://clerk.com/docs/guides/development/custom-flows/organizations/accept-organization-invitations.md).

> To test redirect URLs in your development environment, pass your port. For example, `http://localhost:3000/accept-invitation`.

### Invitation metadata

You can also add metadata to an invitation when creating the invitation through the Backend API. Once the invited user signs up using the invitation link, Clerk stores the **invitation** metadata (`OrganizationInvitation.publicMetadata`) in the Organization **membership's** metadata (`OrganizationMembership.publicMetadata`). For more details on Organization membership metadata, see the [OrganizationMembership](https://clerk.com/docs/reference/types/organization-membership.md) reference.

**cURL**

The following example demonstrates how to set the `public_metadata` parameter on the `POST /v1/organizations/{organization_id}/invitations` endpoint.

filename: terminal
```bash
curl 'https://api.clerk.com/v1/organizations/{org_123}/invitations' \
  -X POST \
  -H 'Authorization: Bearer {{secret}}' \
  -H 'Content-Type: application/json' \
  -d '{ "inviter_user_id": "user_123", "email_address": "email@example.com", "role": "org:member", "public_metadata": {"department": "marketing"} }'
```

**clerkClient**

[`createOrganizationInvitation()`](https://clerk.com/docs/reference/backend/organization/create-organization-invitation.md) accepts a `publicMetadata` parameter. For [`createOrganizationInvitationBulk()`](https://clerk.com/docs/reference/backend/organization/create-organization-invitation-bulk.md), set `publicMetadata` on each invitation object in the `params` array.

## Revoke an invitation

Revoking an invitation prevents the user from using the invitation link that was sent to them.

### Client-side

To revoke an invitation client-side, see the [dedicated guide](https://clerk.com/docs/guides/development/custom-flows/organizations/manage-organization-invitations.md).

### Server-side

To revoke an invitation server-side, use the Backend API by either calling the endpoint directly or using [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md). `clerkClient` is a wrapper around the Backend API that makes it easier to interact with the API.

Use the following tabs to see examples for each method.

**cURL**

The following example demonstrates how to revoke an invitation using the [`POST /v1/organizations/{organization_id}/invitations/{invitation_id}/revoke` endpoint](https://clerk.com/docs/reference/backend-api/tag/organization-invitations/POST/organizations/%7Borganization_id%7D/invitations/%7Binvitation_id%7D/revoke){{ target: '_blank' }}.

- Your Secret Key is already injected into the code snippet.
- Replace the `inv_123` with the ID of the invitation you want to revoke.
- Replace the `user_123` with the ID of the user who is revoking the invitation.

* Replace `YOUR_SECRET_KEY` with your Clerk Secret Key.
* Replace the `inv_123` with the ID of the invitation you want to revoke.
* Replace the `user_123` with the ID of the user who is revoking the invitation.

filename: terminal
```bash
curl 'https://api.clerk.com/v1/organizations/{org_123}/invitations/{inv_123}/revoke' \
  -X POST \
  -H 'Authorization: Bearer {{secret}}' \
  -H 'Content-Type: application/json' \
  -d '{ "requesting_user_id": "user_123" }'
```

**clerkClient**

To use [`clerkClient`](https://clerk.com/docs/reference/backend/overview.md) to revoke an Organization invitation, see the [`revokeOrganizationInvitation()`](https://clerk.com/docs/reference/backend/organization/revoke-organization-invitation.md) reference documentation.

## Next steps

Now that you understand how to invite users to your Organization, you can:

- [Add custom Organization metadata](https://clerk.com/docs/guides/organizations/metadata.md): Learn how to store custom information about an Organization that is not part of the standard fields.
- [Configure Organization settings](https://clerk.com/docs/guides/organizations/configure.md): Learn how to configure Organization settings.
- [Set up Enterprise SSO Connections](https://clerk.com/docs/guides/organizations/add-members/sso.md): Learn how to set up Enterprise SSO Connections for centralized authentication through an Identity Provider.
- [Set up Roles and Permissions](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md): Learn how to set up Roles and Permissions to control what invited users can access.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
