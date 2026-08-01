# The Backend Client object

The Backend `Client` object is similar to the [Client](https://clerk.com/docs/reference/objects/client.md) object as it holds information about the authenticated sessions in the current device. However, the Backend `Client` object is different from the `Client` object in that it is used in the [Backend API](https://clerk.com/docs/reference/backend-api/model/Client){{ target: '_blank' }} and is not directly accessible from the Frontend API.

## Properties

| Property                                                             | Type                                                                                                                                | Description                                                                                                                      |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| <a id="createdat"></a> `createdAt`                                   | `number`                                                                                                                            | The Unix timestamp when the `Client` was first created.                                                                          |
| <a id="id"></a> `id`                                                 | `string`                                                                                                                            | The unique identifier for the `Client`.                                                                                          |
| <a id="lastactivesessionid"></a> `lastActiveSessionId`               | `null | string`                                                                                                          | The ID of the last active [`Session`](https://clerk.com/docs/reference/backend/types/backend-session.md).                        |
| <a id="lastauthenticationstrategy"></a> `lastAuthenticationStrategy` | <code>null | <a href="https://clerk.com/docs/reference/types/last-authentication-strategy.md">LastAuthenticationStrategy</a></code> | The last authentication strategy used by the `Client`.                                                                           |
| <a id="sessionids"></a> `sessionIds`                                 | `string[]`                                                                                                               | An array of [Session](https://clerk.com/docs/reference/backend/types/backend-session.md) IDs associated with the `Client`.       |
| <a id="sessions"></a> `sessions`                                     | <code><a href="https://clerk.com/docs/reference/backend/types/backend-session.md">Session</a>[]</code>                              | An array of [`Session`](https://clerk.com/docs/reference/backend/types/backend-session.md) objects associated with the `Client`. |
| <a id="signinid"></a> `signInId`                                     | `null | string`                                                                                                          | The ID of the associated [SignIn](https://clerk.com/docs/reference/objects/sign-in.md).                                          |
| <a id="signupid"></a> `signUpId`                                     | `null | string`                                                                                                          | The ID of the associated [SignUp](https://clerk.com/docs/reference/objects/sign-up.md).                                          |
| <a id="updatedat"></a> `updatedAt`                                   | `number`                                                                                                                            | The Unix timestamp when the `Client` was last updated.                                                                           |

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
