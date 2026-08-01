# getOrganizationSettings()

Gets the [Organization-related settings](https://clerk.com/docs/guides/organizations/configure.md) for the current instance.

Returns the [`OrganizationSettings`](https://clerk.com/docs/reference/backend/types/backend-organization-settings.md) object.

```typescript
function getOrganizationSettings(): Promise<OrganizationSettings>
```

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.instances.getOrganizationSettings()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/instance/organization_settings`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/instance-settings/GET/instance/organization_settings){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
