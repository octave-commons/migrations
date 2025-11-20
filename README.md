# Promethean Migrations

Deterministic, idempotent repo migrations.

- **State file**: `.promethean/migrations.json` (at repo root)
- **Location**: `packages/migrations/src/migrations/*.ts`
- **Runner**: `pnpm tsx packages/migrations/src/index.ts up`

## Why
Keep housekeeping out of ad-hoc scripts. Track what ran, when, and re-run safely.

## Writing a migration
Create a file like `packages/migrations/src/migrations/001-labels-to-tags.ts` that exports:

```ts
export const id = 1;
export const name = 'labels-to-tags';
export async function up(ctx: Ctx): Promise<void> { /* ... */ }
```

`Ctx` exposes utilities and shared libs (gray-matter/yaml via `@promethean-os/markdown/frontmatter`).

## Running
```bash
pnpm tsx packages/migrations/src/index.ts up         # apply pending
pnpm tsx packages/migrations/src/index.ts list       # show applied/pending
```

## Conventions
- Idempotent: running `up` again changes nothing.
- No regex-only rewrites of frontmatter — always parse & stringify.
- Small, reversible, logged.

<!-- READMEFLOW:BEGIN -->
# @promethean-os/migrations



[TOC]


## Install

```bash
pnpm -w add -D @promethean-os/migrations
```

## Quickstart

```ts
// usage example
```

## Commands

- `build`
- `clean`
- `typecheck`
- `test`
- `lint`
- `lisp`
- `coverage`
- `test:markdown`
- `format`

## License

GPL-3.0-only


### Package graph

```mermaid
flowchart LR
  _promethean_os_migrations["@promethean-os/migrations\n0.0.1"]
  _promethean_os_embedding["@promethean-os/embedding\n0.0.1"]
  _promethean_os_persistence["@promethean-os/persistence\n0.0.1"]
  _promethean_os_discord["@promethean-os/discord\n0.0.1"]
  _promethean_os_migrations --> _promethean_os_embedding
  _promethean_os_migrations --> _promethean_os_persistence
  _promethean_os_discord --> _promethean_os_migrations
  classDef focal fill:#fdf6b2,stroke:#222,stroke-width:2px;
  class _promethean_os_migrations focal;
```


<!-- READMEFLOW:END -->
