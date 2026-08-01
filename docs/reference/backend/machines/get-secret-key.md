# getSecretKey()

Gets the secret key for the given machine.

Returns the machine's secret key.

```typescript
function getSecretKey(machineId: string): Promise<MachineSecretKey>
```

## Parameters

| Parameter   | Type     | Description                                      |
| ----------- | -------- | ------------------------------------------------ |
| `machineId` | `string` | The ID of the machine to get the secret key for. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const machineId = 'mch_123'

const response = await clerkClient.machines.getSecretKey(machineId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/machines/{machine_id}/secret_key`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/machines/GET/machines/%7Bmachine_id%7D/secret_key){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
