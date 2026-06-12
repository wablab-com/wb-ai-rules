# Agent Working Checklist

## Rule

During every task, the agent **MUST** maintain and report the status of the checklist below:
- In **every progress update** shared with the user during the task.
- In the **final completion message** when the task is closed.

Status icons:
- `⏳` pending or in progress
- `✅` completed
- `➖` not applicable

---

## Checklist

### 📖 Pre-task — Documentation Reading
> Rule source: `pre-0-documentation-first.md`

| # | Item | Status |
|---|---|---|
| 1 | Read `.wbdocs/index.md` | ⏳ |
| 2 | Read relevant domain doc(s) at `.wbdocs/domains/` | ⏳ |
| 3 | Read relevant feature doc(s) at `.wbdocs/features/` | ⏳ |
| 4 | Read relevant database store doc(s) at `.wbdocs/database/` | ⏳ |
| 5 | Read `.wbdocs/frontend/index.md` (UI tasks only) | ➖ |

---

### 🔍 Pre-task — Discovery
> Rule source: `pre-0-documentation-first.md`

| # | Item | Status |
|---|---|---|
| 6 | Identified all domains, features, stores, tables, and integrations touched by this task | ⏳ |
| 7 | Created doc(s) for any undocumented area using the correct template before proceeding | ➖ |
| 8 | Registered every new doc in its relevant index file | ➖ |

---

### 🧠 During — Core Principles
> Rule source: `pre-1-core-principles.md`

| # | Item | Status |
|---|---|---|
| 9 | Changes are small and behavior-stable unless explicitly requested otherwise | ⏳ |
| 10 | Correctness, clarity, and maintainability prioritised over cleverness | ⏳ |
| 11 | Domain and existing code paths understood before changing behavior | ⏳ |
| 12 | User-visible correctness, safety, security, and operability treated as first-class requirements | ⏳ |

---

### 🏗️ During — Code Structure
> Rule source: `pre-2-code-structure.md`

| # | Item | Status |
|---|---|---|
| 13 | Methods and classes are focused and single-purpose; large logic split into well-named helpers | ⏳ |
| 14 | Meaningful names used; coupling minimised | ⏳ |
| 15 | Existing architecture, libraries, DI patterns, error handling, and test style followed | ⏳ |
| 16 | Controllers, handlers, commands, and UI callbacks kept thin; business logic placed in services | ⏳ |
| 17 | No broad refactor introduced unless necessary for the change or explicitly approved | ⏳ |

---

### 🔒 During — Safety and Security
> Rule source: `pre-3-safety-and-design.md`

| # | Item | Status |
|---|---|---|
| 18 | No secrets, credentials, private keys, production tokens, or machine paths committed | ⏳ |
| 19 | No large dependencies added without explicit approval | ⏳ |
| 20 | Errors fail fast with explicit, meaningful messages — no silent swallowing of exceptions | ⏳ |
| 21 | Inputs validated and guarded against XSS, CSRF/session riding, session hijacking, SQL injection, directory traversal, and data exposure | ⏳ |
| 22 | No tests removed to make CI pass | ⏳ |
| 23 | Unrelated user worktree changes preserved and not reverted | ⏳ |

---

### 🗄️ During — Database
> Rule source: `pre-5-database-rules.md` — mark `➖` if no database work

| # | Item | Status |
|---|---|---|
| 24 | `.wbdocs/database/index.md` and relevant store doc read before starting | ➖ |
| 25 | Store doc created at `.wbdocs/database/<store-name>.md` if it did not exist | ➖ |
| 26 | Migrations and schema changes documented before or during implementation | ➖ |
| 27 | Safe local defaults recorded separately from production config; no credentials in docs | ➖ |
| 28 | Backup, restore, rollback, and data-retention notes included or confirmed current | ➖ |
| 29 | Data-correctness changes include a before/after validation step | ➖ |

---

### 🔌 During — API Building
> Rule source: `pre-6-api-building.md` — mark `➖` if not building or modifying an API

| # | Item | Status |
|---|---|---|
| 30 | Project's established API style followed consistently (REST / GraphQL / RPC — no mixing) | ➖ |
| 31 | Request and response schemas defined before implementation | ➖ |
| 32 | Every new or changed endpoint documented in `.wbdocs/features/<feature>.md` | ➖ |
| 33 | Breaking vs non-breaking changes explicitly labelled | ➖ |
| 34 | Correct HTTP methods and status codes used; no `200` with error body | ➖ |
| 35 | Consistent error response shape returned across all endpoints | ➖ |
| 36 | Auth and authorisation applied to every non-public endpoint | ➖ |
| 37 | Inputs validated server-side; no sensitive details in error responses | ➖ |
| 38 | Rate limiting applied to public-facing endpoints | ➖ |
| 39 | HTTPS enforced in all non-local environments; explicit CORS policy set | ➖ |
| 40 | API test suite run and result reported | ➖ |

---

### 🌐 During — API Integration
> Rule source: `pre-7-api-integration.md` — mark `➖` if not consuming an external API

| # | Item | Status |
|---|---|---|
| 41 | Relevant integration feature doc at `.wbdocs/features/<integration>.md` read before starting | ➖ |
| 42 | Explicit timeout set on every outbound HTTP call | ➖ |
| 43 | Retry logic with exponential backoff and jitter implemented for transient failures | ➖ |
| 44 | Partial failures handled explicitly; fallback behavior defined and documented | ➖ |
| 45 | All credentials stored in env vars or secrets manager — never hardcoded | ➖ |
| 46 | External data validated and sanitised before use | ➖ |
| 47 | No sensitive payloads, tokens, or PII logged | ➖ |
| 48 | Integration documented in `.wbdocs/features/<integration>.md` (endpoints, versions, failure modes) | ➖ |
| 49 | External APIs mocked in unit tests; failure scenarios tested explicitly | ➖ |

