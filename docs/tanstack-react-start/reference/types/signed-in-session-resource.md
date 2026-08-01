# SignedInSessionResource

The `SignedInSessionResource` is a type that represents sessions for users who have completed the full sign-in flow. It's a union of [ActiveSessionResource](https://clerk.com/docs/tanstack-react-start/reference/types/signed-in-session-resource.md#active-session-resource) and [PendingSessionResource](https://clerk.com/docs/tanstack-react-start/reference/types/signed-in-session-resource.md#pending-session-resource).

```typescript
type SignedInSessionResource = ActiveSessionResource | PendingSessionResource
```

It contains all properties from the [Session](https://clerk.com/docs/tanstack-react-start/reference/objects/session.md) object, but guarantees that the `user` property is non-null and the `status` is either `active` or `pending`.

## `ActiveSessionResource`

An active session means the user is fully logged in and ready to use your app.

| Name   | Type     | Description                                                                                           |
| ------ | -------- | ----------------------------------------------------------------------------------------------------- |
| status | 'active' | Always 'active' for this session type.                                                                |
| user   | User     | The user associated with the session. This property is guaranteed to be non-null for active sessions. |

## `PendingSessionResource`

A pending session means the user has logged in but needs to complete one or more additional verification steps (like session tasks or authenticating with a second factor) before they have full access.

| Name        | Type        | Description                                                                                            |
| ----------- | ----------- | ------------------------------------------------------------------------------------------------------ |
| status      | 'pending'   | Always 'pending' for this session type.                                                                |
| user        | User        | The user associated with the session. This property is guaranteed to be non-null for pending sessions. |
| currentTask | SessionTask | The current pending task for the session. Read more about session tasks.                               |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
