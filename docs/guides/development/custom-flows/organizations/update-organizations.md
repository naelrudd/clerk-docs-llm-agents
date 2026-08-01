# Build a custom flow for updating an Organization

> This guide is for users who want to build a custom flow. To use a _prebuilt_ UI, use the [Account Portal pages](https://clerk.com/docs/guides/account-portal/overview.md) or [prebuilt components](https://clerk.com/docs/reference/components/overview.md).

Organization members with appropriate [Permissions](https://clerk.com/docs/guides/organizations/control-access/roles-and-permissions.md) can update an Organization.

This guide will demonstrate how to use Clerk's API to build a custom flow for updating an Organization.

The following example:

1. Uses the [useOrganization()](https://clerk.com/docs/reference/hooks/use-organization.md) hook to fetch the active `organization`.
2. Uses `organization` to call the `update()` method with the desired name to update the Organization. To see what other attributes can be updated, see the [update() reference doc](https://clerk.com/docs/reference/objects/organization.md#update).

filename: app/components/UpdateOrganization.tsx
```tsx
'use client'

import { useState, useEffect } from 'react'
import { useRouter } from 'next/navigation'
import { useOrganization } from '@clerk/nextjs'

export default function UpdateOrganization() {
  const [name, setName] = useState('')
  const router = useRouter()
  const { organization } = useOrganization()

  useEffect(() => {
    if (!organization) {
      return
    }
    setName(organization.name)
  }, [organization])

  if (!organization) {
    return null
  }

  async function submit(e: React.FormEvent<HTMLFormElement>) {
    e.preventDefault()
    try {
      await organization?.update({ name })
      router.push(`/organizations/${organization?.id}`)
    } catch (err) {
      console.error(err)
    }
  }

  return (
    <div>
      <h1>Update the current organization</h1>
      <form onSubmit={submit}>
        <div>
          <label htmlFor="name">Name</label>
          <input id="name" name="name" value={name} onChange={(e) => setName(e.target.value)} />
        </div>
        <button>Update</button>
      </form>
    </div>
  )
}
```

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
