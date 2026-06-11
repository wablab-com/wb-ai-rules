# Tests

Run this checklist after completing any code change.

- Add or update tests for every behavior change made.
- Add regression tests for bugs when the bug can be captured reliably.
- Fix failing tests before considering the task done, unless the user explicitly accepts a known unrelated failure.
- Prefer fast unit tests for isolated logic and integration/end-to-end checks for critical flows.
- Run the relevant tests or build validation after changes and report the result.
- Comprehensive Coverage & Edge Cases: Identify and test all edge cases, input validation failures, boundary conditions, error-handling paths, and happy paths. Write unit tests that cover these scenarios comprehensively.
- Database Isolation: Ensure database-interacting tests are strictly configured to use a dedicated, isolated test database. Verify the connection configuration to prevent accidental modification, truncation, or damage to the main database.
- Test Independence: Keep tests independent and isolated. Mock or stub external APIs, side-effects, and external dependencies to prevent flaky behavior and shared mutable state.
- Security Testing: Write separate, dedicated unit or integration tests that specifically target security vulnerabilities (e.g. testing input validation, XSS escaping, anti-CSRF measures, authentication/session guards, SQL injection prevention, and directory traversal blocks).
