# <DOMAIN_NAME>

This file documents the `<DOMAIN_NAME>` domain. Keep this page at the domain level: one concise paragraph per feature or subsystem, with links to detailed feature docs under `.wbdocs/features/`.

## <FEATURE_OR_SUBSYSTEM_NAME>

`<FEATURE_OR_SUBSYSTEM_NAME>` owns `<PURPOSE_AND_PUBLIC_BEHAVIOR>`. It depends on `<DEPENDENCIES>`, exposes `<CONTRACTS_OR_ENTRY_POINTS>`, and must preserve `<RULES_CONSTRAINTS_OR_INVARIANTS>`. Agents must read `<DETAILED_FEATURE_DOC_PATH>` before changing this area and must update that doc after related changes.

## Maintenance Rules

- Keep each feature/subsystem entry to one paragraph.
- Put detailed flows, file maps, schemas, configuration, and tests in the linked feature docs.
- Document ownership boundaries explicitly so agents do not move behavior into the wrong layer.
- Remove example sections after real domain entries exist.
