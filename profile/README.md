# cocoindex-gh-sandbox

**Dedicated sandbox org for testing the CocoIndex Code Plus (`cccx`) indexer —
isolated from production.**

It holds stable test fixtures so the indexer can be exercised end-to-end against
GitHub without ever touching the real
[`cocoindex-io`](https://github.com/cocoindex-io) org. Keeping the fixtures and
the indexer's GitHub App here is a hard security boundary: the App installed on
this org **cannot read any production repository**.

## What lives here

- **`cocoindex`** — a snapshot of `cocoindex-io/cocoindex` content (CI disabled)
  used as a corpus for the indexer to read. Refreshed occasionally to track
  upstream; otherwise stable.
- **`index-configs`** — tenant configuration the indexer reads (which repos to
  index, with include/exclude globs).

These are **maintained, reusable fixtures** — the E2E tests point at them, so
they're meant to stay (refreshed in place, not thrown away). A read-only
**GitHub App** (`cocoindex-github-sandbox-for-dev`) gives the indexer read
access to them.

## Ground rules

- ⛔ **No production data** — only test content (snapshots / synthetic fixtures).
- ⛔ **No secrets in repos** — no private keys, tokens, or `.env` files. App
  private keys stay on developer machines / in CI secret stores.
- 🚫 **CI is intentionally disabled** on fixtures (workflow folders renamed) so
  pushes don't trigger Actions runners.

Maintained by the CocoIndex team for developing the enterprise edition of
CocoIndex Code (`cocoindex-code-plus`).
