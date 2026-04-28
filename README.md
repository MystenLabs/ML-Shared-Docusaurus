# Mysten Labs Shared Docusaurus Documentation Components

This repo is the single source of truth for shared custom components, plugins, and scripts used across all Sui Stack documentation sites. Changes here are automatically synced to each docs repo via [docs-shared-components](https://github.com/jessiemongeon1/docs-shared-components).

## Sync behavior

- When `master` is updated, a CI job opens PRs to each docs repo with the changed files.
- Each repo only receives files it already uses — repo-specific files are never added.
- Files with repo-specific imports (e.g. `ImportContent/index.tsx`) are excluded from sync.
- Walrus repos receive Walrus Foundation license headers; all others receive Mysten Labs headers.

## What each repo pulls

All repos share a common base. The table below shows which files from this repo are synced to each site.

| File | Sui | Walrus | Seal | SuiNS |
|---|---|---|---|---|
| `components/Cards/index.tsx` | x | x | x | x |
| `components/Glossary/GlossaryPage.tsx` | x | x | x | x |
| `components/Glossary/GlossaryProvider.tsx` | x | x | x | x |
| `components/Glossary/Term.tsx` | x | x | x | x |
| `components/Glossary/term.module.css` | x | x | x | x |
| `components/ImportContent/index.tsx` | * | * | * | * |
| `components/ImportContent/utils.js` | x | x | x | x |
| `components/RelatedLink/index.tsx` | x | x | x | x |
| `components/SidebarIframe/index.js` | x | x | x | x |
| `components/Snippet/index.tsx` | x | x | x | x |
| `components/ThemeToggle/index.tsx` | x | x | x | x |
| `components/UnsafeLink/index.tsx` | x | x | x | x |
| `css/details.css` | x | x | x | x |
| `js/check-links.mjs` | x | | | |
| `js/convert-release-notes.js` | | x | x | x |
| `js/generate-llmstxt.mjs` | x | | | |
| `js/serve-with-rewrites.js` | | | x | x |
| `js/tabs-md.client.js` | x | x | x | x |
| `js/test-markdown-export.js` | | | x | x |
| `js/utils.js` | x | x | x | x |
| `plugins/descriptions/index.js` | x | x | x | x |
| `plugins/inject-code/index.js` | x | x | x | x |
| `plugins/inject-code/stepLoader.js` | x | x | x | x |
| `plugins/plausible/client/index.ts` | x | x | x | x |
| `plugins/plausible/index.ts` | x | x | x | x |
| `plugins/remark-glossary.js` | x | x | x | x |
| `plugins/tabs-md-client/index.mjs` | x | x | x | x |

`*` = present in the repo but excluded from automatic sync (contains repo-specific imports)

### Target repo paths

| Repo | Shared directory |
|---|---|
| [MystenLabs/sui](https://github.com/MystenLabs/sui) | `docs/site/src/shared/` |
| [MystenLabs/walrus](https://github.com/MystenLabs/walrus) | `docs/site/src/shared/` |
| [MystenLabs/seal](https://github.com/MystenLabs/seal) | `docs/site/src/shared/` |
| [MystenLabs/suins-contracts](https://github.com/MystenLabs/suins-contracts) | `documentation/site/src/shared/` |

## Components that cannot be shared

The following use per-site API keys and are managed individually:

1. Algolia Search (`components/Search`)
2. Push Feedback

Additionally, all `src/theme` and `css/` components are unique to each site to prevent styling conflicts.
