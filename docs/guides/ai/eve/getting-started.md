# Get started with Clerk and eve

**Example Repository**

- [Clerk + eve agents starter](https://github.com/clerk/eve-agents/tree/main)

**Before you start**

- [A Clerk application is required](https://clerk.com/docs/getting-started/quickstart/setup-clerk.md)
- [Integrate Clerk into your Next.js application](https://clerk.com/docs/nextjs/getting-started/quickstart.md)

Built by Vercel, [eve](https://eve.dev) is a filesystem-first framework for durable AI agents. Identity, channels, instructions, tools, and subagents all live in conventional files you can read, diff, and version like any other code.

Clerk and eve fit together through four common patterns:

- [Custom channel auth](https://clerk.com/docs/guides/ai/eve/custom-channel-auth.md) — accept any Clerk token type at the channel boundary and map it to an eve principal.
- [API keys & M2M](https://clerk.com/docs/guides/ai/eve/api-keys-and-m2m.md) — API key callers and machine-to-machine calls between agents.
- [Authorize tool calls](https://clerk.com/docs/guides/ai/eve/authorize-tool-calls.md) — permission checks inside `execute`, plus brokered OAuth for tools that need provider tokens.
- [Enrich instructions](https://clerk.com/docs/guides/ai/eve/enriching-instructions.md) — rebuild the system prompt per session from the authenticated caller.

Each guide starts with a shadcn-installable helper, then builds the pattern from scratch if you'd rather wire it up yourself.

## Install the helpers via shadcn

The [`clerk/eve-agents`](https://github.com/clerk/eve-agents) repo doubles as a [shadcn GitHub registry](https://ui.shadcn.com/docs/registry/github) that exposes `clerkAuth()`, `clerkInstructions()`, `clerkM2MToken()`, `clerkConnect()`, and `clerkOAuthToken()` as a single drop-in.

filename: terminal
```bash
$ bunx --bun shadcn@latest add clerk/eve-agents/auth
```

The helpers land at `lib/clerk-auth/`:

```text
lib/clerk-auth/
├── index.ts        # clerkAuth and related types
├── instructions.ts # clerkInstructions
├── m2m.ts          # clerkM2MToken
└── connect.ts      # clerkConnect, clerkOAuthToken
```

## Try the demo

Clone [`clerk/eve-agents`](https://github.com/clerk/eve-agents) for a working monorepo that exercises every pattern in one place:

filename: terminal
```bash
$ git clone https://github.com/clerk/eve-agents.git
```

| Workspace                 | What it shows                                      |
| ------------------------- | -------------------------------------------------- |
| `apps/dashboard`          | Chat UI with a colocated main agent.               |
| `apps/project-agent`      | Remote subagent reachable only via M2M.            |
| `packages/clerk-eve-auth` | Clerk helpers shipped through the shadcn registry. |

Boot the dashboard, sign in, and switch between **Session**, **API key**, and **Unauthenticated** flows in the UI to watch each path behave differently. Ask the agent to list your GitHub repositories to trigger the OAuth connect flow; ask it to archive a project to watch M2M delegation in action.

## Detailed walkthroughs

Start with [Custom channel auth](https://clerk.com/docs/guides/ai/eve/custom-channel-auth.md) — it produces the eve principal every other pattern reads. From there, layer on [API keys & M2M](https://clerk.com/docs/guides/ai/eve/api-keys-and-m2m.md) for programmatic and agent-to-agent callers, [Authorize tool calls](https://clerk.com/docs/guides/ai/eve/authorize-tool-calls.md) to gate tools and broker provider OAuth, and [Enrich instructions](https://clerk.com/docs/guides/ai/eve/enriching-instructions.md) to personalize the system prompt per caller.

---

## Sitemap

[Overview of all docs pages](https://clerk.com/docs/llms.txt)
