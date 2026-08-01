# updateOrganizationSettings()

Updates the [Organization-related settings](https://clerk.com/docs/guides/organizations/configure.md) for the current instance.

Returns the updated [`OrganizationSettings`](https://clerk.com/docs/reference/backend/types/backend-organization-settings.md) object.

```typescript
function updateOrganizationSettings(params: UpdateOrganizationSettingsParams): Promise<OrganizationSettings>
```

## `UpdateOrganizationSettingsParams`

| Property                                                      | Type                        | Description                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------------------------- | --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="admindeleteenabled"></a> `adminDeleteEnabled?`         | `boolean | null` | Whether [Organization admins](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md#default-roles) are allowed to delete Organizations.                                                                                                                                                                               |
| <a id="creatorroleid"></a> `creatorRoleId?`                   | `string | null`  | Specifies what the default Organization [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) is for an Organization creator.                                                                                                                                                                                 |
| <a id="domainsdefaultroleid"></a> `domainsDefaultRoleId?`     | `string | null`  | Specifies what the default Organization [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) is for the Organization's [Verified Domains](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md).                                                                                      |
| <a id="domainsenabled"></a> `domainsEnabled?`                 | `boolean | null` | Whether [Verified Domains](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md) are enabled for Organizations.                                                                                                                                                                                                              |
| <a id="domainsenrollmentmodes"></a> `domainsEnrollmentModes?` | `string[]`       | Specifies which [enrollment modes](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md#enable-verified-domains) to enable for your Organization's [Verified Domains](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md). Supported modes are `'automatic_invitation'` & `'automatic_suggestion'`. |
| <a id="enabled"></a> `enabled?`                               | `boolean | null` | Whether the instance should enable [Organizations](https://clerk.com/docs/guides/organizations/overview.md).                                                                                                                                                                                                                                        |
| <a id="maxallowedmemberships"></a> `maxAllowedMemberships?`   | `number | null`  | The maximum number of [memberships allowed](https://clerk.com/docs/guides/organizations/configure.md#membership-limits) per Organization.                                                                                                                                                                                                           |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.instances.updateOrganizationSettings({
  enabled: true,
  maxAllowedMemberships: 10,
  adminDeleteEnabled: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/instance/organization_settings`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/instance-settings/PATCH/instance/organization_settings){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
