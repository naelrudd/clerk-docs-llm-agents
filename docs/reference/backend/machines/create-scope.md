# createScope()

Creates a new machine scope, allowing the specified machine to access another machine. Maximum of 150 scopes per machine.

Returns the created [`MachineScope`](https://clerk.com/docs/reference/backend/types/backend-machine-scope.md) object.

```typescript
function createScope(machineId: string, toMachineId: string): Promise<MachineScope>
```

## Parameters

| Parameter     | Type     | Description                                                          |
| ------------- | -------- | -------------------------------------------------------------------- |
| `machineId`   | `string` | The ID of the machine that will have access to the target machine.   |
| `toMachineId` | `string` | The ID of the machine that will be accessible by the source machine. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const machineId = 'mch_123'
const toMachineId = 'mch_456'

const response = await clerkClient.machines.createScope(machineId, toMachineId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/machines/{machine_id}/scopes`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/machines/POST/machines/%7Bmachine_id%7D/scopes){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
