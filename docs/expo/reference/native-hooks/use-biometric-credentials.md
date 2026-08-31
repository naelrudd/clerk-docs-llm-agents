# useBiometricCredentials()

> This hook requires a [development build](https://docs.expo.dev/develop/development-builds/introduction/) that includes a compatible version of `@clerk/expo` and doesn't work in Expo Go.

The `useBiometricCredentials()` hook provides methods to check biometric credential availability, enroll the current app installation, list and revoke credentials, and sign in returning users.

## Returns

The `useBiometricCredentials()` hook returns the following methods:

- [getAvailability()](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#get-availability)
- [list()](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#list)
- [enroll()](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#enroll)
- [revoke()](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#revoke)
- [signIn()](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#sign-in)

### `getAvailability()`

Checks whether a biometric credential and private key are available locally for sign-in. Pass an `id` or `identifierHint` to check a specific credential. The function signature is:

```ts
function getAvailability(
  params?: GetBiometricCredentialAvailabilityParams,
): Promise<BiometricCredentialAvailability>
```

#### Parameters

`getAvailability()` accepts the following parameters (`GetBiometricCredentialAvailabilityParams`):

| Name            | Type   | Description                                                                                             |
| --------------- | ------ | ------------------------------------------------------------------------------------------------------- |
| id?             | string | The ID of the biometric credential to check. When omitted, Clerk checks the available local credential. |
| identifierHint? | string | A local-only user identifier hint used to select a matching credential.                                 |

#### Returns

`getAvailability()` returns the following values:

| Name              | Type                                                                                                                                                                                                                                                                              | Description                                                                                |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| isAvailable       | boolean                                                                                                                                                                                                                                                                           | Whether a local credential and private key are available for biometric sign-in.            |
| unavailableReason | 'environment\_unavailable' | 'native\_api\_disabled' | 'feature\_disabled' | 'unsupported\_platform' | 'biometric\_authentication\_unavailable' | 'no\_local\_credential' | 'local\_key\_missing' | 'server\_credential\_missing' | 'server\_credential\_revoked' | null | The reason biometric sign-in is unavailable. This value is null when sign-in is available. |

### `list()`

Lists active biometric credentials for the signed-in user. Returns a `Promise` that resolves to an array of [BiometricCredential](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#biometric-credential) objects. The function signature is:

```ts
function list(): Promise<BiometricCredential[]>
```

### `enroll()`

Enrolls the current app installation as a biometric credential. Enrollment requires a Clerk session with a status of `active` or `pending`. Returns a `Promise` that resolves to the enrolled [BiometricCredential](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#biometric-credential) object. The function signature is:

```ts
function enroll(params?: EnrollBiometricCredentialParams): Promise<BiometricCredential>
```

#### Parameters

`enroll()` accepts the following parameters (`EnrollBiometricCredentialParams`):

| Name                                                                                                                                                 | Type                                                                                        | Description                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| name?                                                                                                                                                | string                                                                                      | A human-readable name stored with the biometric credential.                       |
| identifierHint?                                                                                                                                      | string                                                                                      | A local-only user identifier hint stored with the credential for later selection. |
| reason?                                                                                                                                              | string                                                                                      | The reason displayed in the system authentication prompt.                         |
| 'biometry\_current\_set': Requires a biometric from the currently enrolled set. Adding or removing biometric enrollment invalidates the private key. | 'biometry\_any': Requires biometric authentication and allows biometric enrollment changes. |                                                                                   |

### `revoke()`

Revokes a biometric credential. If the credential belongs to the current app installation, Clerk also deletes its local private key. Returns a `Promise` that resolves to the revoked [BiometricCredential](https://clerk.com/docs/expo/reference/native-hooks/use-biometric-credentials.md#biometric-credential) object. The function signature is:

```ts
function revoke(id: string): Promise<BiometricCredential>
```

#### Parameters

`revoke()` accepts the following parameter:

| Name | Type   | Description                                   |
| ---- | ------ | --------------------------------------------- |
| id   | string | The ID of the biometric credential to revoke. |

### `signIn()`

Signs in with a locally enrolled biometric credential. The function signature is:

```ts
function signIn(params?: SignInWithBiometricsParams): Promise<BiometricSignInResult>
```

#### Parameters

`signIn()` accepts the following parameters (`SignInWithBiometricsParams`):

| Name            | Type   | Description                                                                                         |
| --------------- | ------ | --------------------------------------------------------------------------------------------------- |
| id?             | string | The ID of the biometric credential to use. When omitted, Clerk uses the available local credential. |
| identifierHint? | string | A local-only user identifier hint used to select a matching credential.                             |
| reason?         | string | The reason displayed in the system authentication prompt.                                           |

#### Returns

`signIn()` returns the following values:

| Name             | Type           | Description                                                                                                   |
| ---------------- | -------------- | ------------------------------------------------------------------------------------------------------------- |
| status           | SignInStatus   | The status of the sign-in attempt.                                                                            |
| createdSessionId | string | null | The ID of the session created by a completed sign-in. Pass this value to setActive() to activate the session. |

## Types

### `BiometricCredential`

| Name          | Type                  | Description                                               |
| ------------- | --------------------- | --------------------------------------------------------- |
| id            | string                | The ID of the biometric credential.                       |
| object        | 'trusted\_device'     | The resource object name.                                 |
| platform      | 'ios' | 'android'    | The platform associated with the credential.              |
| appIdentifier | string                | The native app identifier associated with the credential. |
| name          | string | null        | The human-readable credential name.                       |
| algorithm     | 'ES256'               | The credential's signature algorithm.                     |
| status        | 'active' | 'revoked' | The credential's status.                                  |
| createdAt     | Date                  | The date when the credential was created.                 |
| updatedAt     | Date                  | The date when the credential was last updated.            |
| lastUsedAt    | Date | null          | The date when the credential was last used.               |
| revokedAt     | Date | null          | The date when the credential was revoked.                 |

## How to use the `useBiometricCredentials()` hook

To learn how to enroll a biometric credential, sign in a returning user, and revoke a credential, see the [biometric sign-in guide](https://clerk.com/docs/expo/guides/development/custom-flows/authentication/biometric-sign-in.md).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
