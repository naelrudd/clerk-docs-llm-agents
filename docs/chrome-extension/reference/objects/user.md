# User object

The `User` object holds all of the information for a single user of your application and provides a set of methods to manage their account. Each `User` has at least one authentication identifier, which might be their email address, phone number, or a username.

A user can be contacted at their primary email address or primary phone number. They can have more than one registered email address or phone number, but only one of them will be their primary email address (`User.primaryEmailAddress`) or primary phone number (`User.primaryPhoneNumber`). At the same time, a user can also have one or more external accounts by connecting to [social providers](https://clerk.com/docs/chrome-extension/guides/configure/auth-strategies/social-connections/overview.md) such as Google, Apple, Facebook, and many more (`User.externalAccounts`).

Finally, a `User` object holds profile data like the user's name, profile picture, and a set of [metadata](https://clerk.com/docs/guides/users/extending.md?sdk=chrome-extension) that can be used internally to store arbitrary information. The metadata are split into `publicMetadata` and `privateMetadata`. Both types are set from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }} via [`updateUserMetadata()`](https://clerk.com/docs/reference/backend/user/update-user-metadata.md?sdk=chrome-extension), but public metadata can also be accessed from the [Frontend API](https://clerk.com/docs/reference/frontend-api){{ target: '_blank' }}.

**For AI agents:** To seed or verify user data while building with this object, use the CLI instead of the Dashboard's Users page: run `npx clerk@latest users create --email <email> --password <password> --yes` (the password is required while password authentication is enabled, the default) and `npx clerk@latest users list --query <term>`, or fetch a user's full backend record with `npx clerk@latest api users/<user_id>`. Install [Clerk's skills](https://clerk.com/docs/guides/ai/skills.md?sdk=chrome-extension) with `npx skills add clerk/skills` for correct CLI and SDK usage.

## Example

The following example demonstrates how to use the [useUser()](https://clerk.com/docs/chrome-extension/reference/hooks/use-user.md) hook to access the [User](https://clerk.com/docs/chrome-extension/reference/objects/user.md) object, which contains the current user's data such as their ID.

filename: src/routes/page.tsx
```tsx
import { useUser } from '@clerk/chrome-extension'

export default function Example() {
  const { isSignedIn, user, isLoaded } = useUser()

  // Handle loading state
  if (!isLoaded) return <div>Loading...</div>

  // Protect the page from unauthenticated users
  if (!isSignedIn) return <div>Sign in to view this page</div>

  return <div>Hello {user.id}!</div>
}
```

## Properties

| Property                                                           | Type                                                                                                                                           | Description                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="backupcodeenabled"></a> `backupCodeEnabled`                 | `boolean`                                                                                                                                      | Indicates whether the user has enabled backup codes.                                                                                                                                                                                                                                                                                                                                            |
| <a id="createdat"></a> `createdAt`                                 | `null | Date`                                                                                                                       | The date and time when the user was created.                                                                                                                                                                                                                                                                                                                                                    |
| <a id="createorganizationenabled"></a> `createOrganizationEnabled` | `boolean`                                                                                                                                      | Indicates whether the user can create organizations.                                                                                                                                                                                                                                                                                                                                            |
| <a id="createorganizationslimit"></a> `createOrganizationsLimit`   | `null | number`                                                                                                                     | The maximum number of organizations the user can create.                                                                                                                                                                                                                                                                                                                                        |
| <a id="deleteselfenabled"></a> `deleteSelfEnabled`                 | `boolean`                                                                                                                                      | Indicates whether the user can delete their own account.                                                                                                                                                                                                                                                                                                                                        |
| <a id="emailaddresses"></a> `emailAddresses`                       | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/email-address.md">EmailAddressResource</a>[]</code>                     | An array of all the `EmailAddress` objects associated with the user. Includes the primary.                                                                                                                                                                                                                                                                                                      |
| <a id="enterpriseaccounts"></a> `enterpriseAccounts`               | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/enterprise-account.md">EnterpriseAccountResource</a>[]</code>           | An array of all the `EnterpriseAccount` objects associated with the user via enterprise SSO.                                                                                                                                                                                                                                                                                                    |
| <a id="externalaccounts"></a> `externalAccounts`                   | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/external-account.md">ExternalAccountResource</a>[]</code>               | An array of all the `ExternalAccount` objects associated with the user via OAuth.                                                                                                                                                                                                                                                                                                               |
| <a id="externalid"></a> `externalId`                               | `null | string`                                                                                                                     | The user's ID as used in your external systems. Must be unique across your instance.                                                                                                                                                                                                                                                                                                            |
| <a id="firstname"></a> `firstName`                                 | `null | string`                                                                                                                     | The user's first name.                                                                                                                                                                                                                                                                                                                                                                          |
| <a id="fullname"></a> `fullName`                                   | `null | string`                                                                                                                     | The user's full name.                                                                                                                                                                                                                                                                                                                                                                           |
| <a id="hasimage"></a> `hasImage`                                   | `boolean`                                                                                                                                      | Indicates whether the user has uploaded an image or one was copied from OAuth. Returns `false` if Clerk is displaying an avatar for the user.                                                                                                                                                                                                                                                   |
| <a id="id"></a> `id`                                               | `string`                                                                                                                                       | The unique identifier of the user.                                                                                                                                                                                                                                                                                                                                                              |
| <a id="imageurl"></a> `imageUrl`                                   | `string`                                                                                                                                       | Holds the default avatar or user's uploaded profile image. Compatible with Clerk's [Image Optimization](https://clerk.com/docs/guides/development/image-optimization.md?sdk=chrome-extension).                                                                                                                                                                                                  |
| <a id="lastname"></a> `lastName`                                   | `null | string`                                                                                                                     | The user's last name.                                                                                                                                                                                                                                                                                                                                                                           |
| <a id="lastsigninat"></a> `lastSignInAt`                           | `null | Date`                                                                                                                       | The date and time when the user last signed in.                                                                                                                                                                                                                                                                                                                                                 |
| <a id="legalacceptedat"></a> `legalAcceptedAt`                     | `null | Date`                                                                                                                       | The date and time when the user accepted the legal compliance documents. `null` if [**Require express consent to legal documents**](https://clerk.com/docs/guides/secure/legal-compliance.md?sdk=chrome-extension) is not enabled.                                                                                                                                                              |
| <a id="organizationmemberships"></a> `organizationMemberships`     | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/organization-membership.md">OrganizationMembershipResource</a>[]</code> | An array of all the `OrganizationMembership` objects associated with the user.                                                                                                                                                                                                                                                                                                                  |
| <a id="passkeys"></a> `passkeys`                                   | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/passkey-resource.md">PasskeyResource</a>[]</code>                       | An array of all the `Passkey` objects associated with the user.                                                                                                                                                                                                                                                                                                                                 |
| <a id="passwordenabled"></a> `passwordEnabled`                     | `boolean`                                                                                                                                      | Indicates whether the user has a password on their account.                                                                                                                                                                                                                                                                                                                                     |
| <a id="phonenumbers"></a> `phoneNumbers`                           | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/phone-number.md">PhoneNumberResource</a>[]</code>                       | An array of all the `PhoneNumber` objects associated with the user. Includes the primary.                                                                                                                                                                                                                                                                                                       |
| <a id="primaryemailaddress"></a> `primaryEmailAddress`             | <code>null | <a href="https://clerk.com/docs/chrome-extension/reference/types/email-address.md">EmailAddressResource</a></code>                | The user's primary email address.                                                                                                                                                                                                                                                                                                                                                               |
| <a id="primaryemailaddressid"></a> `primaryEmailAddressId`         | `null | string`                                                                                                                     | The ID of the user's primary email address.                                                                                                                                                                                                                                                                                                                                                     |
| <a id="primaryphonenumber"></a> `primaryPhoneNumber`               | <code>null | <a href="https://clerk.com/docs/chrome-extension/reference/types/phone-number.md">PhoneNumberResource</a></code>                  | The user's primary phone number.                                                                                                                                                                                                                                                                                                                                                                |
| <a id="primaryphonenumberid"></a> `primaryPhoneNumberId`           | `null | string`                                                                                                                     | The ID of the user's primary phone number.                                                                                                                                                                                                                                                                                                                                                      |
| <a id="primaryweb3wallet"></a> `primaryWeb3Wallet`                 | <code>null | <a href="https://clerk.com/docs/chrome-extension/reference/types/web3-wallet.md">Web3WalletResource</a></code>                    | The user's primary Web3 wallet.                                                                                                                                                                                                                                                                                                                                                                 |
| <a id="primaryweb3walletid"></a> `primaryWeb3WalletId`             | `null | string`                                                                                                                     | The ID of the user's primary Web3 wallet.                                                                                                                                                                                                                                                                                                                                                       |
| <a id="publicmetadata"></a> `publicMetadata`                       | [UserPublicMetadata](https://clerk.com/docs/chrome-extension/reference/types/metadata.md#user-public-metadata)                                 | Metadata that can be read from the Frontend API and Backend API and can be set only from the Backend API.                                                                                                                                                                                                                                                                                       |
| <a id="totpenabled"></a> `totpEnabled`                             | `boolean`                                                                                                                                      | Indicates whether the user has enabled TOTP.                                                                                                                                                                                                                                                                                                                                                    |
| <a id="twofactorenabled"></a> `twoFactorEnabled`                   | `boolean`                                                                                                                                      | Indicates whether the user has enabled two-factor authentication.                                                                                                                                                                                                                                                                                                                               |
| <a id="unsafemetadata"></a> `unsafeMetadata`                       | [UserUnsafeMetadata](https://clerk.com/docs/chrome-extension/reference/types/metadata.md#user-unsafe-metadata)                                 | Metadata that can be read and set from the Frontend API. It's considered unsafe because it can be modified from the frontend. There is also an `unsafeMetadata` attribute in the [SignUp](https://clerk.com/docs/chrome-extension/reference/objects/sign-up-future.md) object. The value of that field will be automatically copied to the user's unsafe metadata once the sign-up is complete. |
| <a id="updatedat"></a> `updatedAt`                                 | `null | Date`                                                                                                                       | The date and time when the user was last updated.                                                                                                                                                                                                                                                                                                                                               |
| <a id="username"></a> `username`                                   | `null | string`                                                                                                                     | The user's username.                                                                                                                                                                                                                                                                                                                                                                            |
| <a id="web3wallets"></a> `web3Wallets`                             | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/web3-wallet.md">Web3WalletResource</a>[]</code>                         | An array of all the `Web3Wallet` objects associated with the user. Includes the primary.                                                                                                                                                                                                                                                                                                        |

## Methods

### `createBackupCode()`

Generates a fresh new set of backup codes for the user. Every time the method is called, it will replace the previously generated backup codes.

Returns a [BackupCodeResource](https://clerk.com/docs/chrome-extension/reference/types/backup-code-resource.md) object.

```typescript
function createBackupCode(): Promise<BackupCodeResource>
```

### `createEmailAddress()`

Adds an email address for the user. A new [EmailAddress](https://clerk.com/docs/chrome-extension/reference/types/email-address.md) will be created and associated with the user.

> [**Email** must be enabled](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=chrome-extension#email) in your app's settings in the Clerk Dashboard.

```typescript
function createEmailAddress(params: CreateEmailAddressParams): Promise<EmailAddressResource>
```

#### `CreateEmailAddressParams`

| Property                   | Type     | Description                           |
| -------------------------- | -------- | ------------------------------------- |
| <a id="email"></a> `email` | `string` | The email address to add to the user. |

### `createExternalAccount()`

Adds an external account for the user. A new [ExternalAccount](https://clerk.com/docs/chrome-extension/reference/types/external-account.md) will be created and associated with the user. This method is useful if you want to allow an already signed-in user to connect their account with an external provider, such as Facebook, GitHub, etc., so that they can sign in with that provider in the future.

> The social provider that you want to connect to [must be enabled](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=chrome-extension#sso-connections) in your app's settings in the Clerk Dashboard.

```typescript
function createExternalAccount(params: CreateExternalAccountParams): Promise<ExternalAccountResource>
```

#### `CreateExternalAccountParams`

| Property                                                      | Type                                                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="additionalscopes"></a> `additionalScopes?`             | `OAuthScope[]`                                                                       | Additional scopes for your user to be prompted to approve.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <a id="enterpriseconnectionid"></a> `enterpriseConnectionId?` | `string`                                                                                        | The ID of the enterprise connection to connect to the user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| <a id="oidcloginhint"></a> `oidcLoginHint?`                   | `string`                                                                                        | The value to pass to the [OIDC `login_hint` parameter](https://openid.net/specs/openid-connect-core-1_0.html#:~:text=login_hint,in%20(if%20necessary).) in the generated OAuth redirect URL.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| <a id="oidcprompt"></a> `oidcPrompt?`                         | `string`                                                                                        | The value to pass to the [OIDC `prompt` parameter](https://openid.net/specs/openid-connect-core-1_0.html#:~:text=prompt,reauthentication%20and%20consent.) in the generated OAuth redirect URL.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| <a id="redirecturl"></a> `redirectUrl?`                       | `string`                                                                                        | The full URL or path that the OAuth provider should redirect to, on successful authorization on their part. Typically, this will be a simple `/sso-callback` route that calls [Clerk.handleRedirectCallback](https://clerk.com/docs/chrome-extension/reference/objects/clerk.md#handle-redirect-callback) or mounts the [<AuthenticateWithRedirectCallback />](https://clerk.com/docs/chrome-extension/reference/components/control/authenticate-with-redirect-callback.md) component. See the [custom flow](https://clerk.com/docs/guides/development/custom-flows/authentication/oauth-connections.md?sdk=chrome-extension) for implementation details. |
| <a id="strategy"></a> `strategy?`                             | [OAuthStrategy](https://clerk.com/docs/chrome-extension/reference/types/sso.md#o-auth-strategy) | The strategy corresponding to the OAuth provider. For example: `'oauth_google'`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### `createPasskey()`

Creates a passkey for the signed-in user. For an example, see the [custom flow guide](https://clerk.com/docs/guides/development/custom-flows/authentication/passkeys.md?sdk=chrome-extension#create-user-passkeys).

Returns a [PasskeyResource](https://clerk.com/docs/chrome-extension/reference/types/passkey-resource.md) object.

> When creating a passkey for a user in a multi-domain Clerk app, `createPasskey()` must be called from the primary domain.

```typescript
function createPasskey(): Promise<PasskeyResource>
```

### `createPhoneNumber()`

Adds a phone number for the user. A new [PhoneNumber](https://clerk.com/docs/chrome-extension/reference/types/phone-number.md) will be created and associated with the user.

> [**Phone** must be enabled](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=chrome-extension#phone) in your app's settings in the Clerk Dashboard.

```typescript
function createPhoneNumber(params: CreatePhoneNumberParams): Promise<PhoneNumberResource>
```

#### `CreatePhoneNumberParams`

| Property                               | Type     | Description                          |
| -------------------------------------- | -------- | ------------------------------------ |
| <a id="phonenumber"></a> `phoneNumber` | `string` | The phone number to add to the user. |

### `createTOTP()`

Generates a TOTP secret for a user that can be used to register the application on the user's authenticator app of choice. If this method is called again (while still unverified), it replaces the previously generated secret.

Returns a [TOTPResource](https://clerk.com/docs/chrome-extension/reference/types/totp-resource.md) object.

> The **Authenticator application** multi-factor strategy must be enabled in your app's settings in the Clerk Dashboard. See the [Multi-factor authentication](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=chrome-extension#multi-factor-authentication) section to learn more.

```typescript
function createTOTP(): Promise<TOTPResource>
```

### `createWeb3Wallet()`

Adds a Web3 wallet for the user. A new [Web3WalletResource](https://clerk.com/docs/chrome-extension/reference/types/web3-wallet.md) will be created and associated with the user.

```typescript
function createWeb3Wallet(params: CreateWeb3WalletParams): Promise<Web3WalletResource>
```

#### `CreateWeb3WalletParams`

| Property                             | Type     | Description                                                                                                                                |
| ------------------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| <a id="web3wallet"></a> `web3Wallet` | `string` | The Web3 wallet address, made up of either 0x + 40 hexadecimal characters or a `base58` encoded `ed25519` public key (for Solana wallets). |

### `delete()`

Deletes the current user.

```typescript
function delete(): Promise<void>
```

### `disableTOTP()`

Disables TOTP by deleting the user's TOTP secret.

Returns a [DeletedObjectResource](https://clerk.com/docs/chrome-extension/reference/types/deleted-object-resource.md) object.

> The **Authenticator application** multi-factor strategy must be enabled in your app's settings in the Clerk Dashboard. See the [Multi-factor authentication](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=chrome-extension#multi-factor-authentication) section to learn more.

```typescript
function disableTOTP(): Promise<DeletedObjectResource>
```

### `getOrganizationCreationDefaults()`

Gets organization creation defaults for the current user.

Returns a [OrganizationCreationDefaultsResource](https://clerk.com/docs/chrome-extension/reference/types/organization-creation-defaults.md) object.

```typescript
function getOrganizationCreationDefaults(): Promise<OrganizationCreationDefaultsResource>
```

### `getOrganizationInvitations()`

Gets a list of Organization invitations for the user.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/chrome-extension/reference/types/clerk-paginated-response.md) of [UserOrganizationInvitation](https://clerk.com/docs/chrome-extension/reference/types/user-organization-invitation.md) objects.

```typescript
function getOrganizationInvitations(params?: GetUserOrganizationInvitationsParams): Promise<ClerkPaginatedResponse<UserOrganizationInvitationResource>>
```

#### `GetUserOrganizationInvitationsParams`

| Property                                | Type                                                        | Description                                                                                                                                                         |
| --------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number`                                                    | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number`                                                    | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |
| `status?`                               | `"pending" | "accepted" | "revoked" | "expired"` | The status an invitation can have.                                                                                                                                  |

### `getOrganizationMemberships()`

Gets a list of Organization memberships for the user. Returns a [ClerkPaginatedResponse](https://clerk.com/docs/chrome-extension/reference/types/clerk-paginated-response.md) of [OrganizationMembershipResource](https://clerk.com/docs/chrome-extension/reference/types/organization-membership.md) objects.

```ts
function getOrganizationMemberships(
  params?: GetUserOrganizationMembershipParams,
): Promise<ClerkPaginatedResponse<OrganizationMembershipResource>>
```

#### `GetUserOrganizationMembershipParams`

| Name         | Type   | Description                                                                                                                                                      |
| ------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| initialPage? | number | A number that can be used to skip the first n-1 pages. For example, if initialPage is set to 10, it is will skip the first 9 pages and will fetch the 10th page. |
| pageSize?    | number | A number that indicates the maximum number of results that should be returned for a specific page.                                                               |

### `getOrganizationSuggestions()`

Gets a list of Organization suggestions for the user.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/chrome-extension/reference/types/clerk-paginated-response.md) of [OrganizationSuggestionResource](https://clerk.com/docs/chrome-extension/reference/types/organization-suggestion.md) objects.

```typescript
function getOrganizationSuggestions(params?: GetUserOrganizationSuggestionsParams): Promise<ClerkPaginatedResponse<OrganizationSuggestionResource>>
```

#### `GetUserOrganizationSuggestionsParams`

| Property                                | Type                                                             | Description                                                                                                                                                         |
| --------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number`                                                         | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number`                                                         | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |
| `status?`                               | `"pending" | "accepted" | ("pending" | "accepted")[]` | The status a suggestion can have.                                                                                                                                   |

### `getPaymentMethods()`

Gets a list of payment methods that have been stored.

Returns a [ClerkPaginatedResponse](https://clerk.com/docs/chrome-extension/reference/types/clerk-paginated-response.md) of [BillingPaymentMethodResource](https://clerk.com/docs/chrome-extension/reference/types/billing-payment-method-resource.md) objects.

```typescript
function getPaymentMethods(params?: GetPaymentMethodsParams): Promise<ClerkPaginatedResponse<BillingPaymentMethodResource>>
```

#### `GetPaymentMethodsParams`

| Property                                | Type     | Description                                                                                                                                                         |
| --------------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="initialpage"></a> `initialPage?` | `number` | A number that specifies which page to fetch. For example, if `initialPage` is set to `10`, it will skip the first 9 pages and fetch the 10th page. Defaults to `1`. |
| <a id="pagesize"></a> `pageSize?`       | `number` | A number that specifies the maximum number of results to return per page. Defaults to `10`.                                                                         |

### `getSessions()`

Gets all **active** sessions for this user. This method uses a cache so a network request will only be triggered only once.

Returns an array of [SessionWithActivities](https://clerk.com/docs/chrome-extension/reference/types/session-with-activities.md) objects.

```typescript
function getSessions(): Promise<SessionWithActivitiesResource[]>
```

### `initializePaymentMethod()`

Initializes a payment method.

Returns a [BillingInitializedPaymentMethodResource](https://clerk.com/docs/chrome-extension/reference/types/billing-initialized-payment-method-resource.md) object.

```typescript
function initializePaymentMethod(params: InitializePaymentMethodParams): Promise<BillingInitializedPaymentMethodResource>
```

#### `InitializePaymentMethodParams`

| Property                       | Type       | Description                 |
| ------------------------------ | ---------- | --------------------------- |
| <a id="gateway"></a> `gateway` | `"stripe"` | The payment gateway to use. |

### `isPrimaryIdentification()`

A check whether or not the given resource is the primary identifier for the user.

```typescript
function isPrimaryIdentification(ident: Web3WalletResource | EmailAddressResource | PhoneNumberResource): boolean
```

#### Parameters

| Parameter | Type                                                                                                                                                                                                                                                                                                                                           | Description                                                                   |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| `ident`   | <code><a href="https://clerk.com/docs/chrome-extension/reference/types/web3-wallet.md">Web3WalletResource</a> | <a href="https://clerk.com/docs/chrome-extension/reference/types/email-address.md">EmailAddressResource</a> | <a href="https://clerk.com/docs/chrome-extension/reference/types/phone-number.md">PhoneNumberResource</a></code> | The resource checked against the user to see if it is the primary identifier. |

### `leaveOrganization()`

Leaves an organization that the user is a member of.

Returns a [DeletedObjectResource](https://clerk.com/docs/chrome-extension/reference/types/deleted-object-resource.md) object.

```typescript
function leaveOrganization(organizationId: string): Promise<DeletedObjectResource>
```

#### Parameters

| Parameter        | Type     | Description                          |
| ---------------- | -------- | ------------------------------------ |
| `organizationId` | `string` | The ID of the organization to leave. |

### `reload()`

Reloads the resource, which is useful when you want to access the latest user data after performing a mutation. To make the updated data immediately available, this method forces a session token refresh instead of waiting for the automatic refresh cycle that could temporarily retain stale information. Learn more about [forcing a token refresh](https://clerk.com/docs/guides/sessions/force-token-refresh.md?sdk=chrome-extension).

```typescript
function reload(p?: ClerkResourceReloadParams): Promise<UserResource>
```

#### `ClerkResourceReloadParams`

| Property                                              | Type     | Description                                                                                                                                                                   |
| ----------------------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="rotatingtokennonce"></a> `rotatingTokenNonce?` | `string` | A nonce to use for rotating the user's token. Used in native application OAuth flows to allow the native client to update its JWT once despite changes in its rotating token. |

You only need to call `user.reload()` if you've updated the `User` object outside of the `user.update()` method or Clerk hooks; for example, if you made changes through an API endpoint.

### `removePassword()`

Removes the user's password.

```typescript
function removePassword(params: RemoveUserPasswordParams): Promise<UserResource>
```

#### `RemoveUserPasswordParams`

| Property                                        | Type     | Description                  |
| ----------------------------------------------- | -------- | ---------------------------- |
| <a id="currentpassword"></a> `currentPassword?` | `string` | The user's current password. |

### `setProfileImage()`

Adds the user's profile image or replaces it if one already exists. This method will upload an image and associate it with the user.

```typescript
function setProfileImage(params: SetProfileImageParams): Promise<ImageResource>
```

#### `SetProfileImageParams`

| Property                 | Type                                     | Description                                                                         |
| ------------------------ | ---------------------------------------- | ----------------------------------------------------------------------------------- |
| <a id="file"></a> `file` | `Blob | File | string | null` | The file to set as the user's profile image, or `null` to remove the current image. |

### `update()`

Updates the user's attributes. Use this method to save information you collected about the user.

The appropriate settings must be enabled in the Clerk Dashboard for the user to be able to update their attributes. For example, if you want to use the `update({ firstName })` method, you must enable the **First and last name** setting. It can be found on the [**User & authentication**](https://dashboard.clerk.com/~/user-authentication/user-and-authentication?user_auth_tab=user-profile) page in the Clerk Dashboard.

```typescript
function update(params: UpdateUserParams): Promise<UserResource>
```

#### `UpdateUserParams`

| Name                         | Type               | Description                                                                                                                                                       |
| ---------------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| firstName?                   | string             | The user's first name.                                                                                                                                            |
| lastName?                    | string             | The user's last name.                                                                                                                                             |
| primaryEmailAddressId?       | string             | The ID for the EmailAddress that the user has set as primary.                                                                                                     |
| primaryPhoneNumberId?        | string             | The ID for the PhoneNumber that the user has set as primary.                                                                                                      |
| primaryWeb3WalletId?         | string             | The ID for the Web3Wallet that the user signed up with.                                                                                                           |
| unsafeMetadata? (deprecated) | UserUnsafeMetadata | Deprecated. Use updateMetadata() instead. Deep-merges with the existing value rather than replacing it. This parameter will be removed in a future major version. |
| username?                    | string             | The user's username. Only supported if username is enabled in the instance settings.                                                                              |

### `updateMetadata()`

Updates the user's `unsafeMetadata` using deep-merge semantics. Unlike [update()](https://clerk.com/docs/chrome-extension/reference/objects/user.md#update), which fully replaces `unsafeMetadata`, this method merges the provided value with the existing `unsafeMetadata`. Top-level and nested keys are merged, and any key set to `null` is removed. Only `unsafeMetadata` is writable from the frontend; `publicMetadata` and `privateMetadata` can only be set from the [Backend API](https://clerk.com/docs/reference/backend-api){{ target: '_blank' }}.

```typescript
function updateMetadata(params: UpdateUserMetadataParams): Promise<UserResource>
```

#### `UpdateUserMetadataParams`

| Property                                     | Type                                                                                                           | Description                                                                                                                        |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| <a id="unsafemetadata"></a> `unsafeMetadata` | [UserUnsafeMetadata](https://clerk.com/docs/chrome-extension/reference/types/metadata.md#user-unsafe-metadata) | The metadata to deep-merge with the user's existing `unsafeMetadata`. Keys at any nesting level whose value is `null` are removed. |

### `updatePassword()`

Updates the user's password.

```typescript
function updatePassword(params: UpdateUserPasswordParams): Promise<UserResource>
```

#### `UpdateUserPasswordParams`

| Property                                                      | Type      | Description                                                                                 |
| ------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------- |
| <a id="currentpassword"></a> `currentPassword?`               | `string`  | The user's current password.                                                                |
| <a id="newpassword"></a> `newPassword`                        | `string`  | The user's new password.                                                                    |
| <a id="signoutofothersessions"></a> `signOutOfOtherSessions?` | `boolean` | Whether to sign out the user from all their active sessions once their password is updated. |

### `verifyTOTP()`

Verifies a TOTP secret after a user has created it. The user must provide a code from their authenticator app that has been generated using the previously created secret. This way, correct set up and ownership of the authenticator app can be validated.

Returns a [TOTPResource](https://clerk.com/docs/chrome-extension/reference/types/totp-resource.md) object.

> The **Authenticator application** multi-factor strategy must be enabled in your app's settings in the Clerk Dashboard. See the [Multi-factor authentication](https://clerk.com/docs/guides/configure/auth-strategies/sign-up-sign-in-options.md?sdk=chrome-extension#multi-factor-authentication) section to learn more.

```typescript
function verifyTOTP(params: VerifyTOTPParams): Promise<TOTPResource>
```

#### `VerifyTOTPParams`

| Property                 | Type     | Description         |
| ------------------------ | -------- | ------------------- |
| <a id="code"></a> `code` | `string` | The code to verify. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
