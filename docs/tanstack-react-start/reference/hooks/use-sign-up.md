# useSignUp()

The `useSignUp()` hook provides access to the [SignUpFuture](https://clerk.com/docs/tanstack-react-start/reference/objects/sign-up-future.md) object, which allows you to check the current state of a sign-up attempt and manage the sign-up flow. You can use this to create a custom sign-up flow.

## Returns

| Name          | Type                                                                                                    | Description                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `errors`      | [SignUpErrors](https://clerk.com/docs/tanstack-react-start/reference/types/errors.md)                   | The errors that occurred during the last fetch of the underlying `SignUpFuture` resource. |
| `fetchStatus` | `"idle" | "fetching"`                                                                        | The fetch status of the underlying `SignUpFuture` resource.                               |
| `signUp`      | [SignUpFutureResource](https://clerk.com/docs/tanstack-react-start/reference/objects/sign-up-future.md) | The underlying `SignUpFuture` resource.                                                   |

> The `SignUpFuture` instance referenced by `signUp` does not have a stable identity, and will change as the sign-up flow progresses. Make sure you provide it in dependency arrays when using hooks such as `useEffect`, `useCallback`, or `useMemo`.

## Examples

For example usage of the `useSignUp()` hook, see the [Build your own UI](https://clerk.com/docs/guides/development/custom-flows/overview.md?sdk=tanstack-react-start) guides.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
