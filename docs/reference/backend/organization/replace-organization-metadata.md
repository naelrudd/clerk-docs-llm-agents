# replaceOrganizationMetadata()

Replaces the metadata associated with the specified Organization. Unlike [`updateOrganizationMetadata()`](https://clerk.com/docs/reference/backend/organization/update-organization-metadata.md), which deep-merges into the existing metadata, this method uses replace semantics: when a metadata field is provided, its previous value is overwritten in full with no merging at any level.

The distinction is at two layers:

- **Top-level field omission preserves the existing value.** Each top-level field (`publicMetadata`, `privateMetadata`) is handled independently. If you don't include a field in the request, the stored value for that field is left untouched.
- **The value inside a provided field is replaced in full.** When you do include a field, its previous content is discarded — any nested keys present before but absent in the new value are dropped. There is no merge.

For the provided field, you can also send:

- `{}` (empty object) to clear the field.
- `null` to overwrite the field with a JSON `null` value. Prefer `{}` unless you specifically need a stored `null`.

Returns the updated [`Organization`](https://clerk.com/docs/reference/backend/types/backend-organization.md).

```typescript
function replaceOrganizationMetadata(organizationId: string, params: { privateMetadata?: OrganizationPrivateMetadata; publicMetadata?: OrganizationPublicMetadata }): Promise<Organization>
```

## Parameters

| Parameter                 | Type                                                                                                                                                                                                                                                                                                      | Description                                                                                                                                                                      |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `organizationId`          | `string`                                                                                                                                                                                                                                                                                                  | The ID of the Organization to replace the metadata for.                                                                                                                          |
| `params`                  | <code>{ privateMetadata?: <a href="https://clerk.com/docs/reference/types/metadata.md#organization-private-metadata">OrganizationPrivateMetadata</a>; publicMetadata?: <a href="https://clerk.com/docs/reference/types/metadata.md#organization-public-metadata">OrganizationPublicMetadata</a>; }</code> | The metadata to replace.                                                                                                                                                         |
| `params.privateMetadata?` | [OrganizationPrivateMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-private-metadata)                                                                                                                                                                                           | Metadata that can be read and set only from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.                                               |
| `params.publicMetadata?`  | [OrganizationPublicMetadata](https://clerk.com/docs/reference/types/metadata.md#organization-public-metadata)                                                                                                                                                                                             | Metadata that can be read from the Frontend API and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}, but can be set only from the Backend API. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const organizationId = 'org_123'

const response = await clerkClient.organizations.replaceOrganizationMetadata(organizationId, {
  publicMetadata: {
    tier: 'enterprise',
  },
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PUT/organizations/{organization_id}/metadata`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/organizations/PUT/organizations/%7Borganization_id%7D/metadata){{ target: '_blank' }} for more information.

Here's an example of making a request directly to the endpoint using cURL.

Replace `YOUR_SECRET_KEY` with your Clerk Secret Key. You can find your Secret Key on the [**API keys**](https://dashboard.clerk.com/~/api-keys) page in the Clerk Dashboard.

filename: curl.sh
```bash
curl -XPUT -H 'Authorization: Bearer {{secret}}' -H "Content-type: application/json" -d '{
  "public_metadata": {
    "tier": "enterprise"
  }
}' 'https://api.clerk.com/v1/organizations/{organization_id}/metadata'
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
