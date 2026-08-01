# SessionStatus

The `SessionStatus` enum is used to indicate the status of a session.

```tsx
type SessionStatus =
  | 'abandoned'
  | 'active'
  | 'pending'
  | 'ended'
  | 'expired'
  | 'removed'
  | 'replaced'
  | 'revoked'
```

## Properties

| Value       | Description                                                                                                                                                                                                            |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `abandoned` | The session was abandoned client-side.                                                                                                                                                                                 |
| `active`    | The session is valid and all activity is allowed.                                                                                                                                                                      |
| `pending`   | The user has signed in but hasn't completed [session tasks](https://clerk.com/docs/guides/configure/session-tasks.md?sdk=nextjs).                                                                                      |
| `ended`     | The user signed out of the session, but the [Session](https://clerk.com/docs/nextjs/reference/objects/session.md) remains in the [Client](https://clerk.com/docs/nextjs/reference/objects/client.md) object.           |
| `expired`   | The period of allowed activity for this session has passed.                                                                                                                                                            |
| `removed`   | The user signed out of the session and the [Session](https://clerk.com/docs/nextjs/reference/objects/session.md) was removed from the [Client](https://clerk.com/docs/nextjs/reference/objects/client.md) object.      |
| `replaced`  | The session has been replaced by another one, but the [Session](https://clerk.com/docs/nextjs/reference/objects/session.md) remains in the [Client](https://clerk.com/docs/nextjs/reference/objects/client.md) object. |
| `revoked`   | The application ended the session and the [Session](https://clerk.com/docs/nextjs/reference/objects/session.md) was removed from the [Client](https://clerk.com/docs/nextjs/reference/objects/client.md) object.       |

[session-ref]: /docs/reference/objects/session

[client-ref]: /docs/reference/objects/client

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
