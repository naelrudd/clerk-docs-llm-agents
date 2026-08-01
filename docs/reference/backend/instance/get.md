# get()

Gets the current [`Instance`](https://clerk.com/docs/reference/backend/types/backend-instance.md).

```typescript
function get(): Promise<Instance>
```

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```ts
const response = await clerkClient.instances.get()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/instance`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/instance-settings/GET/instance){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
