# Agent Rules

This domain documents the reusable agent rules and templates maintained in this repository. Keep this page at the domain level: one concise paragraph per feature or subsystem, with details remaining in the rule files themselves.

## Documentation-First Protocol

The documentation-first protocol owns mandatory reading of `.wbdocs/index.md`, `.wbdocs/environment.md`, relevant domain docs, and affected `.wbdocs/` pages before tasks, plus mandatory documentation updates after every task when anything is changed, learned, clarified, or discovered. Its source files include `.wbrules/pre-0-documentation-first.md`, `.wbrules/pre-4-documentation-contract.md`, `.wbrules/post-2-update-documentation.md`, and the relevant templates under `.wbrules/templates/`.

## Agent Working Checklist

The agent working checklist in `.wbrules/index.md` is a milestone source checklist. Agents must understand the task first, select only applicable checklist items for the task, use that scoped sub-checklist internally while working, and print the completed scoped checklist once in the final response. Its milestone groups distinguish startup, scoping, discovery gates, work, validation, and closeout; missing-documentation items are discovery gates that may trigger during scoping, investigation, or implementation and must be satisfied before proceeding in the affected area. Progress updates should describe current work and blockers without repeatedly printing checklist tables. Documentation-update items remain mandatory for every task, including questions, whenever anything is changed, learned, clarified, or discovered.

## Rule Catalog

The rule catalog in `.wbrules/README.md` explains loading order and maps rule files by phase. Keep it generic, synchronized with `.wbrules/index.md`, and free of application-specific project details.
