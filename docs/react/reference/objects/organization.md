# Organization object

The `Organization` object holds information about an Organization, as well as methods for managing it.

To use these methods, you must have the **Organizations** feature [enabled in your app's settings in the Clerk Dashboard](https://clerk.com/docs/guides/organizations/configure.md?sdk=react#enable-organizations).

## Example

The following example uses the [useOrganization()](https://clerk.com/docs/react/reference/hooks/use-organization.md) hook to access the active [Organization](https://clerk.com/docs/react/reference/objects/organization.md) object.

filename: src/components/Organization.tsx
```jsx
import { useOrganization } from '@clerk/react'

export default function Page() {
  const { isLoaded, organization } = useOrganization()

  if (!isLoaded) return <div>Loading...</div>

  return <h1>Welcome to {organization?.name}</h1>
}
```

## Properties

| Property                                                       | Type                                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                               |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="admindeleteenabled"></a> `adminDeleteEnabled`           | `boolean`                                                                                                           | Whether the Organization allows admins to delete users.                                                                                                                                                                                                                                                                                                                   |
| <a id="createdat"></a> `createdAt`                             | `Date`                                                                                                              | The date when the Organization was first created.                                                                                                                                                                                                                                                                                                                         |
| <a id="exclusivemembership"></a> `exclusiveMembership`         | `boolean`                                                                                                           | Whether the Organization enforces exclusive membership, meaning members must have it set as their active Organization. Defaults to `false` for instances that have not adopted the feature.                                                                                                                                                                               |
| <a id="hasimage"></a> `hasImage`                               | `boolean`                                                                                                           | Whether the Organization has an image.                                                                                                                                                                                                                                                                                                                                    |
| <a id="id"></a> `id`                                           | `string`                                                                                                            | The unique identifier for the Organization.                                                                                                                                                                                                                                                                                                                               |
| <a id="imageurl"></a> `imageUrl`                               | `string`                                                                                                            | Holds the Organization's logo. Compatible with Clerk's [Image Optimization](https://clerk.com/docs/guides/development/image-optimization.md?sdk=react).                                                                                                                                                                                                                   |
| <a id="maxallowedmemberships"></a> `maxAllowedMemberships`     | `number`                                                                                                            | The maximum number of memberships allowed in the Organization.                                                                                                                                                                                                                                                                                                            |
| <a id="memberscount"></a> `membersCount`                       | `number`                                                                                                            | The number of members in the Organization.                                                                                                                                                                                                                                                                                                                                |
| <a id="name"></a> `name`                                       | `string`                                                                                                            | The name of the Organization.                                                                                                                                                                                                                                                                                                                                             |
| <a id="pendinginvitationscount"></a> `pendingInvitationsCount` | `number`                                                                                                            | The number of pending invitations in the Organization.                                                                                                                                                                                                                                                                                                                    |
| <a id="publicmetadata"></a> `publicMetadata`                   | [OrganizationPublicMetadata](https://clerk.com/docs/react/reference/types/metadata.md#organization-public-metadata) | Metadata that can be read from both the [Frontend API](https://clerk.com/docs/reference/frontend-api){{ target: '_blank' }} and [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}, but can be set only from the Backend API. Once the user accepts the invitation and signs up, these metadata will end up in the user's public metadata. |
| <a id="selfservessoenabled"></a> `selfServeSSOEnabled`         | `boolean`                                                                                                           | Whether the Organization allows self-serve SSO.                                                                                                                                                                                                                                                                                                                           |
| <a id="slug"></a> `slug`                                       | `null | string`                                                                                          | The URL-friendly identifier of the Organization. If supplied, it must be unique for the instance.                                                                                                                                                                                                                                                                         |
| <a id="updatedat"></a> `updatedAt`                             | `Date`                                                                                                              | The date when the Organization was last updated.                                                                                                                                                                                                                                                                                                                          |

## Methods

### `addMember()`

Adds a user as a member to an organization. A user can only be added to an organization if they are not already a member of it and if they already exist in the same instance as the organization. Only administrators can add members to an organization.

Returns an [OrganizationMembershipResource](https://clerk.com/docs/react/reference/types/organization-membership.md) object.

```typescript
function addMember(params: AddMemberParams): Promise<OrganizationMembershipResource>
```

#### `AddMemberParams`

| Property                     | Type     | Description                                                                                                                                  |
| ---------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="role"></a> `role`     | `string` | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) that will be assigned to the user. |
| <a id="userid"></a> `userId` | `string` | The unique identifier of the user to add as a member.                                                                                        |

### `addPaymentMethod()`

Adds a payment method.

Returns a [BillingPaymentMethodResource](https://clerk.com/docs/react/reference/types/billing-payment-method-resource.md) object.

```typescript
function addPaymentMethod(params: AddPaymentMethodParams): Promise<BillingPaymentMethodResource>
```

#### `AddPaymentMethodParams`

| Property                                 | Type       | Description                                                        |
| ---------------------------------------- | ---------- | ------------------------------------------------------------------ |
| <a id="gateway"></a> `gateway`           | `"stripe"` | The payment gateway to use.                                        |
| <a id="paymenttoken"></a> `paymentToken` | `string`   | A token representing payment details, usually from a payment form. |

### `createDomain()`

Creates a new domain.

Returns an [OrganizationDomainResource](https://clerk.com/docs/react/reference/types/organization-domain-resource.md) object.

> You must have [**Verified domains**](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md?sdk=react) enabled in your app's settings in the Clerk Dashboard.

```typescript
function createDomain(domainName: string, params?: Pick<CreateOrganizationDomainParams, "enrollmentMode">): Promise<OrganizationDomainResource>
```

#### Parameters

| Parameter    | Type                                                                                                                                                            | Description                                                                      |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `domainName` | `string`                                                                                                                                                        | The name of the domain to create.                                                |
| `params?`    | `Pick`<[CreateOrganizationDomainParams](https://clerk.com/docs/react/reference/objects/organization.md#create-organization-domain-params), `"enrollmentMode"`> | Optional parameters, including the `enrollmentMode` to assign to the new domain. |

## `createOrganizationDomainParams`

| Property                                      | Type                                                                                                  | Description                                                                                                            |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| <a id="enrollmentmode"></a> `enrollmentMode?` | `"manual_invitation" | "automatic_invitation" | "automatic_suggestion" | "enterprise_sso"` | The enrollment mode that determines how matching users are added to the Organization. Defaults to `manual_invitation`. |
| <a id="name"></a> `name`                      | `string`                                                                                              | The domain name, for example `clerk.com`.                                                                              |

### `destroy()`

Deletes the Organization. Only administrators can delete an Organization.

Deleting an Organization will also delete all memberships and invitations. **This is not reversible.**

```typescript
function destroy(): Promise<void>
```

### `getDomain()`

Gets a domain for an Organization based on the given domain ID.

Returns an [OrganizationDomainResource](https://clerk.com/docs/react/reference/types/organization-domain-resource.md) object.

> You must have [**Verified domains**](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md?sdk=react) enabled in your app's settings in the Clerk Dashboard.

```typescript
function getDomain(domainId: { domainId: string }): Promise<OrganizationDomainResource>
```

#### Parameters

| Parameter  | Type                               | Description                                 |
| ---------- | ---------------------------------- | ------------------------------------------- |
| `domainId` | `{ domainId: string; }` | The unique identifier of the domain to get. |

### `getDomains()`

Gets the list of domains.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [OrganizationDomainResource](https://clerk.com/docs/react/reference/types/organization-domain-resource.md) objects.

> You must have [**Verified domains**](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md?sdk=react) enabled in your app's settings in the Clerk Dashboard.

```typescript
function getDomains(params?: GetDomainsParams): Promise<ClerkPaginatedResponse<OrganizationDomainResource>>
```

#### `GetDomainsParams`

| Property                                | Type                                                                                                  | Description                                                                                                                                                                          |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `enrollmentMode?`                       | `"manual_invitation" | "automatic_invitation" | "automatic_suggestion" | "enterprise_sso"` | The [enrollment mode](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md?sdk=react#enable-verified-domains) will decide how new users join an organization. |
| <a id="initialpage"></a> `initialPage?` | `number`                                                                                              | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`.                  |
| <a id="pagesize"></a> `pageSize?`       | `number`                                                                                              | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                                          |

### `getInvitations()`

Gets the list of invitations.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [OrganizationInvitationResource](https://clerk.com/docs/react/reference/types/organization-invitation.md) objects.

```typescript
function getInvitations(params?: GetInvitationsParams): Promise<ClerkPaginatedResponse<OrganizationInvitationResource>>
```

#### `GetInvitationsParams`

| Property                                | Type                                                            | Description                                                                                                                                                         |
| --------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number`                                                        | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number`                                                        | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |
| `status?`                               | `("pending" | "accepted" | "revoked" | "expired")[]` | The status of the invitations to get.                                                                                                                               |

### `getMembershipRequests()`

Gets the list of membership requests.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [OrganizationMembershipRequestResource](https://clerk.com/docs/react/reference/types/organization-membership-request.md) objects.

> You must have [**Verified domains** and **Automatic suggestion**](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md?sdk=react) enabled in your app's settings in the Clerk Dashboard.

```typescript
function getMembershipRequests(params?: GetMembershipRequestParams): Promise<ClerkPaginatedResponse<OrganizationMembershipRequestResource>>
```

#### `GetMembershipRequestParams`

| Property                                | Type                                                        | Description                                                                                                                                                         |
| --------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number`                                                    | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number`                                                    | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |
| `status?`                               | `"pending" | "accepted" | "revoked" | "expired"` | The status of the membership requests to get.                                                                                                                       |

### `getMemberships()`

Gets the list of Organization Memberships.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [OrganizationMembershipResource](https://clerk.com/docs/react/reference/types/organization-membership.md) objects.

```typescript
function getMemberships(params?: GetMembersParams): Promise<ClerkPaginatedResponse<OrganizationMembershipResource>>
```

#### `GetMembersParams`

| Property                                | Type                                                                                                                                | Description                                                                                                                                                         |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number`                                                                                                                            | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number`                                                                                                                            | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |
| `query?`                                | `string`                                                                                                                            | The query to filter the users by.                                                                                                                                   |
| `role?`                                 | <code><a href="https://clerk.com/docs/react/reference/types/organization-custom-role-key.md">OrganizationCustomRoleKey</a>[]</code> | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) to filter the users by.                                   |

### `getPaymentMethods()`

Gets a list of payment methods that have been stored.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [BillingPaymentMethodResource](https://clerk.com/docs/react/reference/types/billing-payment-method-resource.md) objects.

```typescript
function getPaymentMethods(params?: GetPaymentMethodsParams): Promise<ClerkPaginatedResponse<BillingPaymentMethodResource>>
```

#### `GetPaymentMethodsParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

### `getRoles()`

Gets the list of [Roles](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) available.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/react/reference/types/clerk-paginated-response.md) of [RoleResource](https://clerk.com/docs/react/reference/types/role-resource.md) objects and a `has_role_set_migration` status.

When `has_role_set_migration` is `true`, updating Organization membership Roles is not allowed. Learn how to [build a custom flow for managing member Roles in an Organization](https://clerk.com/docs/guides/development/custom-flows/organizations/manage-roles.md?sdk=react).

```typescript
function getRoles(params?: GetRolesParams): Promise<GetRolesResponse>
```

#### `GetRolesParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

### `initializePaymentMethod()`

Initializes a payment method.

Returns a [BillingInitializedPaymentMethodResource](https://clerk.com/docs/react/reference/types/billing-initialized-payment-method-resource.md) object.

```typescript
function initializePaymentMethod(params: InitializePaymentMethodParams): Promise<BillingInitializedPaymentMethodResource>
```

#### `InitializePaymentMethodParams`

| Property                       | Type       | Description                 |
| ------------------------------ | ---------- | --------------------------- |
| <a id="gateway"></a> `gateway` | `"stripe"` | The payment gateway to use. |

### `inviteMember()`

Creates and sends an invitation to the given email address.

Returns an [OrganizationInvitationResource](https://clerk.com/docs/react/reference/types/organization-invitation.md) object.

```typescript
function inviteMember(params: InviteMemberParams): Promise<OrganizationInvitationResource>
```

#### `InviteMemberParams`

| Property                                 | Type     | Description                                                                                                                                  |
| ---------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddress"></a> `emailAddress` | `string` | The email address of the user to invite.                                                                                                     |
| <a id="role"></a> `role`                 | `string` | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) that will be assigned to the user. |

### `inviteMembers()`

Creates and sends invitations to the given email addresses.

Returns an array of [OrganizationInvitationResource](https://clerk.com/docs/react/reference/types/organization-invitation.md) objects.

```typescript
function inviteMembers(params: InviteMembersParams): Promise<OrganizationInvitationResource[]>
```

#### `InviteMembersParams`

| Property                                     | Type                  | Description                                                                                                                                   |
| -------------------------------------------- | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="emailaddresses"></a> `emailAddresses` | `string[]` | The email addresses of the users to invite.                                                                                                   |
| <a id="role"></a> `role`                     | `string`              | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) that will be assigned to the users. |

### `attemptOwnershipVerification()`

Completes the verification process started by [prepareOwnershipVerification()](https://clerk.com/docs/react/reference/objects/organization.md#prepare-ownership-verification), by resolving the published TXT record for each of the given domains in a single request. A single bad domain does not fail the batch; it lands in the returned [OrganizationDomainsBulkOwnershipVerificationResource](https://clerk.com/docs/react/reference/types/organization-domains-bulk-ownership-verification-resource.md) object's `errors` array.

Returns an [OrganizationDomainsBulkOwnershipVerificationResource](https://clerk.com/docs/react/reference/types/organization-domains-bulk-ownership-verification-resource.md) object.

```typescript
function attemptOwnershipVerification(domainIds: string[]): Promise<OrganizationDomainsBulkOwnershipVerificationResource>
```

#### Parameters

| Parameter   | Type                  | Description                                       |
| ----------- | --------------------- | ------------------------------------------------- |
| `domainIds` | `string[]` | The unique identifiers of the domains to attempt. |

### `prepareOwnershipVerification()`

Starts the verification process of multiple [Verified Domains](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md?sdk=react) at once by issuing a fresh TXT challenge for each of the given domains in a single request. Each resolved domain's `ownershipVerification` property carries the `txtRecordName` and `txtRecordValue` the Organization [admin](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) must publish. A single bad domain does not fail the batch; it lands in the returned [OrganizationDomainsBulkOwnershipVerificationResource](https://clerk.com/docs/react/reference/types/organization-domains-bulk-ownership-verification-resource.md) object's `errors` array.

Returns an [OrganizationDomainsBulkOwnershipVerificationResource](https://clerk.com/docs/react/reference/types/organization-domains-bulk-ownership-verification-resource.md) object.

```typescript
function prepareOwnershipVerification(domainIds: string[]): Promise<OrganizationDomainsBulkOwnershipVerificationResource>
```

#### Parameters

| Parameter   | Type                  | Description                                       |
| ----------- | --------------------- | ------------------------------------------------- |
| `domainIds` | `string[]` | The unique identifiers of the domains to prepare. |

### `reload()`

Reloads the resource, which is useful when you want to access the latest user data after performing a mutation. To make the updated data immediately available, this method forces a session token refresh instead of waiting for the automatic refresh cycle that could temporarily retain stale information. Learn more about [forcing a token refresh](https://clerk.com/docs/guides/sessions/force-token-refresh.md?sdk=react).

```typescript
function reload(p?: ClerkResourceReloadParams): Promise<OrganizationResource>
```

#### `ClerkResourceReloadParams`

| Property                                              | Type     | Description                                                                                                                                                                   |
| ----------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="rotatingtokennonce"></a> `rotatingTokenNonce?` | `string` | A nonce to use for rotating the user's token. Used in native application OAuth flows to allow the native client to update its JWT once despite changes in its rotating token. |

### `removeMember()`

Removes a member.

Returns an [OrganizationMembershipResource](https://clerk.com/docs/react/reference/types/organization-membership.md) object.

```typescript
function removeMember(userId: string): Promise<OrganizationMembershipResource>
```

#### Parameters

| Parameter | Type     | Description                                  |
| --------- | -------- | -------------------------------------------- |
| `userId`  | `string` | The unique identifier of the user to remove. |

### `setLogo()`

Sets or replaces an Organization's logo.

```typescript
function setLogo(params: SetOrganizationLogoParams): Promise<OrganizationResource>
```

#### `SetOrganizationLogoParams`

| Property                 | Type                                     | Description                                                                                            |
| ------------------------ | ---------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| <a id="file"></a> `file` | `null | string | Blob | File` | The file to set as the Organization's logo. The file must be an image and its size cannot exceed 10MB. |

### `update()`

Updates the current Organization.

```typescript
function update(params: UpdateOrganizationParams): Promise<OrganizationResource>
```

#### `UpdateOrganizationParams`

| Property                  | Type     | Description                                                                                       |
| ------------------------- | -------- | ------------------------------------------------------------------------------------------------- |
| <a id="name"></a> `name`  | `string` | The name of the Organization.                                                                     |
| <a id="slug"></a> `slug?` | `string` | The URL-friendly identifier of the Organization. If supplied, it must be unique for the instance. |

### `updateMember()`

Updates a given member.

Returns an [OrganizationMembershipResource](https://clerk.com/docs/react/reference/types/organization-membership.md) object.

```typescript
function updateMember(params: UpdateMembershipParams): Promise<OrganizationMembershipResource>
```

#### `UpdateMembershipParams`

| Property                     | Type     | Description                                                                                                                                  |
| ---------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="role"></a> `role`     | `string` | The [Role](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=react) that will be assigned to the user. |
| <a id="userid"></a> `userId` | `string` | The unique identifier of the user to update.                                                                                                 |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
