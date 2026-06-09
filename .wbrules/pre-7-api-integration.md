# API Integration Rules

Load this file before starting any task that involves calling, consuming, or depending on an external or internal API — including questions about how an integration works.

> **Docs protocol:** See `pre-0-documentation-first.md`. For this area, read `.wbdocs/features/<integration-name>.md` before starting. If you discover an undocumented external service or integration, create its feature doc before proceeding.


## Reliability

- Set an explicit timeout on every outbound HTTP call. Never rely on the default or no timeout.
- Implement retry logic with exponential backoff and jitter for transient failures (network errors, `429`, `503`).
- Handle partial failures explicitly — do not assume a successful HTTP response means the payload is valid or complete.
- Define and document the fallback behavior when the external service is unavailable or degraded.
- Treat every external call as a potential point of failure. Fail fast and surface errors clearly rather than silently degrading.

## Security

- Store all API keys, tokens, and credentials in environment variables or a secrets manager. Never hardcode them.
- Never commit credentials, tokens, or secret values to source control or documentation.
- Validate and sanitize all data received from external APIs before using it — treat external input as untrusted.
- Never log full request or response bodies if they may contain API keys, tokens, PII, or sensitive user data.
- Rotate credentials on suspected exposure immediately and revoke the compromised values.

## Contracts and Documentation

- Document the external service, the specific endpoints consumed, and the data flowing in and out in `.wbdocs/features/<feature-name>.md`.
- Record the API version, contract version, or SDK version being relied upon.
- Document known failure modes and how the system handles each (retry, fallback, alert, fail open/closed).
- When the external API changes, update the feature doc and review all callers before closing the task.

## Error Handling

- Map external error codes to internal domain errors. Do not leak raw third-party error messages to end users.
- Log external failures with enough context (endpoint, status code, correlation ID) to debug, without logging sensitive payloads.
- Alert or surface errors at an appropriate severity level — silent swallowing of integration failures is not acceptable.

## Testing

- Mock or stub external APIs in all unit tests. Never call real external services in unit tests.
- Use contract tests or a sandboxed integration environment for critical integrations.
- Test failure scenarios explicitly: timeouts, `4xx` responses, `5xx` responses, malformed payloads, and empty responses.
- Document the test command or environment setup needed to run integration tests against the real service.
