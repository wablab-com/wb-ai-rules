# Safety and Design Rules

- Do not remove tests to pass CI.
- Do not add large dependencies without approval.
- Fail fast with explicit, meaningful errors; do not swallow exceptions silently.
- Treat security as correctness. Validate inputs and guard against injection, path traversal, authorization, authentication, secret handling, and data exposure risks.
- Do not commit secrets, credentials, private keys, production tokens, personal machine paths, or private operational data.
- Preserve user changes in the worktree. Do not revert unrelated modified files unless the user explicitly asks.
