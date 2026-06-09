# Database Documentation

This folder documents all data stores used by `<PROJECT_NAME>`. Each real store has its own child doc.

> Agents: read `pre-5-database-rules.md` before working on any data store. If you discover a store or table with no doc, create its doc immediately using `templates/database-store.md`.

## Data stores

| Store | Type | Doc | Purpose |
|---|---|---|---|
| `<store-name>` | `<e.g. PostgreSQL, Redis, S3>` | [<store-name>.md](./<store-name>.md) | `<one-line purpose>` |

## Maintenance rules

- Add a row to the table above for every real store when its doc is created.
- Do not document environment-specific connection strings or credentials here.
- Keep this index concise — detail lives in the per-store docs.
