# cocoindex-gh-sandbox

**Throwaway sandbox org for testing — not production.**

It exists so the **CocoIndex Code Plus (`cccx`) indexer** can be exercised
end-to-end against GitHub without ever touching the real
[`cocoindex-io`](https://github.com/cocoindex-io) org. Keeping the test fixtures
and the indexer's GitHub App here is a hard security boundary: the App installed
on this org **cannot read any production repository**.

## What lives here

- **Test fixture repos** — e.g. `cocoindex` (a CI-disabled snapshot of
  `cocoindex-io/cocoindex` used as a corpus to index) and `index-configs`
  (tenant configuration for the indexer). These are **disposable**: they may be
  force-pushed, rebuilt, or deleted at any time. Don't depend on them for
  anything real.
- A read-only **GitHub App** (`cocoindex-github-sandbox-for-dev`) the indexer
  uses to read these repos.

## Ground rules

- ⛔ **No production data** — only synthetic or public-derived test content.
- ⛔ **No secrets in repos** — no private keys, tokens, or `.env` files. App
  private keys stay on developer machines / in CI secret stores.
- 🚫 **CI is intentionally disabled** on fixtures (workflow folders are renamed),
  so pushes don't trigger Actions runners.
- ♻️ Treat every repo here as **ephemeral**.

Maintained by the CocoIndex team for developing the enterprise edition of
CocoIndex Code (`cocoindex-code-plus`).
