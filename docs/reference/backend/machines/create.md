# create()

Creates a new machine.

Returns the created [`Machine`](https://clerk.com/docs/reference/backend/types/backend-machine.md) object.

```typescript
function create(bodyParams: CreateMachineParams): Promise<Machine>
```

## `CreateMachineParams`

| Property                                        | Type                  | Description                                                                                              |
| ----------------------------------------------- | --------------------- | -------------------------------------------------------------------------------------------------------- |
| <a id="defaulttokenttl"></a> `defaultTokenTtl?` | `number`              | The default time-to-live (TTL) in seconds for tokens created by this machine. Must be at least 1 second. |
| <a id="name"></a> `name`                        | `string`              | The name of the machine.                                                                                 |
| <a id="scopedmachines"></a> `scopedMachines?`   | `string[]` | An array of machine IDs that the new machine will have access to. Maximum of 150 scopes per machine.     |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

### Basic machine creation

```ts
const response = await clerkClient.machines.create({
  name: 'Email Server',
})
```

### Machine with scoped access

```ts
const response = await clerkClient.machines.create({
  name: 'API Gateway',
  scopedMachines: ['mch_123', 'mch_456'],
  defaultTokenTtl: 3600,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/machines`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/machines/POST/machines){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
