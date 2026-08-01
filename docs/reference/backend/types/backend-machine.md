# The Backend Machine object

The Backend [Machine](https://clerk.com/docs/reference/backend/types/backend-machine.md) object holds information about a machine.

## Properties

| Property                                       | Type                                                                                                   | Description                                                                   |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| <a id="createdat"></a> `createdAt`             | `number`                                                                                               | The Unix timestamp when the machine was created.                              |
| <a id="defaulttokenttl"></a> `defaultTokenTtl` | `number`                                                                                               | The default time-to-live (TTL) in seconds for tokens created by this machine. |
| <a id="id"></a> `id`                           | `string`                                                                                               | The unique identifier for the machine.                                        |
| <a id="instanceid"></a> `instanceId`           | `string`                                                                                               | The ID of the instance the machine belongs to.                                |
| <a id="name"></a> `name`                       | `string`                                                                                               | The name of the machine.                                                      |
| <a id="scopedmachines"></a> `scopedMachines`   | <code><a href="https://clerk.com/docs/reference/backend/types/backend-machine.md">Machine</a>[]</code> | The machines that the current machine has access to.                          |
| <a id="secretkey"></a> `secretKey?`            | `string`                                                                                               | The secret key for the machine.                                               |
| <a id="updatedat"></a> `updatedAt`             | `number`                                                                                               | The Unix timestamp when the machine was last updated.                         |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
