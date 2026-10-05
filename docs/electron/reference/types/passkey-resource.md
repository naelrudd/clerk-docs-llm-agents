# PasskeyResource

An interface that describes a passkey associated with a user response.

## Properties

| Name         | Type                 | Description                                 |
| ------------ | -------------------- | ------------------------------------------- |
| createdAt    | Date                 | The date when the passkey was created.      |
| id           | string               | The unique identifier of the passkey.       |
| lastUsedAt   | Date | null         | The date when the passkey was last used.    |
| name         | string               | The passkey's name.                         |
| updatedAt    | Date                 | The date when the passkey was last updated. |
| verification | VerificationResource | The verification details for the passkey.   |

## Methods

### `update()`

Updates the name of the associated passkey for the signed-in user.

```ts
function update(params: { name: string }): Promise<PasskeyResource>
```

For an example of how to use these methods, see the [Passkeys custom flows documentation](https://clerk.com/docs/guides/development/custom-flows/authentication/passkeys.md?sdk=electron#rename-user-passkeys).

### `delete()`

Deletes the associated passkey for the signed-in user.

```ts
function delete(): Promise<DeletedObjectResource>
```

Learn more:

- [DeletedObjectResource](https://clerk.com/docs/electron/reference/types/deleted-object-resource.md)

For an example of how to use these methods, see the [Passkeys custom flows documentation](https://clerk.com/docs/guides/development/custom-flows/authentication/passkeys.md?sdk=electron#delete-user-passkeys).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
