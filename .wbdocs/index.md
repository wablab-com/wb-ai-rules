# wb-ai-rules Documentation

This repository maintains reusable agent rules in `.wbrules/` and project documentation templates used by agents. Agents must read this index first, then `.wbdocs/environment.md`, then the relevant domain docs before changing rules, templates, or repository guidance.

## Loading Order

1. Read `.wbdocs/environment.md` to identify the current environment and safety policy.
2. Read `.wbdocs/domains/index.md` to select the relevant domain.
3. Read `.wbdocs/domains/agent-rules.md` before changing `.wbrules/`, templates, agent instructions, or checklist behavior.

## Documentation Boundaries

- Generic reusable rules, checklists, and templates live in `.wbrules/`.
- Repository-specific documentation about this rules project lives in `.wbdocs/`.
- Keep high-level index pages concise and update affected docs after every task when something is changed, learned, clarified, or discovered.
