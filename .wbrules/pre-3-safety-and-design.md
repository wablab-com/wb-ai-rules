# Safety and Design Rules

- Do not remove tests to pass CI.
- Do not add large dependencies without approval.
- Fail fast with explicit, meaningful errors; do not swallow exceptions silently.
- Treat security as correctness. The agent must make sure that all written code is secure and free of vulnerabilities, covering:
  - Cross-Site Scripting (XSS): Ensure proper output encoding, context-aware escaping, and Content Security Policy compliance.
  - Cross-Site Request Forgery (CSRF) & Session Riding: Implement state-changing request protection via anti-CSRF tokens and SameSite cookie attributes.
  - Session Hijacking: Secure cookie flags (Secure, HttpOnly, SameSite), session rotation upon authentication state changes, and session/token validation.
  - SQL Injection: Always use parameterized queries, prepared statements, or an ORM; never concatenate untrusted inputs into database queries.
  - Directory Traversal (Path Injection): Validate, sanitize, and canonicalize all file paths; restrict file access to predefined safe directories.
- Write dedicated, separate security unit tests that explicitly cover security checks and test vulnerabilities (e.g., verifying XSS filters, anti-CSRF token verification, session guards, SQL injection rejection, and directory traversal blocks).
- Do not commit secrets, credentials, private keys, production tokens, personal machine paths, or private operational data.
- Preserve user changes in the worktree. Do not revert unrelated modified files unless the user explicitly asks.
