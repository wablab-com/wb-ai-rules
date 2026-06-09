# Frontend and UI Rules

Load this file before starting any task that involves UI, views, components, screens, or client-side logic — regardless of platform (web, mobile, desktop).

---

## ⚠️ Standards Compliance — Read Before Writing Any UI

This section is mandatory. Violating it produces inconsistent UIs that break the established design system.

### Docs protocol

> See `pre-0-documentation-first.md` for the universal read/update protocol. For this area, read `.wbdocs/frontend/index.md` before starting. If it does not exist, create it using `.wbrules/templates/frontend-index.md` first. If you discover a new component pattern, library, or UI convention during the task, document it before finishing.


### Never introduce unapproved libraries or tools

- Do not add a new UI framework, component library, icon set, animation library, charting library, or styling system without explicit user approval.
- Do not add a new utility that duplicates something already in the approved stack.
- If an existing library does not cover a need, ask rather than silently introducing an alternative.

### Always use the established design system

- Use the project's documented design tokens: color palette, typography scale, spacing scale, border radii, shadows, and z-index layers. Never hardcode raw values that should come from tokens.
- Use the project's existing component patterns: buttons, modals, drawers, toasts, forms, tables, badges, and navigation elements. Never create a parallel version of an existing component.
- Use the project's documented layout structure: grid system, page shell, sidebar, header, and footer conventions.
- Match the project's established theme (dark/light mode, brand colors, font families). Never apply a different theme to a new screen.

### When standards need to change

- If the task genuinely requires a new component pattern or a change to an existing standard, document the decision in `.wbdocs/frontend/index.md` **before or during** implementation — not after.
- Updating the standard is allowed; ignoring it is not.

---

## All Platforms

### Architecture

- Keep UI components thin. Business logic belongs in services, view models, or domain modules — not in components, screens, or widgets.
- Keep components small and single-purpose. Split when a component grows beyond one clear responsibility.
- Separate presentational (dumb) components from container (smart) components. Presentational components must not call APIs or trigger side effects directly.
- Never hardcode user-facing strings inline. Use localization/i18n keys from the start, even if only one language is supported today.
- Handle loading, error, and empty states for every data-dependent UI surface. A component that only handles the happy path is incomplete.

### State Management

- Keep state as local as possible; lift only when two or more components genuinely need to share it.
- Separate UI state (loading spinners, error banners, form dirty flags) from domain/business state.
- Derive computed values rather than duplicating state. Duplicate state always diverges.
- Never store sensitive data — tokens, PII, session secrets — in unencrypted client-side storage without understanding the exposure risk.

### Accessibility

- Meet WCAG 2.1 AA as the minimum baseline. Accessibility is not optional.
- Every interactive element must be operable by keyboard and assistive technology.
- Respect system-level accessibility settings: reduced motion, high contrast, large text/dynamic type.
- Test with at least one automated accessibility tool (axe, Lighthouse, or equivalent) before considering UI work done.

### Performance

- Do not block the main or UI thread with heavy computation. Offload to background threads, workers, or async tasks.
- Measure before optimizing. Use profiling tools to identify actual bottlenecks.
- Lazy-load routes, screens, and heavy assets that are not on the critical render or startup path.

### Security

- Never embed API keys, tokens, secrets, or credentials in client-side code or bundled assets.
- Treat all data coming from external APIs or user input as untrusted. Validate and sanitize before rendering or processing.
- Do not log PII, tokens, or sensitive user data to the console or client-side logging services.

### Testing

- Unit test component logic, state transformations, and conditional rendering paths.
- Write interaction/behavior tests (clicks, form submission, navigation) for all critical user flows.
- Test loading, error, and empty states — not only the happy path.
- Run the relevant UI test suite and report the result before marking the task done.

---

## Web

### HTML and Semantics

