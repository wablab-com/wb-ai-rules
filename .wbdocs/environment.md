# Environment Registry

This file maps safe runtime fingerprints to the environment type agents must use before starting any task.

## Mandatory Startup Rule

Agents must read this file immediately after `.wbdocs/index.md` and before reading domain, feature, database, or frontend docs. If the current host or runtime is not registered here, or if hostname alone does not identify it confidently, the agent must stop, ask the user whether the environment is `production`, `staging`, `dev`, `local`, or `test`, then update this file before continuing.

## Environment Types

| Type | Meaning | Default Safety Policy |
|---|---|---|
| `production` | Live users, live data, live credentials, or live infrastructure may be affected. | Read-only by default. No automated tests, seeders, fixtures, migrations, destructive scripts, or data writes without explicit task-specific approval and documented rollback expectations. |
| `staging` | Production-like validation environment with non-production risk boundaries. | Automated tests may run only when they target staging-safe resources and do not mutate protected data. |
| `dev` | Shared development environment. | Automated tests may run when isolated from shared data and external side effects. |
| `local` | Developer workstation or local container. | Documentation validation and non-destructive file inspection may run. Automated tests may run only when configured for local/test resources. |
| `test` | Dedicated automated test environment. | Automated tests may run when isolated from production and external side effects. |

## Known Environments

Record only safe identifiers. Do not store secrets, credentials, tokens, private keys, DSNs, or sensitive operational payloads. Hostname alone is often not enough; record enough independent safe fingerprints to distinguish similarly named hosts, containers, or cloned machines.

| Name | Type | Safe Fingerprints | Test Policy | Data/Credential Risk | Notes |
|---|---|---|---|---|---|
| Local rules workspace | `local` | `hostname=ahmadfds`, `machine-id-sha256=9ee036a2682154ee04476c8debe9be7b4f159c643731da5ee2f5969630859517` | Documentation validation and read-only Git/file inspection are allowed. No database or external-service tests are expected for this repository. | No application runtime data store is documented for this rules repository. Do not record secrets or personal operational payloads. | Classified from the local unrestricted workspace context for this repository. |

## Local Tooling Notes

- Git commit and push are available through plain Git in the local rules workspace.
- GitHub CLI (`gh`) is not installed in the local rules workspace as of the latest publish check; use plain Git for commit/push tasks unless `gh` is installed later.

## Fingerprint Guidance

- Prefer safe, non-secret identifiers such as hostname, container name, deployment name, cloud project alias, or hashed machine/MAC identifiers.
- Use two or more independent fingerprints for production, staging, shared dev, and any environment that can affect shared data. A hostname-only match is acceptable only when this file explicitly documents that the hostname is unique and stable.
- Hash or redact identifiers when they reveal private infrastructure details.
- Never include passwords, tokens, API keys, database URLs, private IP ranges that are sensitive, or personal machine paths.
- When fingerprints conflict or the current environment is ambiguous, ask the user before proceeding.

## Production Guardrails

- Do not run unit tests, automated tests, integration tests, end-to-end tests, seeders, fixture loaders, destructive scripts, migrations, schema changes, or database-interacting tests on production without explicit task-specific approval.
- Prefer read-only inspection on production.
- Treat data, databases, credentials, backups, queues, caches, logs, and external services as critical.
- Before risky production work, document the intended change, expected impact, backup/restore state, rollback path, and approval.
