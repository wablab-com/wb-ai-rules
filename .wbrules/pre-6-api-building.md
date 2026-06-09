# API Building Rules

Load this file before starting any task that involves designing, implementing, or modifying an API endpoint — including questions about the API contract.

> **Docs protocol:** See `pre-0-documentation-first.md`. For this area, read the relevant feature doc at `.wbdocs/features/<feature-name>.md` and the domain doc before starting. If you discover an undocumented endpoint or a new API feature, create its doc before proceeding.


## Design

- Follow the project's established API style (REST, GraphQL, RPC) consistently — do not mix conventions.
- Use plural nouns for REST resource paths (`/users`, not `/user`). Use kebab-case for multi-word segments.
- Version APIs from day one (`/api/v1/`). Never introduce a breaking change to an existing versioned route.
- Prefer additive changes (new fields, new endpoints) over mutations to existing contracts.
- Deprecate before removing: mark deprecated endpoints explicitly and document the removal timeline.

## Contracts

- Define request and response schemas before implementation, not after.
- Document every endpoint in the relevant feature doc (`.wbdocs/features/<feature-name>.md`) before or during implementation.
- Treat the documented schema as the source of truth. If the implementation diverges, update the doc — not the other way around.
- Explicitly label which changes are breaking vs non-breaking when modifying existing endpoints.

## HTTP Semantics

- Use HTTP methods correctly: `GET` for reads (idempotent, no side effects), `POST` for creates, `PUT`/`PATCH` for updates, `DELETE` for deletes.
- Return correct HTTP status codes: `2xx` for success, `4xx` for client errors, `5xx` for server errors.
- Never return `200 OK` with an error payload. Never return `500` for a client mistake.
- Return consistent error response shapes across all endpoints (e.g., `{ error: { code, message, details } }`).

## Security

- Authenticate and authorize every non-public endpoint — never rely on obscurity or route structure.
- Validate and sanitize all inputs server-side, regardless of client-side validation.
- Never expose internal IDs, stack traces, file paths, or sensitive system details in error responses.
- Apply rate limiting to all public-facing endpoints.
- Enforce HTTPS in all non-local environments. Never allow plaintext in production.
- Set explicit CORS policies. Do not use wildcard origins (`*`) in production.

## Error Handling

- Return structured, consistent error bodies for all failure cases.
- Log server-side errors with enough context to debug, but never log request bodies that may contain secrets or PII.
- Fail fast and return a clear error rather than returning a partial or silently degraded response.

## Testing

- Write tests that cover the happy path, validation errors, auth failures, and edge cases for every endpoint.
- Test contract shape (status code + response structure), not just business logic.
- Run the API test suite and report the result before considering the task done.
