# rotateSecretKey()

Rotates the secret key for the given machine.

Returns the new secret key.

```typescript
function rotateSecretKey(params: RotateMachineSecretKeyParams): Promise<MachineSecretKey>
```

## `RotateMachineSecretKeyParams`

| Property                                         | Type     | Description                                                                                                                                                                                                                                                                    |
| ------------------------------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <a id="machineid"></a> `machineId`               | `string` | The ID of the machine to rotate the secret key for.                                                                                                                                                                                                                            |
| <a id="previoustokenttl"></a> `previousTokenTtl` | `number` | The time in seconds that the previous secret key will remain valid after rotation. This ensures a graceful transition period for updating applications with the new secret key. Set to `0` to immediately expire the previous key. Maximum value is `28800` seconds (8 hours). |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const machineId = 'mch_123'

const response = await clerkClient.machines.rotateSecretKey({
  machineId,
  previousTokenTtl: 3600,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/machines/{machine_id}/secret_key/rotate`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/machines/POST/machines/%7Bmachine_id%7D/secret_key/rotate){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
