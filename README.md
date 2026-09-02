# vendor-docs-sync

Mirrored vendor documentation that agents in the DataCrew workspace rely on. Each
top-level folder is mirrored from an upstream source by a Trigger.dev
`schedules.task` living in
[`jaewilson07/trigger-dev-workflows`](https://github.com/jaewilson07/trigger-dev-workflows)'s
`watchdog` project (`watchdog/src/trigger/vendor-docs/`), then ingested from
here into [mdrag](https://github.com/jaewilson07/mdrag) — mdrag's
`/ingest/git-repo` always points at a subfolder of this repo, never directly
at an upstream vendor repo.

See jaewilson07/trigger-dev-workflows#128 for the full design (why this repo
exists, the two mirror strategies, the mdrag collection-scoping and
stale-document cleanup fixes).

## Layout

| Folder                | Mirrored from                                                          | Strategy      | mdrag collection                          |
| ---------------------- | ------------------------------------------------------------------------ | ------------- | ------------------------------------------ |
| `domo-docs/`           | `DomoApps/domo-documentation-hub` (`s/article` subtree)                  | git-mirror    | `repo_domoapps-domo-documentation-hub`     |
| `letta-docs/`          | `letta-ai/letta-docs-md` (whole repo)                                    | git-mirror    | `repo_letta-ai-letta-docs-md`              |
| `trigger-dev-skills/`  | `triggerdotdev/skills` (whole repo)                                     | git-mirror    | `repo_triggerdotdev-skills`                |
| `claude-code-docs/`    | Anthropic's own docs site, discovered via its sitemap (no upstream repo) | crawl-mirror  | `repo_claude-code-docs` (created on first sync) |

Each task mirrors its source into its subfolder (committing + pushing only
when content actually changed), then mdrag ingests that subfolder with an
explicit `collection_id` — never the auto-derived one, which would otherwise
collapse all four subfolders into a single `repo_jaewilson07-vendor-docs-sync`
collection (see #128, "Collection collapse").

## Who writes here

Only the four vendor-docs-sync Trigger.dev tasks push to this repo (via a
GitHub PAT scoped for that purpose). No CI runs here and no other consumer is
assumed — see #128's Out of Scope section.

Until each task's first successful production run, the subfolders below carry
only a placeholder `README.md` rather than real mirrored content.
