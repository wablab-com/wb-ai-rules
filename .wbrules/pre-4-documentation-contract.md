# Documentation Contract

Load this file before starting work to understand where project documentation lives and how it is structured. The mandatory read/update protocol is defined in `pre-0-documentation-first.md` and applies here without repetition.

## Where project-specific docs live

All project-specific documentation, domain pages, feature pages, frontend docs, and database docs
are stored under `.wbdocs/` in the project repository — **not** in `.wbrules/`.

> `.wbrules/` contains only generic, reusable agent rules that apply to any project.
> Never add project-specific content to `.wbrules/`.

> **Docs protocol:** The mandatory read/update/discover protocol is defined in `pre-0-documentation-first.md`. Load that file first.

## Documentation entrypoints

Load in this order when starting any task:

- `.wbdocs/index.md` — top-level index; defines ownership and loading order for all docs in this project.
- `.wbdocs/environment.md` — mandatory environment registry; maps safe host fingerprints to `production`, `staging`, `dev`, `local`, or `test`, and defines environment-specific safety rules.
- `.wbdocs/domains/index.md` — one paragraph per domain; covers responsibility, boundaries, interactions, and cross-cutting concerns.
- `.wbdocs/frontend/index.md` — frontend structure, theming, libraries, state management, routing, and verification.
- `.wbdocs/database/index.md` — data stores, ownership, schema/migration paths, access patterns, and backup/restore notes.



## Three-layer documentation model

Use this model when the project is large enough to warrant it:

| Layer | Location | Purpose |
|---|---|---|
| Layer 1 | `.wbdocs/index.md`, `.wbdocs/environment.md`, `.wbdocs/domains/index.md` | Index and safety pages — map ownership, loading order, runtime environment, and guardrails |
| Layer 2 | `.wbdocs/domains/<domain-name>.md` | Domain pages — summarize features and boundaries |
| Layer 3 | `.wbdocs/domains/<domain-name>/<feature>.md` | Feature pages — detailed behavior, flows, files, data model, integrations, config, security, and testing |

## Page content rules

- **Domain index** (`.wbdocs/domains/index.md`): one paragraph per domain; cover responsibility, boundaries, interactions, and cross-cutting concerns; keep it concise.
- **Environment registry** (`.wbdocs/environment.md`): list each known environment with enough safe host fingerprints to identify it reliably, environment type, safety policy, test policy, data/credential risk notes, and escalation requirements. Hostname alone is not sufficient unless documented as unique.
- **Domain page** (`.wbdocs/domains/<domain-name>.md`): one paragraph per feature or major subsystem; include purpose, public behavior, rules and constraints, and references to detailed docs.
- **Feature page**: cover behavior and flows, key files/classes, data model, integrations, config, security, and testing.
- **High-level index pages**: stay concise and avoid changelogs.

## Templates

Reusable doc templates live in `.wbrules/templates/`. Use them when creating new pages in `.wbdocs/`.

| Template | Use for |
|---|---|
| [templates/domains-index.md](./templates/domains-index.md) | Domain index at `.wbdocs/domains/index.md` |
| [templates/environment-doc.md](./templates/environment-doc.md) | Environment registry at `.wbdocs/environment.md` |
| [templates/domain-doc.md](./templates/domain-doc.md) | New domain page at `.wbdocs/domains/<domain-name>.md` |
| [templates/features-index.md](./templates/features-index.md) | Features folder index at `.wbdocs/features/index.md` |
| [templates/feature-doc.md](./templates/feature-doc.md) | New feature page at `.wbdocs/features/<feature-name>.md` |
| [templates/database-index.md](./templates/database-index.md) | Database index at `.wbdocs/database/index.md` |
| [templates/database-store.md](./templates/database-store.md) | Per-store doc at `.wbdocs/database/<store-name>.md` — schema, migrations, backup, security |
| [templates/frontend-index.md](./templates/frontend-index.md) | Frontend standards at `.wbdocs/frontend/index.md` — stack, tokens, theme, layout, component patterns |

Copy the template, replace all `<PLACEHOLDER>` values, and remove the example feature section once real entries exist.

## AGENTS.md

Keep `AGENTS.md` (if present) high-signal and general. Link to `.wbrules/` and `.wbdocs/` rather than duplicating long rules inline.
