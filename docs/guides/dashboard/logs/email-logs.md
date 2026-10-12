# Email Logs

The [**Email Logs**](https://dashboard.clerk.com/~/email-logs) page of the Clerk Dashboard shows a reverse-chronological feed of delivery events for transactional emails sent through Clerk. Use it to check whether a receiving mail service accepted a message or whether delivery was delayed or failed.

To learn how to filter entries, inspect event details, and understand retention, see the [Logs overview](https://clerk.com/docs/guides/dashboard/logs/overview.md).

## Access

The following workspace members can view Email Logs:

- Members with the **Owner**, **Admin**, or **Support** [Role](https://clerk.com/docs/guides/dashboard/manage-team-access.md#available-roles).
- Members with the **Developer** Role, in **development instances** only.

## Supported events

The following table lists event types to use when filtering Email Logs in the Clerk Dashboard.

| Event type   | Description                               |
| ------------ | ----------------------------------------- |
| `accepted`   | Message accepted for processing           |
| `delivered`  | Message delivered to the recipient server |
| `deferred`   | Delivery deferred by the recipient server |
| `bounced`    | Delivery bounced by the recipient server  |
| `dropped`    | Message dropped by delivery policy        |
| `blocked`    | Delivery blocked by the recipient server  |
| `complained` | Recipient marked the message as spam      |

## Troubleshoot delivery

If a recipient reports a missing email, filter by their email address and the time the message was expected. Review the event details to determine whether the receiving service accepted the message or whether delivery was delayed or failed. You can use the message ID to follow events for the same message.

Events such as `bounced`, `complained`, and `dropped` can help explain why Clerk stopped sending to an address. For eligible events, members with the **Owner**, **Admin**, or **Support** Role can select **Remove address** in the event details.

See [Email suppression lists](https://clerk.com/docs/guides/development/troubleshooting/email-suppression-lists.md) to understand these events and when an address can be removed from a suppression list. For broader troubleshooting, see [Email deliverability](https://clerk.com/docs/guides/development/troubleshooting/email-deliverability.md).

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
