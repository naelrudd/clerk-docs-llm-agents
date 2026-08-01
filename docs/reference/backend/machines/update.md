# update()

Updates the given machine.

Returns the updated [`Machine`](https://clerk.com/docs/reference/backend/types/backend-machine.md) object.

```typescript
function update(params: UpdateMachineParams): Promise<Machine>
```

## `UpdateMachineParams`

| Property                                        | Type     | Description                                                                                              |
| ----------------------------------------------- | -------- | -------------------------------------------------------------------------------------------------------- |
| <a id="defaulttokenttl"></a> `defaultTokenTtl?` | `number` | The default time-to-live (TTL) in seconds for tokens created by this machine. Must be at least 1 second. |
| <a id="machineid"></a> `machineId`              | `string` | The ID of the machine to update.                                                                         |
| <a id="name"></a> `name?`                       | `string` | The name of the machine.                                                                                 |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const machineId = 'mch_123'

const response = await clerkClient.machines.update({
  machineId,
  name: 'New Machine Name',
  defaultTokenTtl: 3600,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/machines/{machine_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/machines/PATCH/machines/%7Bmachine_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
