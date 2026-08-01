# createTestingToken()

Creates a [Testing Token](https://clerk.com/docs/guides/development/testing/overview.md#testing-tokens) for the instance.

Returns the created [`TestingToken`](https://clerk.com/docs/reference/backend/types/backend-testing-token.md) object.

```typescript
function createTestingToken(): Promise<TestingToken>
```

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const response = await clerk.testingTokens.createTestingToken()
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `POST/testing_tokens`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/testing-tokens/POST/testing_tokens){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
