# SSOBypassAllowlistResource

The `SSOBypassAllowlistResource` object lets you manage which Organization members can sign in with an email code instead of using their enterprise single sign-on (SSO) connection. Access these methods through [organization.ssoBypassAllowlist](https://clerk.com/docs/vue/reference/objects/organization.md#properties).

These methods only manage the allowlists of the Organization's own enterprise connections. To manage the allowlist for every connection on the instance, use the [Clerk Dashboard or the Backend API](https://clerk.com/docs/guides/configure/auth-strategies/enterprise-connections/sso-bypass.md?sdk=vue#manage-the-allowlist).

> These methods require the `org:sys_entconns_sso_bypass:manage` [System Permission](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md?sdk=vue#system-permissions).

## Methods

### `getUsers()`

Lists the Organization members on the SSO bypass allowlist. Returns an array of [SSOBypassAllowlistUserResource](https://clerk.com/docs/vue/reference/types/sso-bypass-allowlist-resource.md#ssobypassallowlistuserresource) objects.

```typescript
function getUsers(): Promise<SSOBypassAllowlistUserResource[]>
```

### `addUser()`

Adds an Organization member to the allowlist. The member must have a verified email address on a domain served by one of the Organization's enterprise connections. Returns the member's [SSOBypassAllowlistUserResource](https://clerk.com/docs/vue/reference/types/sso-bypass-allowlist-resource.md#ssobypassallowlistuserresource) object. Adding a member who's already on the allowlist returns their existing entry.

```typescript
function addUser(params: { userId: string }): Promise<SSOBypassAllowlistUserResource>
```

#### Parameters

| Name   | Type   | Description                               |
| ------ | ------ | ----------------------------------------- |
| userId | string | The ID of the Organization member to add. |

### `addUsers()`

Adds Organization members to the allowlist. The method sends one request per 100 IDs, one after another. If a request fails, the promise rejects, and members added by earlier requests stay on the allowlist.

```typescript
function addUsers(params: { userIds: string[] }): Promise<SSOBypassAllowlistBulkCreateResult>
```

#### Parameters

| Name    | Type      | Description                                 |
| ------- | --------- | ------------------------------------------- |
| userIds | string[] | The IDs of the Organization members to add. |

#### Returns

`addUsers()` returns an `SSOBypassAllowlistBulkCreateResult` object with the following properties:

| Name   | Type                                 | Description                                                                                                                                                                                                                                                                      |
| ------ | ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| data   | SSOBypassAllowlistUserResource[]    | The members on the allowlist, including members who were already on it.                                                                                                                                                                                                          |
| errors | { userId: string, code: string }[] | The members who couldn't be added. The code is resource\_not\_found when the user isn't a member of the Organization, and sso\_bypass\_domain\_not\_served when the member has no verified email address on a domain served by one of the Organization's enterprise connections. |

An error for one member doesn't prevent other members from being added.

### `removeUser()`

Removes an Organization member from the allowlist. Entries on enterprise connections outside the Organization aren't affected. Returns a [DeletedObjectResource](https://clerk.com/docs/vue/reference/types/deleted-object-resource.md) object.

```typescript
function removeUser(userId: string): Promise<DeletedObjectResource>
```

#### Parameters

| Name   | Type   | Description                                  |
| ------ | ------ | -------------------------------------------- |
| userId | string | The ID of the Organization member to remove. |

## `SSOBypassAllowlistUserResource`

An Organization member's entry on the SSO bypass allowlist.

| Name           | Type           | Description                                             |
| -------------- | -------------- | ------------------------------------------------------- |
| createdAt      | Date           | The date when the member was added to the allowlist.    |
| id             | string         | The unique identifier for the entry. Same as userId.    |
| publicUserData | PublicUserData | Information about the member that's publicly available. |
| updatedAt      | Date           | The date when the entry was last updated.               |
| userId         | string         | The ID of the member.                                   |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
