# wb-ai-rules

A generic, reusable set of AI agent working rules that can be attached to any project.

---

## Folder structure

```
.wbrules/    ← Generic agent rules (this repo). Never add project-specific content here.
.wbdocs/     ← Project-specific documentation. Created per project, lives beside .wbrules/.
```

## How to use

1. Copy or symlink `.wbrules/` into any project repository.
2. Create a `.wbdocs/` folder in that project for all project-specific docs.
3. Configure your agent to load `.wbrules/README.md` as its entry point.

## Rules directory

See [.wbrules/README.md](./.wbrules/README.md) for the full loading convention and file index.
