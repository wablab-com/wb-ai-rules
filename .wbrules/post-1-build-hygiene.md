# Build Hygiene

Run this checklist after completing any code change.

- When touching code, fix at least one existing build warning when practical unless the user explicitly scopes the work differently.
- Do not hide warnings by weakening diagnostics unless the warning is proven invalid and the change is documented.
- Keep generated outputs, caches, and local artifacts out of source control unless the project explicitly tracks them.
