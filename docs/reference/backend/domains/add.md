# add()

Adds a new domain to the instance. Useful in the case of multi-domain instances, allows adding [satellite domains](https://clerk.com/docs/guides/dashboard/dns-domains/satellite-domains.md) to an instance.

Returns the created [`Domain`](https://clerk.com/docs/reference/backend/types/domain.md) object.

```typescript
function add(params: AddDomainParams): Promise<Domain>
```

## `AddDomainParams`

| Property                                 | Type                       | Description                                                                                                                                                                                        |
| ---------------------------------------- | -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <a id="is_satellite"></a> `is_satellite` | `boolean`                  | Whether the new domain is a satellite domain. Only `true` is accepted at the moment.                                                                                                               |
| <a id="name"></a> `name`                 | `string`                   | The new domain name. For development instances, can contain the port, e.g., `myhostname:3000`. For production instances, must be a valid FQDN, e.g., `mysite.com`. Cannot contain protocol scheme. |
| <a id="proxy_url"></a> `proxy_url?`      | `string | null` | The proxy URL for the domain. Applicable only to production instances.                                                                                                                             |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerkClient.domains.add({
  is_satellite: true,
  name: 'example.com',
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/domains`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/domains/POST/domains){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
