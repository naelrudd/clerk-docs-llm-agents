# get()

Gets the given machine.

Returns the [`Machine`](https://clerk.com/docs/reference/backend/types/backend-machine.md) object.

```typescript
function get(machineId: string): Promise<Machine>
```

## Parameters

| Parameter   | Type     | Description                   |
| ----------- | -------- | ----------------------------- |
| `machineId` | `string` | The ID of the machine to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const machineId = 'mch_123'

const response = await clerkClient.machines.get(machineId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/machines/{machine_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/machines/GET/machines/%7Bmachine_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
