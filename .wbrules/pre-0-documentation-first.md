# Documentation First

Documentation is the **single most important practice** in this framework.

Code without current documentation is a liability. An agent that changes code without reading or updating docs is worse than no agent at all — it leaves the system in an unknown state that future agents cannot safely reason about.

**This rule has no exceptions.** It applies to every task type: implementation, debugging, refactoring, investigation, and questions.

---

## Before starting any task

1. **Read `.wbdocs/index.md` first.** Always. Without exception.
2. **Read `.wbdocs/environment.md` next.** Always. Without exception.
3. Identify the current runtime environment from `.wbdocs/environment.md` before doing anything else:
   - Match the current environment using enough safe fingerprints to be confident. Hostname alone is often not enough; use MAC address, machine-id, container ID, cloud/deployment identifier, or another safe fingerprint when available.
   - If the current hostname plus the required supporting fingerprint(s) are listed, follow the documented environment type and safety policy.
   - If the current environment is not registered, stop and ask the user to classify it as `production`, `staging`, `dev`, `local`, or `test`.
   - After the user answers, update `.wbdocs/environment.md` with the environment type, safe non-secret host fingerprints, and required safety notes before continuing.
4. Follow `.wbdocs/index.md` loading order to identify which domain, feature, database, and frontend docs apply to the current task.
5. Read every relevant doc in full before writing code, answering a question, or forming any conclusion.
6. If a required doc does not exist, create it using the appropriate template from `.wbrules/templates/` before proceeding. Do not work in an undocumented area.

> Skipping this step and relying on memory or guesswork is a failure mode. Docs exist precisely because memory and context are unreliable across tasks and agents.

## Environment safety

Agents must know which environment they are operating in before starting any task. The environment doc is a safety gate, not a passive note.

- `production` means real users, real data, real credentials, or live infrastructure may be affected.
- Agents must not run unit tests, automated tests, integration tests, end-to-end tests, seeders, destructive commands, migrations, schema changes, data cleanup scripts, or fixture loaders against production unless the user gives explicit, task-specific approval and the command is documented as production-safe.
- On production, treat data, databases, credentials, backups, queues, caches, logs, and external services as critical. Prefer read-only inspection, require explicit approval for writes, and document backup/rollback expectations before risky work.
- Environment docs must record only safe identifiers and operational notes. Do not store secrets, credentials, tokens, private keys, production DSNs, or sensitive operational payloads.
- Hostname is only a hint unless the environment doc explicitly says it is unique. Prefer two or more independent safe fingerprints for production, staging, shared dev, and any host that can affect shared data.
- If environment identity is ambiguous or contradictory, stop and ask the user before proceeding.

---

## After finishing any task

1. **Update every doc that is now stale, incomplete, or missing information.**
2. This applies even when no code changed. If a question, investigation, or discussion revealed:
   - an undocumented behavior
   - a design decision or constraint
   - a gotcha, edge case, or failure mode
   - a clarification of something previously vague

   → **Write it into the relevant `.wbdocs/` file immediately.**

3. Do not defer. A doc update deferred is a doc update lost.
4. **A task is not complete until the docs reflect the current state of the system.**

---

## Discovering new areas

During any task you may encounter something that has no doc yet: a domain boundary you didn't know existed, a feature you're seeing for the first time, a database table or store that isn't documented, an external integration with no feature doc, or a UI pattern not recorded in the frontend standards.

**When this happens:**

1. **Stop and create the doc before proceeding.** Do not work in an undocumented area.
2. Use the correct template from `.wbrules/templates/`:

   | Discovered | Template to use | Create at |
   |---|---|---|
   | Environment registry | `templates/environment-doc.md` | `.wbdocs/environment.md` |
   | New domain | `templates/domain-doc.md` | `.wbdocs/domains/<domain-name>.md` |
   | New feature or subsystem | `templates/feature-doc.md` | `.wbdocs/features/<feature-name>.md` |
   | New database store | `templates/database-store.md` | `.wbdocs/database/<store-name>.md` |
   | New database table | *(add to the store doc using its schema section)* | `.wbdocs/database/<store-name>.md` |
   | New external integration | `templates/feature-doc.md` | `.wbdocs/features/<integration-name>.md` |
   | New UI component pattern | *(add to frontend standards)* | `.wbdocs/frontend/index.md` |

3. Add an entry to the relevant index (`.wbdocs/domains/index.md`, `.wbdocs/database/index.md`, or `.wbdocs/frontend/index.md`) so the new doc is discoverable.
4. Keep the new doc current from the moment it is created — it is your responsibility.

> Discovering something undocumented is not a reason to skip documentation. It is the strongest reason to create it immediately.

---

## Why this is non-negotiable

- Agents operate across sessions with no shared memory. Docs are the only persistent knowledge.
- An undocumented decision will be re-made — often differently — by the next agent or the next session.
- Inconsistent documentation leads to inconsistent systems: different API contracts, mismatched schemas, conflicting component patterns.
- Reading docs before acting prevents duplicated effort, broken integrations, and overwritten work.

---

## The documentation chain

Every area of the system has a doc. Agents must follow this chain:

```
.wbdocs/index.md                        ← always read first
├── .wbdocs/environment.md              ← always read second; identifies current environment and safety policy
└── .wbdocs/domains/index.md            ← domain map
    └── .wbdocs/domains/<domain>.md     ← domain detail
        └── .wbdocs/features/<feat>.md  ← feature detail
.wbdocs/database/index.md               ← read for any data store work
    └── .wbdocs/database/<store>.md     ← store detail
.wbdocs/frontend/index.md               ← read for any UI work
```

See `pre-4-documentation-contract.md` for the full documentation structure, templates, and three-layer model.

---

## Summary

| Phase | Action | Applies to |
|---|---|---|
| Before | Read `.wbdocs/index.md`, `.wbdocs/environment.md`, and relevant docs | Every task, every time |
| Before | Register unknown environment fingerprints after asking the user | Every task on an unregistered environment |
| Before | Create missing docs from templates if absent | Every task |
| During | If a new domain/feature/table/store/integration is discovered, create its doc immediately | Every task |
| During | Register the new doc in the relevant index file | Every task |
| After | Update all affected docs | Every task, including questions |
| After | Write newly learned facts into docs immediately | Every task |
| After | Do not close the task until docs are current | Every task |
