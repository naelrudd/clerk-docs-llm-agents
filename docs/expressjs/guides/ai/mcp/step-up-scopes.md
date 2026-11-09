# Request more scopes with step-up authorization

**Before you start**

- [Build an MCP server](https://clerk.com/docs/guides/ai/mcp/build-mcp-server.md?sdk=expressjs)

When a client connects to your MCP server, the user approves a set of scopes. With step-up authorization, that first grant stays small, and the server asks for more scopes only when the agent calls a tool that needs them:

1. The agent calls a tool, such as `whoami`, with an access token that lacks the tool's scope.
2. Before the tool runs, your server answers `403 Forbidden` with a challenge: a `WWW-Authenticate: Bearer error="insufficient_scope", scope="..."` header that names the scopes to request.
3. The MCP client sends the user through Clerk's OAuth consent screen again, this time for the scopes in the challenge.
4. The client retries the tool call with the new access token.

The MCP TypeScript SDK (`@modelcontextprotocol/server`) sends this challenge for you when you set the `scopeChallenge` option of `registerTool()`. The `requireAdditionalScopes()` helper from [`@clerk/mcp-tools`](https://github.com/clerk/mcp-tools) builds that option from the scopes a tool needs.

This guide assumes that you've completed [Build an MCP server](https://clerk.com/docs/expressjs/guides/ai/mcp/build-mcp-server.md). It changes that server so that clients connect with only the `profile` scope, the baseline every request needs. Its `get_clerk_user_data` tool stops returning the email address, and a new `whoami` tool returns the user's ID and primary email. `email` becomes the step-up scope: the server asks clients for it the first time they call `whoami`.

Clients handle the challenge differently, so check your client's documentation. For example, Claude Code reports the missing scopes and asks the user to run `/mcp`, which opens the consent screen for those scopes. Clients without step-up support report a failed request and ask for the same baseline scopes when they reconnect, so their users can't use the tool unless the client requests the step-up scope when it connects.

1. ## Install the required versions

   The `scopeChallenge` option requires `@modelcontextprotocol/server` 2.1 or later, and `requireAdditionalScopes()` requires [`@clerk/mcp-tools`](https://github.com/clerk/mcp-tools) 0.9.0 or later. SDK 1.x (`@modelcontextprotocol/sdk`) and 2.0 don't have the option: TypeScript rejects it, and plain JavaScript ignores it.

   Install or update the packages.

   ```npm
   npm install @clerk/mcp-tools@latest @modelcontextprotocol/server @modelcontextprotocol/node
   ```

   The Express server in the [build guide](https://clerk.com/docs/expressjs/guides/ai/mcp/build-mcp-server.md) uses `streamableHttpHandler()` from `@clerk/mcp-tools/express`, which runs on SDK 1.x and can't send the challenge. This guide switches the `/mcp` route to `createMcpHandler()` from SDK 2 and adapts it to Express with `toNodeHandler()` from `@modelcontextprotocol/node`, which requires `@modelcontextprotocol/server` 2.4 or later. Keep `@modelcontextprotocol/sdk` installed: the metadata handlers from `@clerk/mcp-tools/express` still import it.
2. ## Allow clients to request the step-up scope

   A client can receive only the scopes your Clerk instance lets it request. If it asks for any other scope, Clerk rejects the authorization request with `invalid_scope`, and step-up fails. `email` is a built-in scope. For a scope of your own, such as `projects:write`, create a [custom scope](https://clerk.com/docs/guides/configure/auth-strategies/oauth/how-clerk-implements-oauth.md?sdk=expressjs#custom-scopes). Assign it to the pre-registered OAuth applications that can request it, and add it to the allowed scopes below for dynamic clients.

   MCP clients usually connect as dynamic clients, either through Client ID Metadata Documents (CIMD) or Dynamic Client Registration (DCR). By default, each dynamic client can request only the scopes it registered or first connected with. Clients that send no `scope` get Clerk's default scopes, `profile` and `email`, which would grant `email` up front. To let dynamic clients step up instead:

   1. In the Clerk Dashboard, navigate to the [**OAuth applications**](https://dashboard.clerk.com/~/oauth-applications) page and select the **Settings** tab.
   2. Under **Client onboarding**, set **Default scopes for dynamic clients** to `profile` only.
   3. In **Allowed scopes for dynamic clients**, add `profile`, `email`, and any custom scopes your tools need, and save your changes. The allowed scopes must include every default scope.

   These settings don't change the scopes you set on a pre-registered CIMD client. In the Clerk Dashboard, on the [**OAuth applications**](https://dashboard.clerk.com/~/oauth-applications) page, select the **Applications** tab, select the client, and edit its scopes to include the step-up scope.
3. ## Reduce the required scopes and add the tool's data

   In `lib/mcp-auth.ts`, reduce `REQUIRED_SCOPES` to the baseline. Remove the email address from `getUserProfile()`, because tokens with only `profile` can call it, and add `getWhoami()`.

   filename: lib/mcp-auth.ts

   ```ts
   // ...
   export const REQUIRED_SCOPES = ['profile', 'email']
   export const REQUIRED_SCOPES = ['profile']

   // ...

   export async function getUserProfile(userId: string) {
     const user = await clerkClient.users.getUser(userId)
     return {
       id: user.id,
       firstName: user.firstName,
       lastName: user.lastName,
       imageUrl: user.imageUrl,
       email:
         user.emailAddresses.find((address) => address.id === user.primaryEmailAddressId)
           ?.emailAddress ?? null,
     }
   }

   export async function getWhoami(userId: string) {
     const user = await clerkClient.users.getUser(userId)
     return {
       id: user.id,
       email:
         user.emailAddresses.find((address) => address.id === user.primaryEmailAddressId)
           ?.emailAddress ?? null,
     }
   }
   ```

   `verifyMcpToken()` must still return `resourceMetadataUrl`, as in the [build guide](https://clerk.com/docs/expressjs/guides/ai/mcp/build-mcp-server.md). The SDK puts it in the challenge's `resource_metadata` parameter, which tells the client where to find your authorization server.
4. ## Register the tool with a scope challenge

   Pass `requireAdditionalScopes()` the scopes the tool needs, as separate arguments, and use the result as the tool's `scopeChallenge` option.

   Update `index.ts`. On SDK 2, tool callbacks read the token from `ctx.http?.authInfo`, and the route passes the verified token to the SDK as `req.auth`.

   filename: index.ts

   ```ts
   import {
     authServerMetadataHandlerClerk,
     protectedResourceHandlerClerk,
     streamableHttpHandler,
   } from '@clerk/mcp-tools/express'
   import { McpServer } from '@modelcontextprotocol/sdk/server/mcp.js'
   import { requireAdditionalScopes } from '@clerk/mcp-tools/server'
   import { toNodeHandler } from '@modelcontextprotocol/node'
   import { createMcpHandler, McpServer } from '@modelcontextprotocol/server'
   import express from 'express'
   import cors from 'cors'
   import {
     getUserProfile,
     getWhoami,
     MCP_RESOURCE_URL,
     REQUIRED_SCOPES,
     RESOURCE_METADATA_URL,
     verifyMcpToken,
   } from './lib/mcp-auth.ts'

   const app = express()
   app.use(cors({ exposedHeaders: ['WWW-Authenticate'] }))
   app.use(express.json())

   function createServer() {
     const server = new McpServer({ name: 'profile-server', version: '1.0.0' })
     server.registerTool(
       'get_clerk_user_data',
       { description: 'Gets the authorized user’s profile and primary email' },
       { description: 'Gets the authorized user’s profile' },
       async (ctx) => {
         const userId = ctx.http?.authInfo?.extra?.userId
         if (typeof userId !== 'string') throw new Error('Missing authenticated user')
         return {
           content: [{ type: 'text', text: JSON.stringify(await getUserProfile(userId)) }],
         }
       },
     )
     server.registerTool(
       'whoami',
       {
         description: 'Gets the authorized user’s ID and primary email. Needs the email scope.',
         scopeChallenge: requireAdditionalScopes('email'),
       },
       async (ctx) => {
         const userId = ctx.http?.authInfo?.extra?.userId
         if (typeof userId !== 'string') throw new Error('Missing authenticated user')
         return {
           content: [{ type: 'text', text: JSON.stringify(await getWhoami(userId)) }],
         }
       },
     )
     return server
   }

   const mcpHandler = toNodeHandler(createMcpHandler(createServer))

   app.post('/mcp', async (req, res) => {
     const authInfo = await verifyMcpToken(
       new Request(MCP_RESOURCE_URL, {
         headers: { authorization: req.get('authorization') ?? '' },
       }),
     )
     const challenge = `Bearer resource_metadata="${RESOURCE_METADATA_URL}"`
     if (!authInfo) {
       res.status(401).set('WWW-Authenticate', challenge).json({ error: 'invalid_token' })
       return
     }
     if (!REQUIRED_SCOPES.every((scope) => authInfo.scopes.includes(scope))) {
       // Keep the granted scopes, so the new token doesn't lose them
       const scopes = [...new Set([...authInfo.scopes, ...REQUIRED_SCOPES])].join(' ')
       res
         .status(403)
         .set(
           'WWW-Authenticate',
           `${challenge}, error="insufficient_scope", scope="${REQUIRED_SCOPES.join(' ')}"`,
         )
         .set('WWW-Authenticate', `${challenge}, error="insufficient_scope", scope="${scopes}"`)
         .json({ error: 'insufficient_scope' })
       return
     }

     Object.assign(req, { auth: authInfo })
     await streamableHttpHandler(createServer)(req, res)
     await mcpHandler(req, res, req.body)
   })
   app.all('/mcp', (_, res) => {
     res.status(405).set('Allow', 'POST, OPTIONS').json({ error: 'method_not_allowed' })
   })
   app.get(
     '/.well-known/oauth-protected-resource/mcp',
     protectedResourceHandlerClerk({
       resource: MCP_RESOURCE_URL,
       scopes_supported: REQUIRED_SCOPES,
     }),
   )
   app.get('/.well-known/oauth-authorization-server', authServerMetadataHandlerClerk)
   app.listen(3000)
   ```
5. ## Test step-up

   Restart your server, clear your MCP client's stored token for this server, and then reconnect so it gets a new token. A token left over from the build guide already has `email`, so `whoami` would run without step-up. If your client requests the baseline scopes, the consent screen lists your basic profile information, but not your email address. Ask the agent "Who am I?" so it calls `whoami`. If your client supports step-up, the consent screen opens again for `email`, and the call succeeds. In Claude Code, run `/mcp`, re-authenticate the server, and then ask again.

   If the consent screen doesn't open again, check the `403` response's `WWW-Authenticate` header. Confirm that its `scope` lists the token's granted scopes followed by `email`, such as `profile offline_access email`, and that its `resource_metadata` is your protected resource metadata URL. If Clerk then answers the authorization request with `invalid_scope`, [allow clients to request the step-up scope](https://clerk.com/docs/expressjs/guides/ai/mcp/step-up-scopes.md#allow-clients-to-request-the-step-up-scope).

## Best practices

Follow these rules for every tool that uses `scopeChallenge`.

### Challenge for the full scope set

The `scope` in the challenge is the complete set the client should request, including the scopes the token already has. Some clients request exactly the challenged scopes, and the new token replaces the old one. A challenge for only `email` produces a token without `profile`, and every other tool then fails or challenges again.

`requireAdditionalScopes()` requires the tool's scopes in addition to the ones the token already has, so it challenges for the granted scopes plus the missing ones. The SDK's own `requireScopes()` helper challenges for only the scopes you list, so if you use it, list every scope the token should keep.

### Keep step-up scopes out of the baseline

Add the step-up scope only to the tool's `scopeChallenge`. Anywhere else, step-up doesn't work as intended:

- **Route checks**, such as the `requiredScopes` of `withMcpAuth()` or the check in the Express route, run on every request, including `initialize` and `tools/list`. A step-up scope there rejects every token without it.
- **`scopes_supported`** in your protected resource metadata guides what MCP clients request when they first connect, unless the `401` challenge names scopes of its own. Keep it to the baseline, as in the [build guide](https://clerk.com/docs/expressjs/guides/ai/mcp/build-mcp-server.md). It doesn't limit what a token can get, so a client can still request step-up scopes up front.

## Limitations

`scopeChallenge` applies only to certain requests, so check these limits before you rely on it.

### When the SDK sends the challenge

The SDK sends the challenge only when:

- The server runs `@modelcontextprotocol/server` 2.1 or later. Tools behind the `streamableHttpHandler()` adapters in `@clerk/mcp-tools/express` and `@clerk/mcp-tools/hono` run SDK 1.x and must check their scopes themselves.
- The request comes over HTTP, through `createMcpHandler()` or the Streamable HTTP transport. Over stdio (local servers), the tool runs without the challenge.
- The request carries auth info. `requireAdditionalScopes()` and `requireScopes()` leave unauthenticated requests to your authentication check.

### How the challenge behaves

- The SDK checks `tools/call`, `resources/read`, and `prompts/get` requests for enabled tools, resources, and prompts. `registerResource()` and `registerPrompt()` accept the same `scopeChallenge` option.
- The challenge runs before the SDK validates the tool's arguments.
- `tools/list` still includes the tool for tokens that lack its scope. Mention the step-up scope in the tool's description so agents know to expect another consent screen.
- If a `scopeChallenge` function throws, the SDK answers `500 Internal Server Error`. `requireAdditionalScopes()` validates its scopes when you call it. It throws a `Clerk error:` at startup if you pass no scopes, an empty string, or a scope with a space, quote, backslash, control character, or non-ASCII character.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
