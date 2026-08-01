# getSession()

Gets the given [`Session`](https://clerk.com/docs/reference/backend/types/backend-session.md).

```typescript
function getSession(sessionId: string): Promise<Session>
```

## Parameters

| Parameter   | Type     | Description                   |
| ----------- | -------- | ----------------------------- |
| `sessionId` | `string` | The ID of the session to get. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const sessionId = 'sess_123'

const response = await clerkClient.sessions.getSession(sessionId)
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `GET/sessions/{session_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/sessions/GET/sessions/%7Bsession_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
