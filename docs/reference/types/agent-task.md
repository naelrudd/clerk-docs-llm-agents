# AgentTask

An interface that represents an [Agent Task](https://clerk.com/docs/guides/development/testing/agent-tasks.md).

## Properties

| Name        | Type   | Description                                                                                                                                            |
| ----------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| agentId     | string | A stable identifier for the agent, unique per agent\_name within an instance.                                                                          |
| agentTaskId | string | A unique identifier for this Agent Task.                                                                                                               |
| url         | string | The Frontend API (FAPI) URL that, when visited, creates a session for the user. Only returned by create(); revoke() returns the Agent Task without it. |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