- Use semantic HTML elements (`<nav>`, `<main>`, `<article>`, `<aside>`, `<header>`, `<footer>`, `<button>`, `<form>`). Never use `<div>` or `<span>` for interactive elements.
- Each page must have exactly one `<h1>`. Use a logical heading hierarchy (`h1` → `h2` → `h3`).
- All images require meaningful `alt` text. Decorative images use `alt=""`.
- All form inputs must have associated `<label>` elements.

### Styling

- Use the project's established styling approach (CSS modules, utility classes, CSS-in-JS, etc.) consistently. Do not introduce a second system.
- Avoid hardcoded pixel values for font sizes; use relative units (`rem`, `em`) to respect user font-size preferences.
- Test layouts at standard breakpoints: mobile, tablet, and desktop.

### Performance

- Meet Core Web Vitals targets: LCP, CLS, and INP. Measure with Lighthouse or equivalent.
- Use content hashing for long-lived static assets and set appropriate cache headers.
- Avoid layout thrashing: do not interleave DOM reads and writes in loops.

### Security

- Use HTTPS only. Never serve mixed content.
- Set appropriate security headers: `Content-Security-Policy`, `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`.
- Sanitize any HTML rendered from user input or external sources. Never use `innerHTML` with untrusted content.
- Prefer `httpOnly` cookies for session tokens over `localStorage` to reduce XSS exposure.
- Apply CSRF protection on all state-changing requests.

### Browser Compatibility

- Establish and document the browser support matrix at the project level.
- Test critical flows in all supported browsers before closing a UI task.
- Avoid experimental APIs without a documented fallback for unsupported browsers.

---

## Mobile (iOS / Android / Cross-platform)

### Touch and Input

- Touch targets must meet minimum size requirements: **44×44 pt** on iOS, **48×48 dp** on Android.
- Design for touch-first: avoid hover-only interactions, fine-grained pointer targets, or mouse-centric patterns.
- Support both portrait and landscape orientations unless the project explicitly restricts one.

### Connectivity and Offline

- Handle offline and low-connectivity states gracefully. Show clear feedback; never silently fail.
- Avoid assuming a fast or reliable network. Cache aggressively for critical data.
- Test on throttled network conditions, not only on fast Wi-Fi.

### Platform and OS

- Respect OS conventions for navigation patterns, gestures, and back behavior — do not fight the platform.
- Handle system interruptions: incoming calls, push notifications, and background/foreground app transitions.
- Respect system accessibility settings: Dynamic Type, VoiceOver/TalkBack, Reduce Motion, high-contrast mode.
- Test on real devices or high-fidelity emulators at minimum OS versions supported by the project.

### Permissions

- Request permissions only at the moment they are needed, not at app launch.
- Explain clearly why a permission is needed before requesting it.
- Handle permission denial gracefully: never crash or hide functionality without clear user communication.

### Performance and Battery

- Minimize background processing, location polling, and wake locks to avoid draining battery.
- Profile startup time and reduce time-to-interactive on first launch.
- Avoid memory leaks: dispose listeners, subscriptions, and timers when screens or components are destroyed.

---

## Desktop

### OS Conventions

- Respect platform conventions for menus, keyboard shortcuts, and window management (macOS, Windows, Linux).
- Provide full keyboard navigation for all functionality. Pointer-only flows are not acceptable.
- Handle multi-window, multi-display, and high-DPI/scaling scenarios.

### System Integration

- Handle application lifecycle events: minimize, restore, close, and system shutdown.
- Respect OS-level accessibility settings and system font/theme preferences.
- Test on all target OS versions and DPI configurations before closing a UI task.

---

## Documentation

- `.wbdocs/frontend/index.md` is the single source of truth for the project's UI stack and standards. Keep it current.
- Use `.wbrules/templates/frontend-index.md` to create it if it does not yet exist.
- Create a feature doc at `.wbdocs/features/<feature-name>.md` for any UI feature with non-trivial flows, state, or integration.
- When adding a new screen, component pattern, library, or UI convention, update `.wbdocs/frontend/index.md` immediately — before closing the task.
