# Feature Documentation

Use this folder for detailed technical docs below the domain level. A feature doc should be created when an area has enough behavior, data flow, integration, or operational risk that future agents need more than a one-paragraph domain summary.

When creating a new feature doc, copy `.wbrules/templates/feature-doc.md` to `.wbdocs/features/<feature-name>.md` and fill every section. Link to it from the relevant domain page in `.wbdocs/domains/<domain-name>.md`.

## Maintenance Rules

- Keep feature docs current when behavior, data contracts, configuration, or validation changes.
- Do not paste large code blocks or changelogs; link to source files and describe stable contracts.
- Record known edge cases and failure handling.
- Document tests and validation commands that prove the feature still works.
