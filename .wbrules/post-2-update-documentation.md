# Update Documentation

## ⚠️ This checklist is MANDATORY after every task — including questions

Do not close any task until this checklist is complete.

- **Every task** — code change, bug fix, refactor, investigation, or question — must end with a doc update if anything was learned, changed, clarified, or discovered.
- If a question revealed new information (an undocumented behavior, a constraint, a design decision, a gotcha) — write it into the relevant `.wbdocs/` file immediately.
- Do not defer doc updates. Deferring is the same as losing the information.
- If module responsibilities, public APIs, or major behavior changed, update the relevant `.wbdocs/` pages.
- If a new module or domain was introduced, create its doc page under `.wbdocs/domains/`.
- If an existing feature doc is now outdated, correct it before closing the task.
- Keep `.wbdocs/domains/index.md` consistent with the current domain list.
- High-level index pages must remain concise — avoid appending changelogs or verbose history.
- Never add project-specific content to `.wbrules/`. All project documentation belongs in `.wbdocs/`.

## Newly discovered areas

If the task revealed any domain, feature, database store, table, external integration, or UI pattern that has no doc yet:

| Discovered | Action |
|---|---|
| New domain | Create `.wbdocs/domains/<domain-name>.md` using `templates/domain-doc.md`. Add entry to `.wbdocs/domains/index.md`. |
| New feature or subsystem | Create `.wbdocs/features/<feature-name>.md` using `templates/feature-doc.md`. Link from the domain page. |
| New database store | Create `.wbdocs/database/<store-name>.md`. Add entry to `.wbdocs/database/index.md`. |
| New database table | Add a schema entry to the relevant `.wbdocs/database/<store-name>.md`. |
| New external integration | Create `.wbdocs/features/<integration-name>.md` using `templates/feature-doc.md`. |
| New UI component pattern | Add it to the component patterns section of `.wbdocs/frontend/index.md`. |

Do not close the task until every newly discovered area has a doc and is registered in its index.



## Database changes

If the task touched a data store, schema, or migration:

- Create or update the child doc for the affected store at `.wbdocs/database/<store-name>.md`.
- Confirm that any new migration or schema change is recorded in the store's doc.
- Verify that backup, restore, rollback, and data-retention notes are still accurate.
- Confirm no credentials, connection strings, or production tokens were added to any doc file.

## Frontend and UI changes

If the task touched any UI, component, screen, or client-side code:

- If `.wbdocs/frontend/index.md` does not exist, create it using `.wbrules/templates/frontend-index.md` now.
- If a new library, plugin, or tool was introduced (with approval), add it to the stack section of `.wbdocs/frontend/index.md`.
- If a new design token (color, spacing, typography, shadow) was defined, add it to the tokens section.
- If a new component pattern (button variant, modal type, form layout, etc.) was introduced, document it in the component patterns section.
- If the layout structure, routing strategy, or state management approach changed, update the relevant section.
- If a new UI feature with non-trivial flows or integration was added, create `.wbdocs/features/<feature-name>.md`.
- Confirm that no hardcoded values (raw hex colors, magic spacing numbers, font names) were introduced that should be tokens.
