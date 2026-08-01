# Clerk Docs for LLM Agents

An unofficial, machine-readable mirror of the official [Clerk developer documentation](https://clerk.com/docs) — all pages mirrored as plain Markdown so AI coding assistants, LLM agents, RAG pipelines, and vector stores can consume them without scraping or HTML parsing.

Clerk provides authentication, user management, and organization (multi-tenancy) for web and mobile apps. This repo lets any agent answer integration questions — SDK setup (Next.js, React, Expo, etc.), prebuilt components, custom flows, Backend/Frontend APIs, webhooks, sessions, and more — directly from first-party documentation text.

## Why this exists

- Official docs ship an `llms.txt` / `llms-full.txt` index but not a plain cloneable corpus.
- Agents often need to read many pages during an integration; a local, structured Markdown mirror is faster and more reliable than live-fetching 2,300+ pages.
- Deterministic snapshot: pin a commit and know exactly what docs your agent is reading.

## How to use

Point your agent at this repo (or a subfolder). Suggested flow:

1. **Discover** — read [`llms.txt`](llms.txt) for the full page catalog, or
   [`llms-full.txt`](llms-full.txt) for the **entire docs corpus in one file** (~26 MB) — convenient for a single-context ingestion.
2. **Read** — load any page directly, e.g. `docs/getting-started/core-concepts.md`, `docs/guides/...`, `docs/reference/backend/...`.
3. **Embed/index** — feed the page tree into your vector store or context window.

### Layout

| Path | Contents |
|------|----------|
| [`docs.md`](docs.md) | Docs home / welcome |
| [`docs/`](docs/) | All documentation pages, mirrored 1:1 from `clerk.com/docs/...` |
| — `docs/getting-started/` | Core concepts, quickstarts |
| — `docs/guides/` | In-depth guides (auth flows, organizations, account portal, webhooks, etc.) |
| — `docs/reference/` | SDK & API reference (backend, frontend, components, API types) |
| — `docs/nextjs/`, `docs/react/`, `docs/react-router/`, `docs/tanstack-react-start/`, `docs/nuxt/`, `docs/vue/`, `docs/astro/`, `docs/expo/`, `docs/chrome-extension/`, `docs/js-frontend/`, `docs/expressjs/`, `docs/fastify/`, `docs/android/`, `docs/ios/`, `docs/ruby/`, `docs/go/` | Framework-specific SDK docs |
| [`llms.txt`](llms.txt) | Official full page index (titles + URLs) |
| [`llms-full.txt`](llms-full.txt) | Official full docs corpus, single file |

## Updating

Re-mirror from the official index:

```bash
curl -sL -o llms.txt https://clerk.com/docs/llms.txt
curl -sL -o llms-full.txt https://clerk.com/docs/llms-full.txt
# parse each https://clerk.com/docs/*.md link in llms.txt and download
```

## License & attribution

- This repository is **not affiliated with, endorsed by, or sponsored by Clerk Inc.**
- All documentation content is © Clerk Inc. and belongs to its respective owners.
- It mirrors the official [Clerk docs](https://clerk.com/docs/), which serves these pages as Markdown via `llms.txt` / `llms-full.txt` specifically for AI consumption.
- This repo is provided "as is" for reference/educational purposes. Refer to [clerk.com/docs](https://clerk.com/docs) for authoritative, always-current documentation.
- No API keys, secrets, or credentials are (or should be) stored here.
