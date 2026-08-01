# update()

Updates a domain for the instance. Both primary and satellite domains can be updated. If you choose to use Clerk via proxy, use this endpoint to specify the `proxy_url`. Whenever you decide you'd rather switch to DNS setup for Clerk, simply set `proxy_url` to `null` for the domain.

When you update a production instance's primary domain name, you have to make sure that you've completed all the necessary setup steps for DNS and emails to work. Expect downtime otherwise. Updating a primary domain's name will also update the instance's home origin, affecting the default application paths.

Returns the updated [`Domain`](https://clerk.com/docs/reference/backend/types/domain.md) object.

```typescript
function update(params: UpdateDomainParams): Promise<Domain>
```

## `UpdateDomainParams`

| Property        | Type                        | Description                                                                                                                                                                                                                                                     |
| --------------- | --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `domainId`      | `string`                    | The ID of the domain that will be updated.                                                                                                                                                                                                                      |
| `is_secondary?` | `boolean | null` | Whether this is a domain for a secondary app, meaning that any subdomain provided is significant and will be stored as part of the domain. This is useful for supporting multiple apps (one primary and multiple secondaries) on the same root domain (eTLD+1). |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.domains.update({
  domainId: 'domain_123',
  is_secondary: true,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `PATCH/domains/{domain_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/domains/PATCH/domains/%7Bdomain_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