---

### 🖥️ During — Frontend and UI
> Rule source: `pre-8-frontend-rules.md` — mark `➖` if no UI work

| # | Item | Status |
|---|---|---|
| 50 | `.wbdocs/frontend/index.md` read before writing any component, screen, or style (**MUST MUST MUST** read before starting) | ➖ |
| 51 | No new UI framework, component library, icon set, or styling system introduced without approval | ➖ |
| 52 | Established design tokens, library colors, and layouts followed — no hardcoded colors or custom layouts deviating from the standard | ➖ |
| 53 | Existing component patterns and partials used — **relied on partials as much as possible** and no parallel version of an existing component created | ➖ |
| 54 | Established layout structure, grid, and theme followed — no different theme on new screens | ➖ |
| 55 | Loading, error, and empty states handled for every data-dependent UI surface | ➖ |
| 56 | Business logic kept out of components — placed in services or view models | ➖ |
| 57 | Semantic HTML used; heading hierarchy correct; all inputs labelled (web) | ➖ |
| 58 | WCAG 2.1 AA accessibility minimum met; automated a11y tool run | ➖ |
| 59 | Touch targets meet minimum size requirements (mobile: 44×44 pt iOS / 48×48 dp Android) | ➖ |
| 60 | No secrets or credentials embedded in client-side code or bundled assets | ➖ |

---

### ⚡ During — Performance
> Rule source: `pre-9-performance-rules.md` — mark `➖` if no database design, query changes, or complex code paths

| # | Item | Status |
|---|---|---|
| 61 | Indexes created or verified for all search filters, foreign keys, and sorting fields in affected schemas | ⏳ |
| 62 | Database queries profiled (e.g. using `EXPLAIN`) and optimized to avoid N+1 issues and full table scans | ⏳ |
| 63 | Large datasets batched, paginated, or streamed to prevent high memory consumption | ⏳ |
| 64 | Algorithmic complexity minimized, and caching applied to computationally expensive hot paths | ⏳ |

---

### 🔍 During — Search Engine Optimisation (SEO)
> Rule source: `pre-10-seo-rules.md` — mark `➖` if no web frontend or public-facing route changes

| # | Item | Status |
|---|---|---|
| 65 | Descriptive title tag and compelling meta description set for every public web page | ⏳ |
| 66 | Strict heading hierarchy starting with a single H1 and semantic HTML structure implemented | ⏳ |
| 67 | Canonical tags, robots directives, and schema markup (JSON-LD) configured correctly | ⏳ |
| 68 | All links use descriptive anchor text and all images have descriptive alt attributes | ⏳ |

---

### 🧪 Post-task — Tests
> Rule source: `post-0-tests.md`

| # | Item | Status |
|---|---|---|
| 69 | Tests added or updated for every behavior change | ⏳ |
| 70 | Regression test added for any bug fixed (when reliably capturable) | ➖ |
| 71 | Failing tests fixed before closing — or user has explicitly accepted a known unrelated failure | ⏳ |
| 72 | Fast unit tests used for isolated logic; integration/E2E used for critical flows | ⏳ |
| 73 | Relevant test suite or build validation run — result reported | ⏳ |
| 74 | All edge cases, input validation failures, boundary conditions, error paths, and happy paths identified and tested with unit tests | ⏳ |
| 75 | Database-interacting tests strictly configured to use a dedicated, isolated test database to prevent damage to the main database | ⏳ |
| 76 | Tests kept independent and isolated by mocking/stubbing external APIs, side-effects, and dependencies | ⏳ |
| 77 | Separate, dedicated unit or integration tests written to explicitly cover security controls and vulnerability vectors (XSS, CSRF, session hijacking/riding, SQL injection, directory traversal) | ⏳ |

---

### 🧹 Post-task — Build Hygiene
> Rule source: `post-1-build-hygiene.md`

| # | Item | Status |
|---|---|---|
| 78 | At least one existing build warning fixed (when practical and not explicitly scoped out) | ⏳ |
| 79 | No warnings hidden or diagnostics weakened | ⏳ |
| 80 | Generated outputs, caches, and local artifacts excluded from source control | ⏳ |

---

### 📝 Post-task — Documentation Updates
> Rule source: `post-2-update-documentation.md`

| # | Item | Status |
|---|---|---|
| 81 | All affected `.wbdocs/` pages updated | ⏳ |
| 82 | Any fact or knowledge gained (even from a question) written into the relevant doc immediately | ⏳ |
| 83 | Newly discovered domain/feature/store/table/integration doc created using correct template | ➖ |
| 84 | New doc registered in its index file (domains, database, or frontend index) | ➖ |
| 85 | `.wbdocs/domains/index.md` consistent with the current domain list | ⏳ |
| 86 | Database store doc updated — schema, migrations, backup/restore notes current | ➖ |
| 87 | Frontend standards doc updated — new libs, colors, layouts, tokens, or component patterns recorded (**MUST MUST MUST** update after any change) | ➖ |
| 88 | No project-specific content added to `.wbrules/` | ✅ |

---

## How to report

Copy and paste the relevant sections into your progress update or final completion message, updating each status icon. Example format:

```
## Task complete — <short title>

<summary of what was done>

### Checklist
| # | Item | Status |
|---|---|---|
| 1 | Read `.wbdocs/index.md` | ✅ |
| 2 | Read relevant domain doc(s) | ✅ |
| 3 | Read relevant feature doc(s) | ✅ |
...
```

If any item remains `⏳` in the final message, explain why it is still pending or blocked.
