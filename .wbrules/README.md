# .wbrules

Generic, reusable agent rules that apply to **any** project this folder is attached to.

> 📋 **Agent working checklist:** [`index.md`](./index.md) — maintain and report its status in every progress update and in the final completion message.

---


## ⚠️ Important: Do NOT add project-specific content here

`.wbrules/` is a shared, project-agnostic ruleset.

- **Do NOT** add project-specific rules, domain docs, feature pages, or any content tied to a particular codebase here.
- **All project-specific and custom documentation belongs in `.wbdocs/`** — a sibling folder created per project.

---

## 📌 Foundation: Documentation is the most important rule

> **Documentation is not a step. It is the framework.**

Reading and maintaining docs is the single most important practice in this ruleset. All other rules depend on it.

- **`pre-0-documentation-first.md` MUST be loaded before any other file.**
- Read `.wbdocs/index.md` before every task — code, investigation, or question.
- Update affected docs after every task — even if no code changed.
- A task is not done until the docs reflect the current state of the system.

See [pre-0-documentation-first.md](./pre-0-documentation-first.md) for the full protocol.

---

## File naming convention

Files are prefixed to signal **when** the agent should load them:

| Prefix | When to load | Purpose |
|---|---|---|
| `pre-N-` | **Before starting** any task | Context, constraints, architecture, and guardrails the agent must internalize before touching code |
| `post-N-` | **After finishing** any task | Checklists and actions the agent must complete before marking the task done |

`N` is a zero-based integer that defines the **loading order** within each group. Load `pre-` files in ascending order, then do the work, then apply `post-` files in ascending order.

---

## Loading order

### Pre (load before starting work)

| File | Purpose |
|---|---|
| [pre-0-documentation-first.md](./pre-0-documentation-first.md) | 📌 **Foundation** — mandatory read/update protocol for all tasks including questions |
| [pre-1-core-principles.md](./pre-1-core-principles.md) | Foundational values all agents must uphold |
| [pre-2-code-structure.md](./pre-2-code-structure.md) | How to organize and write code |
| [pre-3-safety-and-design.md](./pre-3-safety-and-design.md) | Security, error handling, and hard limits |
| [pre-4-documentation-contract.md](./pre-4-documentation-contract.md) | Where docs live (`.wbdocs/`) and how they are structured |
| [pre-5-database-rules.md](./pre-5-database-rules.md) | Data store documentation, migration discipline, secret handling, and data-correctness rules |
| [pre-6-api-building.md](./pre-6-api-building.md) | Design, contracts, HTTP semantics, security, and testing rules for building APIs |
| [pre-7-api-integration.md](./pre-7-api-integration.md) | Reliability, security, contracts, error handling, and testing rules for consuming external APIs |
| [pre-8-frontend-rules.md](./pre-8-frontend-rules.md) | Architecture, accessibility, performance, security, and platform rules for web, mobile, and desktop UI |

### Post (apply after finishing work)

| File | Purpose |
|---|---|
| [post-0-tests.md](./post-0-tests.md) | Run and add tests after changes |
| [post-1-build-hygiene.md](./post-1-build-hygiene.md) | Fix warnings and keep build clean |
| [post-2-update-documentation.md](./post-2-update-documentation.md) | Keep `.wbdocs/` in sync — mandatory after every task including questions |

---

## Companion folder: `.wbdocs/`

Project-specific documentation lives in `.wbdocs/` alongside this folder.
See [pre-4-documentation-contract.md](./pre-4-documentation-contract.md) for the full documentation structure.

---

## Templates

Reusable doc starters live in `templates/`. Copy and fill them when creating new `.wbdocs/` pages.

| Template | Use for |
|---|---|
| [templates/domains-index.md](./templates/domains-index.md) | Domain index at `.wbdocs/domains/index.md` |
| [templates/domain-doc.md](./templates/domain-doc.md) | New domain page at `.wbdocs/domains/<domain-name>.md` |
| [templates/features-index.md](./templates/features-index.md) | Features folder index at `.wbdocs/features/index.md` |
| [templates/feature-doc.md](./templates/feature-doc.md) | New feature page at `.wbdocs/features/<feature-name>.md` |
| [templates/database-index.md](./templates/database-index.md) | Database index at `.wbdocs/database/index.md` |
| [templates/database-store.md](./templates/database-store.md) | Per-store doc at `.wbdocs/database/<store-name>.md` — schema, migrations, backup, security |
| [templates/frontend-index.md](./templates/frontend-index.md) | Frontend standards at `.wbdocs/frontend/index.md` — stack, tokens, theme, layout, component patterns |
