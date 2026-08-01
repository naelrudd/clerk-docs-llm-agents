# Build a custom flow for managing Organization Membership Requests

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md) or [prebuilt components](https://clerk.com/docs/reference/components/overview.md).

This guide will demonstrate how to use the Clerk API to build a custom flow for managing [Organization Membership Requests](https://clerk.com/docs/guides/organizations/add-members/verified-domains.md#membership-requests).

The following example:

1. Uses the [useOrganization()](https://clerk.com/docs/reference/hooks/use-organization.md) hook to get `membershipRequests`, which is a list of the Active Organization's Membership Requests.
   - `membershipRequests` is an object with `data` that contains an array of [OrganizationMembershipRequest](https://clerk.com/docs/reference/types/organization-membership-request.md) objects.
   - Each `OrganizationMembershipRequest` object has an [accept()](https://clerk.com/docs/reference/types/organization-membership-request.md#accept) and [reject()](https://clerk.com/docs/reference/types/organization-membership-request.md#reject) method to accept or reject the Membership Request, respectively.
2. Maps over the `data` array to display the Membership Requests in a table, providing an "Accept" and "Reject" button for each request that calls the `accept()` and `reject()` methods, respectively.

filename: app/components/MembershipRequests.tsx
```jsx
'use client'

import { useOrganization } from '@clerk/nextjs'

export const MembershipRequestsParams = {
  membershipRequests: {
    pageSize: 5,
    keepPreviousData: true,
  },
}

// List of organization membership requests.
export const MembershipRequests = () => {
  const { isLoaded, membershipRequests } = useOrganization(MembershipRequestsParams)

  if (!isLoaded) {
    return <>Loading</>
  }

  return (
    <>
      <h1>Membership requests</h1>
      <table>
        <thead>
          <tr>
            <th>User</th>
            <th>Date requested</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          {membershipRequests?.data?.map((mem) => (
            <tr key={mem.id}>
              <td>{mem.publicUserData.identifier}</td>
              <td>{mem.createdAt.toLocaleDateString()}</td>
              <td>
                <button
                  onClick={async () => {
                    await mem.accept()
                  }}
                >
                  Accept
                </button>
                <button
                  onClick={async () => {
                    await mem.reject()
                  }}
                >
                  Reject
                </button>
              </td>
            </tr>
          ))}
        </tbody>
      </table>

      <div>
        <button
          disabled={!membershipRequests?.hasPreviousPage || membershipRequests?.isFetching}
          onClick={() => membershipRequests?.fetchPrevious?.()}
        >
          Previous
        </button>

        <button
          disabled={!membershipRequests?.hasNextPage || membershipRequests?.isFetching}
          onClick={() => membershipRequests?.fetchNext?.()}
        >
          Next
        </button>
      </div>
    </>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
