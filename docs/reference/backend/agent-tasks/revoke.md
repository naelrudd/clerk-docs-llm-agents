# revoke()

> Agent Tasks are currently in beta. If you run into any issues, please reach out to our [support team](https://clerk.com/support).

Revokes the given Agent Task.

Returns the revoked [`AgentTask`](https://clerk.com/docs/reference/backend/types/backend-agent-task.md) object.

```typescript
function revoke(agentTaskId: string): Promise<Omit<AgentTask, "url">>
```

## Parameters

| Parameter     | Type     | Description                         |
| ------------- | -------- | ----------------------------------- |
| `agentTaskId` | `string` | The ID of the Agent Task to revoke. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
await clerkClient.agentTasks.revoke('agttsk_123')
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/agents/tasks/{agent_task_id}/revoke`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/agent-tasks/POST/agents/tasks/%7Bagent_task_id%7D/revoke){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
