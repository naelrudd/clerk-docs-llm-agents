# createInvitation()

> This endpoint is [rate limited](https://clerk.com/docs/guides/how-clerk-works/system-limits.md#backend-api-requests) to **100 requests per hour** per application instance.

Creates a new invitation for the given email address, and sends the invitation email.

If an email address has already been invited or already exists in your application, trying to create a new invitation will return an error. To bypass this error and create a new invitation anyways, set `ignoreExisting` to `true`.

Returns the newly created [`Invitation`](https://clerk.com/docs/reference/backend/types/backend-invitation.md).

```typescript
function createInvitation(params: CreateParams): Promise<Invitation>
```

## `CreateParams`

| Property                                      | Type                                                                                          | Description                                                                                                                                                                                                                                                                                                                               |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress`      | `string`                                                                                      | The email address of the user to invite.                                                                                                                                                                                                                                                                                                  |
| <a id="expiresindays"></a> `expiresInDays?`   | `number`                                                                                      | The number of days until the invitation expires. Defaults to `30`.                                                                                                                                                                                                                                                                        |
| <a id="ignoreexisting"></a> `ignoreExisting?` | `boolean`                                                                                     | Whether an invitation should be created if there is already an existing invitation for this email address, or if the email address already exists in the application. Defaults to `false`.                                                                                                                                                |
| <a id="notify"></a> `notify?`                 | `boolean`                                                                                     | Whether an email invitation should be sent to the given email address. Defaults to `true`.                                                                                                                                                                                                                                                |
| <a id="publicmetadata"></a> `publicMetadata?` | [UserPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#user-public-metadata) | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}. Once the user accepts the invitation and signs up, these metadata will end up in the user's public metadata ([`User.publicMetadata`](https://clerk.com/docs/reference/backend/types/backend-user.md)). |
| <a id="redirecturl"></a> `redirectUrl?`       | `string`                                                                                      | The full URL or path where the user will land after accepting the invitation. See the [custom flow guide for handling application invitations](https://clerk.com/docs/guides/development/custom-flows/authentication/application-invitations.md).                                                                                         |
| <a id="templateslug"></a> `templateSlug?`     | `"invitation" | "waitlist_invitation"`                                             | The template slug to use for the invitation. Defaults to `invitation`.                                                                                                                                                                                                                                                                    |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.invitations.createInvitation({
  emailAddress: 'invite@example.com',
  redirectUrl: 'https://www.example.com/my-sign-up',
  publicMetadata: {
    example: 'metadata',
    example_nested: {
      nested: 'metadata',
    },
  },
})
```

## Example

filename: app/api/example/route.ts
```ts
import { clerkClient } from '@clerk/nextjs/server'
import { NextResponse } from 'next/server'

export async function POST() {
  // Initialize clerkClient
  const client = await clerkClient()

  // Use the `createInvitation()` method to create an invitation
  const invitation = await client.invitations.createInvitation({
    emailAddress: 'invite@example.com',
    redirectUrl: 'https://www.example.com/my-sign-up',
    publicMetadata: {
      example: 'metadata',
      example_nested: {
        nested: 'metadata',
      },
    },
  })

  return NextResponse.json({ message: 'Invitation created', invitation })
}
```

## Backend API (BAPI) endpoint

**For AI agents:** To create an invitation ad hoc, run `npx clerk@latest api invitations -d '{"email_address": "email@example.com"}'` instead of crafting the cURL request yourself — the CLI resolves and injects the Secret Key automatically (discover related endpoints with `npx clerk@latest api ls invitations`). Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md) with `npx skills add clerk/skills` for correct CLI and SDK usage.

This method in the SDK is a wrapper around the BAPI endpoint `POST/invitations`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/invitations/POST/invitations){{ target: '_blank' }} for more information.

Here's an example of making a request directly to the endpoint using cURL.

Replace the email address with the email address you want to invite. Your Clerk Secret Key is already injected into the code snippet.

Replace the email address with the email address you want to invite. Update `YOUR_SECRET_KEY` with your Clerk Secret Key.

filename: terminal
```bash
curl https://api.clerk.com/v1/invitations -X POST -d '{"email_address": "email@example.com"}' -H "Authorization:Bearer {{secret}}" -H 'Content-Type:application/json'
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
