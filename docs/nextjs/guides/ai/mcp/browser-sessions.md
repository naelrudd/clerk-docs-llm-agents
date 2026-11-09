# Sign agents in to your app with a one-time link (Beta)

> **Beta:** This feature is currently in beta. Functionality may change before general availability. If you run into any issues, please reach out to our [support team](https://clerk.com/contact/support).

When an agent uses a browser for your user and reaches your app's sign-in page, it usually stops there, or asks the user for a password. A `create_browser_session` tool on your MCP server lets the agent get a one-time link instead. The link opens your app already signed in as the user that the MCP access token belongs to.

You add the tool with [`@clerk/mcp-tools`](https://github.com/clerk/mcp-tools). It creates the link with [Agent Tasks](https://clerk.com/docs/guides/development/testing/agent-tasks.md?sdk=nextjs) and takes the user from the verified access token, never from the tool's input. The agent can set only the path in your app and a short task description.

This guide adds the tool to the MCP server from [Build an MCP server](https://clerk.com/docs/nextjs/guides/ai/mcp/build-mcp-server.md). Follow that guide first. The tool relies on its `verifyMcpToken()`, which checks the token's audience and returns the result of `verifyClerkToken()`. Without the audience check, any OAuth access token your instance issued, to any OAuth application, could create a link.

1. ## Install dependencies

   The tool requires `@clerk/mcp-tools` 0.9.0 or later. [Step-up authorization](https://clerk.com/docs/nextjs/guides/ai/mcp/step-up-scopes.md) requires `@modelcontextprotocol/server` 2.1 or later.

   ```npm
   npm install @clerk/mcp-tools@latest @modelcontextprotocol/server@latest
   ```
2. ## Create a scope for the tool

   The link signs a browser in to your app as the user, so require a scope that the user approves for each MCP client. Use a scope for this tool only, not one that nearly every client gets, such as `profile` or `email`. With a common scope, every MCP client the user connects can open your app as them.

   1. In the Clerk Dashboard, navigate to the [**OAuth applications**](https://dashboard.clerk.com/~/oauth-applications) page.
   2. Select the **Scopes** tab and create a [custom scope](https://clerk.com/docs/guides/configure/auth-strategies/oauth/how-clerk-implements-oauth.md?sdk=nextjs#custom-scopes) named `browser_session`.
   3. Assign the scope to the OAuth applications that may use the tool.
   4. If MCP clients register themselves through [Client ID Metadata Documents (CIMD)](https://clerk.com/docs/guides/configure/auth-strategies/oauth/client-id-metadata-documents.md?sdk=nextjs) or dynamic client registration, select the **Settings** tab and add the scope to **Allowed scopes for dynamic clients**. The list limits what those clients can request, so also include every default scope and any other scope they need.

   Don't add the scope to the default scopes, so a client gets it only after the user approves it.

   In `lib/mcp-auth.ts`, export the scope next to `REQUIRED_SCOPES`:

   filename: lib/mcp-auth.ts

   ```ts
   export const BROWSER_SESSION_SCOPES = ['browser_session']
   ```

   Keep it out of `REQUIRED_SCOPES`. Those scopes are required for every request to your MCP server, while `BROWSER_SESSION_SCOPES` is required only by this tool.
3. ## Advertise the scope

   Add the scope to `scopes_supported` in your protected resource metadata. Some MCP clients request this list when they first connect, and for clients without step-up authorization, it's the only way to ask for the scope. If that list includes a scope a client can't request, Clerk rejects the whole request with `invalid_scope`, and the client can't connect to your MCP server. Complete the previous step first.

   filename: app/.well-known/oauth-protected-resource/mcp/route.ts

   ```ts
   import {
     metadataCorsOptionsRequestHandler,
     protectedResourceHandlerClerk,
   } from '@clerk/mcp-tools/next'
   import { BROWSER_SESSION_SCOPES, MCP_RESOURCE_URL, REQUIRED_SCOPES } from '../../../../lib/mcp-auth'

   const handler = protectedResourceHandlerClerk({
     resource: MCP_RESOURCE_URL,
     scopes_supported: [...REQUIRED_SCOPES, ...BROWSER_SESSION_SCOPES],
   })
   const corsHandler = metadataCorsOptionsRequestHandler()

   export { handler as GET, corsHandler as OPTIONS }
   ```
4. ## Register the tool

   Create the tool with `createBrowserSessionTool()` and pass the result to `server.registerTool()`. Set `destinationUrl` to the page of your app the link opens. It must be on a domain of the same Clerk instance as your MCP server. Keep the localhost value during local development and replace `APP_URL` with your HTTPS URL when you deploy.

   filename: app/[transport]/route.ts

   ```ts
   import { createMcpHandler, withMcpAuth } from 'mcp-handler'
   import {
     browserSessionInstructions,
     createBrowserSessionTool,
   } from '@clerk/mcp-tools/create-browser-session'
   import {
     BROWSER_SESSION_SCOPES,
     getUserProfile,
     MCP_RESOURCE_URL,
     REQUIRED_SCOPES,
     verifyMcpToken,
   } from '../../lib/mcp-auth'

   const APP_URL = 'http://localhost:3000/'

   // Created once, so a bad configuration fails at startup instead of on every request
   const browserSessionTool = createBrowserSessionTool({
     secretKey: process.env.CLERK_SECRET_KEY!,
     destinationUrl: APP_URL,
     requiredScopes: BROWSER_SESSION_SCOPES,
   })

   const handler = createMcpHandler(
     (server) => {
       server.registerTool(...browserSessionTool)

       // Your other tools...
     },
     { instructions: browserSessionInstructions(APP_URL) },
   )

   const authHandler = withMcpAuth(handler, (request) => verifyMcpToken(request), {
     required: true,
     requiredScopes: REQUIRED_SCOPES,
     resourceUrl: new URL(MCP_RESOURCE_URL).origin,
     resourceMetadataPath: '/.well-known/oauth-protected-resource/mcp',
   })

   export { authHandler as GET, authHandler as POST }
   ```

   `browserSessionInstructions()` tells agents about the tool in your server's instructions. Some MCP clients show agents only the server instructions until the agent searches for a tool, so without them an agent may open your app and stop at the sign-in page.
5. ## Try it

   Start your app and [connect an MCP client](https://clerk.com/docs/guides/ai/mcp/connect-mcp-client.md?sdk=nextjs) that can use a browser. Ensure the agent's browser profile isn't signed in to your app. If Clerk detects another session in that browser, it refuses the link, and the link stays valid.

   Ask the agent to open your app. It should call `create_browser_session`, either first or when it reaches the sign-in page, and open the link it gets back. If your MCP client asks, approve the `browser_session` scope.

## What the session can do

By default, the link starts a restricted session. The session can read data and refresh its own session token. Clerk's Frontend API refuses every other write from it, including:

- Session touch requests, which update the session's last active time
- Sign-in, sign-up, and sign-out
- A switch to another session or Organization
- Changes to the user's own profile and Organizations
- Reverification, and OAuth consent and approval

The agent controls the browser, so these limits keep it from approving its own OAuth grant or changing the user's credentials.

Clerk also refuses JWT template and Firebase tokens, so `getToken({ template })` fails in a restricted session.

Your app's backend sees an ordinary signed-in session, and Clerk doesn't limit what your own API lets it do. To treat agent sessions differently in your backend, check for the `agt` claim in the session's `sessionClaims`.

If Clerk doesn't confirm the restriction, the tool tries to revoke the link, returns no link, and fails with the `restricted_not_applied` error code.

To start an ordinary session instead, pass `restricted: false` to `createBrowserSessionTool()`.

## Security and limits

- The link is a credential: anyone who has it before it's used or expires can sign in as the user. The tool never includes it in errors or logs, but the tool result contains it so that the agent can open it. Don't log tool results, and treat MCP client and gateway logs of tool results as credentials.
- Each link works once and expires after 1 hour. The session it starts lasts up to 30 minutes by default. Set `sessionMaxDurationInSeconds` to change that.
- The agent can pass a `path`, such as `/settings`, with an optional query and hash. It replaces the path of `destinationUrl`, and the tool refuses any path that would leave your app.
- The session starts in the user's last active Organization if they're still a member, and otherwise in their personal workspace. A restricted session can't start in the personal workspace when your instance has **Membership required** turned on. In that case, the tool fails with the `organization_rejected` error code. A restricted session can't switch to another Organization.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
