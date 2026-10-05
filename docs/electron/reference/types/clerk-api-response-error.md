# ClerkAPIResponseError

An interface that represents an error returned by the Clerk API.

## Properties

| Name          | Type             | Description                                                                                     |
| ------------- | ---------------- | ----------------------------------------------------------------------------------------------- |
| clerkError    | true             | Always true, marks this as a Clerk API error.                                                   |
| clerkTraceId? | string           | Optional. A trace ID from Clerk for debugging or support.                                       |
| errors        | ClerkAPIError[] | An array of error objects with more details about what went wrong.                              |
| message       | string           | The main error message.                                                                         |
| retryAfter?   | number           | Optional. If set, tells you how many seconds to wait before retrying (from Retry-After header). |
| status        | number           | The HTTP status code returned by the API.                                                       |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
