# <STORE_NAME>

> **Type:** `<e.g. PostgreSQL 15, Redis 7, MongoDB 7, S3-compatible>`
> **Owned by domain:** `<domain-name>`
> **Used by:** `<list of domains or services that read/write this store>`

---

## Purpose

`<What data this store holds and why it exists. One paragraph.>`

---

## Connection and Configuration

| Setting | Local default | Notes |
|---|---|---|
| Host | `localhost` | |
| Port | `<e.g. 5432>` | |
| Database / Bucket name | `<e.g. myapp_dev>` | |
| Auth mechanism | `<e.g. password, IAM role>` | |

> **Never document real credentials, production connection strings, or secret values here.**
> Store secrets in your secrets manager or `.env` (gitignored). Reference the key name only (e.g. `DATABASE_URL`).

---

## Schema

### Tables / Collections / Keys

#### `<table_or_collection_name>`

| Column / Field | Type | Nullable | Default | Description |
|---|---|---|---|---|
| `id` | `<e.g. uuid>` | No | `gen_random_uuid()` | Primary key |
| `<field>` | `<type>` | `<yes/no>` | `<default or —>` | `<description>` |

**Indexes:**
- `<index_name>` on `(<columns>)` — `<reason for index>`

**Constraints:**
- `<constraint description>`

**Relationships:**
- `<table>.<column>` → `<other_table>.<column>` (`<cascade behavior>`)

*(Repeat this block for each table / collection / key namespace.)*

---

## Migrations

| Migration | Date | Description |
|---|---|---|
| `<migration file or ID>` | `<YYYY-MM-DD>` | `<what it changed>` |

**Migration rules:**
- Document new migrations here before or during implementation — not after.
- Include rollback steps for any destructive migration.
- Mark irreversible migrations explicitly.

---

## Access Patterns

| Operation | Who calls it | Query / Command | Notes |
|---|---|---|---|
| `<e.g. Find user by email>` | `<service/module>` | `<e.g. SELECT * FROM users WHERE email = $1>` | `<any index or performance note>` |

---

## Data Retention and Lifecycle

| Data type | Retention policy | Deletion mechanism |
|---|---|---|
| `<e.g. audit logs>` | `<e.g. 90 days>` | `<e.g. scheduled job>` |

---

## Backup and Restore

| Concern | Detail |
|---|---|
| Backup frequency | `<e.g. daily at 02:00 UTC>` |
| Backup location | `<e.g. S3 bucket name pattern — no credentials>` |
| Restore procedure | `<step-by-step or link to runbook>` |
| Estimated RTO | `<Recovery Time Objective>` |
| Estimated RPO | `<Recovery Point Objective>` |

---

## Rollback Notes

`<Describe how to roll back schema changes or bad data migrations. Include any manual steps required.>`

---

## Operational Notes

`<Known quirks, performance characteristics, connection pool settings, replication lag considerations, or anything else future agents need to know.>`

---

## Security

| Concern | Detail |
|---|---|
| Encryption at rest | `<yes/no + mechanism>` |
| Encryption in transit | `<yes/no + mechanism>` |
| Access control | `<who/what has read and write access>` |
| Sensitive fields | `<list any PII or sensitive columns and how they are protected>` |
| Audit logging | `<yes/no — what is logged>` |
