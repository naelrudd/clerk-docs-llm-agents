# deleteUserWeb3Wallet()

Deletes a Web3 wallet identification for the given user.

Returns the [`DeletedObject`](https://clerk.com/docs/reference/backend/types/deleted-object.md) object.

```typescript
function deleteUserWeb3Wallet(params: DeleteWeb3WalletParams): Promise<DeletedObject>
```

## `DeleteWeb3WalletParams`

| Property                                                             | Type     | Description                                         |
| -------------------------------------------------------------------- | -------- | --------------------------------------------------- |
| <a id="userid"></a> `userId`                                         | `string` | The ID of the user to delete the Web3 wallet for.   |
| <a id="web3walletidentificationid"></a> `web3WalletIdentificationId` | `string` | The ID of the Web3 wallet identification to delete. |

## Usage

> Using `clerkClient` varies based on the SDK you're using. Refer to the [overview](https://clerk.com/docs/reference/backend/overview.md) for usage details, including guidance on [how to access the `userId` and other properties](https://clerk.com/docs/reference/backend/overview.md#example-get-the-user-id-and-other-properties).

```tsx
const userId = 'user_123'
const web3WalletIdentificationId = 'web3_wallet_identification_123'

const response = await clerkClient.users.deleteUserWeb3Wallet({
  userId,
  web3WalletIdentificationId,
})
```

## Backend API (BAPI) endpoint

This method in the SDK is a wrapper around the BAPI endpoint `DELETE/users/{user_id}/web3_wallets/{web3_wallet_identification_id}`. See the [BAPI reference](https://clerk.com/docs/reference/backend-api/tag/users/DELETE/users/%7Buser_id%7D/web3_wallets/%7Bweb3_wallet_identification_id%7D){{ target: '_blank' }} for more information.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
