# Database Rules

Load this file before starting any task that touches a data store, schema, migration, or data-correctness change — including questions about the database.

> **Docs protocol:** See `pre-0-documentation-first.md`. For this area, read `.wbdocs/database/index.md` and `.wbdocs/database/<store-name>.md` before starting. If you discover a new store or table with no doc, create it before proceeding.


## Documentation

- Create a child doc (`.wbdocs/database/<store-name>.md`) for each real data store used by the project.
- Document migrations and schema changes **before or during** implementation — not after the details are forgotten.
- Record safe local defaults (e.g., `localhost`, dev credentials) separately from production or shared-environment configuration.
- Never store credentials, secret connection strings, or production tokens in any documentation file.
- Include backup, restore, rollback, and data-retention notes for every critical store.

## Data correctness

- For changes that affect data correctness, include a validation step that compares old vs new data paths, or cached vs rebuilt results, when relevant.
- Treat data-correctness changes with the same rigor as security changes: validate before and after, not only in tests.
