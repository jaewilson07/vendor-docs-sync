# claude-code-docs

Mirrored from Anthropic's own Claude Code documentation site, discovered via
its sitemap (no upstream git repo of its own — unlike the other three
sources) by `watchdog/src/trigger/vendor-docs/claudeCodeDocsIngest.ts`
(`jaewilson07/trigger-dev-workflows`), daily at `0 9 * * *` UTC.

Design reference (not a runtime dependency):
[`ericbuess/claude-code-docs`](https://github.com/ericbuess/claude-code-docs)'s
`scripts/fetch_claude_docs.py` and `.github/workflows/update-docs.yml`.

Each synced page is written here alongside a `manifest.json` recording its
source URL and content hash (same purpose as `ericbuess/claude-code-docs`'s
`docs_manifest.json`).

This placeholder is replaced by the mirrored content on that task's first
successful production run — see jaewilson07/trigger-dev-workflows#128.
