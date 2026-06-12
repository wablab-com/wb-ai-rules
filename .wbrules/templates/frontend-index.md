# Frontend Standards

This file is the single source of truth for the UI standards of `<PROJECT_NAME>`. All agents **MUST MUST MUST** read this file before writing any UI/frontend code, and **MUST MUST MUST** update it immediately when standards, layouts, colors, or components change.

> Agents: do not introduce libraries, tokens, themes, layout schemes, colors, or component patterns that are not listed here without explicit user approval. Once documented here, you MUST follow these standards. You must also rely on partials as much as possible to build UIs.

---

## Stack

| Concern | Library / Tool | Version | Notes |
|---|---|---|---|
| Framework | `<e.g. React, Vue, Flutter, SwiftUI>` | `<version>` | |
| Component library | `<e.g. shadcn/ui, MUI, Ant Design, None>` | `<version>` | |
| Styling system | `<e.g. Tailwind CSS, CSS Modules, Styled Components>` | `<version>` | |
| Icons | `<e.g. Lucide, Heroicons, FontAwesome>` | `<version>` | |
| Animations | `<e.g. Framer Motion, React Spring, None>` | `<version>` | |
| Charts / data viz | `<e.g. Recharts, Chart.js, None>` | `<version>` | |
| State management | `<e.g. Zustand, Redux Toolkit, Pinia, None>` | `<version>` | |
| Routing | `<e.g. React Router, Next.js App Router, None>` | `<version>` | |
| Forms | `<e.g. React Hook Form, Formik, None>` | `<version>` | |
| HTTP client | `<e.g. Axios, ky, fetch>` | `<version>` | |
| Testing | `<e.g. Vitest + Testing Library, Jest, Cypress>` | `<version>` | |

**Rule**: Adding any entry to this table requires explicit user approval. Agents must not install unlisted packages for UI concerns.

---

## Design Tokens & Standards

Agents must use these tokens and documented standards for all styling, colors, and layouts. Never hardcode raw values or deviate from these structures.

### Colors

| Token | Value | Usage |
|---|---|---|
| `color-primary` | `<e.g. #6366F1>` | Primary actions, links |
| `color-primary-hover` | `<value>` | Hover state for primary |
| `color-secondary` | `<value>` | Secondary actions |
| `color-danger` | `<e.g. #EF4444>` | Destructive actions, errors |
| `color-warning` | `<value>` | Warnings |
| `color-success` | `<value>` | Success states |
| `color-surface` | `<value>` | Card/panel backgrounds |
| `color-background` | `<value>` | Page background |
| `color-text-primary` | `<value>` | Body text |
| `color-text-secondary` | `<value>` | Muted/helper text |
| `color-border` | `<value>` | Borders and dividers |

### Typography

| Token | Value | Usage |
|---|---|---|
| `font-family-base` | `<e.g. 'Inter', sans-serif>` | Body and UI text |
| `font-family-mono` | `<e.g. 'JetBrains Mono', monospace>` | Code blocks |
| `font-size-xs` | `<e.g. 0.75rem>` | Labels, captions |
| `font-size-sm` | `<e.g. 0.875rem>` | Secondary text |
| `font-size-base` | `<e.g. 1rem>` | Body |
| `font-size-lg` | `<e.g. 1.125rem>` | Subtitles |
| `font-size-xl` | `<e.g. 1.25rem>` | Section headings |
| `font-size-2xl` | `<e.g. 1.5rem>` | Page headings |
| `font-weight-normal` | `<e.g. 400>` | |
| `font-weight-medium` | `<e.g. 500>` | |
| `font-weight-semibold` | `<e.g. 600>` | |
| `font-weight-bold` | `<e.g. 700>` | |
| `line-height-base` | `<e.g. 1.5>` | |

### Spacing

| Token | Value |
|---|---|
| `space-1` | `<e.g. 0.25rem / 4px>` |
| `space-2` | `<e.g. 0.5rem / 8px>` |
| `space-3` | `<e.g. 0.75rem / 12px>` |
| `space-4` | `<e.g. 1rem / 16px>` |
| `space-6` | `<e.g. 1.5rem / 24px>` |
| `space-8` | `<e.g. 2rem / 32px>` |
| `space-12` | `<e.g. 3rem / 48px>` |
| `space-16` | `<e.g. 4rem / 64px>` |

### Borders, Shadows, and Radius

| Token | Value | Usage |
|---|---|---|
| `radius-sm` | `<e.g. 4px>` | Inputs, badges |
| `radius-md` | `<e.g. 8px>` | Cards, buttons |
| `radius-lg` | `<e.g. 12px>` | Modals, panels |
| `radius-full` | `<e.g. 9999px>` | Pills, avatars |
| `shadow-sm` | `<value>` | Subtle elevation |
| `shadow-md` | `<value>` | Cards |
| `shadow-lg` | `<value>` | Modals, dropdowns |

---

## Theme

| Setting | Value |
|---|---|
| Default theme | `<light / dark / system>` |
| Dark mode support | `<yes / no>` |
| Theme switching mechanism | `<e.g. CSS variables, class on html element, context provider>` |
| Theme token file location | `<e.g. src/styles/tokens.css>` |

---

## Layout Structure

### Page Shell

Describe the top-level layout of the application:

```
<e.g.>
┌─────────────────────────────────────┐
│ TopNav / Header                     │
├──────────┬──────────────────────────┤
│ Sidebar  │ Main Content Area        │
│          │                          │
└──────────┴──────────────────────────┘
           │ Footer (optional)        │
```

| Region | Component / File | Notes |
|---|---|---|
| Header / TopNav | `<path>` | |
| Sidebar | `<path>` | `<collapsible? always-visible?>` |
| Main content wrapper | `<path>` | |
| Footer | `<path>` | |

### Grid and Breakpoints

| Breakpoint | Min width | Columns | Gutter |
|---|---|---|---|
| `xs` | `<e.g. 0px>` | `<e.g. 4>` | `<e.g. 16px>` |
| `sm` | `<e.g. 640px>` | `<e.g. 8>` | `<e.g. 16px>` |
| `md` | `<e.g. 768px>` | `<e.g. 12>` | `<e.g. 24px>` |
| `lg` | `<e.g. 1024px>` | `<e.g. 12>` | `<e.g. 24px>` |
| `xl` | `<e.g. 1280px>` | `<e.g. 12>` | `<e.g. 32px>` |

---

## Component Patterns

Document every reusable component pattern. Agents must use these; they must not create parallel versions.

### Buttons

| Variant | Usage | Class / Component |
|---|---|---|
| Primary | Main call-to-action | `<e.g. <Button variant="primary">` |
| Secondary | Alternative action | `<e.g. <Button variant="secondary">` |
| Destructive | Delete, remove, irreversible action | `<e.g. <Button variant="destructive">` |
| Ghost | Low-emphasis action | `<e.g. <Button variant="ghost">` |
| Link | Inline text action | `<e.g. <Button variant="link">` |
| Icon-only | Toolbar/icon button | `<e.g. <IconButton aria-label="...">` |

Button sizes: `<sm | md | lg>`. Default: `<md>`.
Loading state: `<how to show spinner inside button>`.
Disabled state: `<visual treatment and aria-disabled usage>`.

### Modals and Dialogs

| Type | Usage | Component |
|---|---|---|
| Confirmation dialog | Destructive or irreversible actions | `<e.g. <ConfirmDialog>` |
| Form modal | Create or edit in an overlay | `<e.g. <Modal>` |
| Alert dialog | System messages requiring acknowledgment | `<e.g. <AlertDialog>` |

Modal rules:
- Always trap focus inside the modal when open.
- Always close on `Escape` key.
- Always provide a visible close button.
- Overlay backdrop: `<color and opacity>`.
- Max width: `<e.g. 480px for sm, 640px for md, 800px for lg>`.

### Drawers / Sidepanels

| Variant | Direction | Component |
|---|---|---|
| `<e.g. filter drawer>` | `<right>` | `<component>` |

### Toasts / Notifications

| Variant | Usage | Component |
|---|---|---|
| Success | Positive outcome | `<e.g. toast.success(...)>` |
| Error | Failure | `<e.g. toast.error(...)>` |
| Warning | Non-blocking caution | `<e.g. toast.warning(...)>` |
| Info | Neutral message | `<e.g. toast.info(...)>` |

Position: `<e.g. top-right>`. Auto-dismiss: `<e.g. 4000ms>`.

### Forms

| Element | Component | Notes |
|---|---|---|
| Text input | `<component>` | |
| Textarea | `<component>` | |
| Select / dropdown | `<component>` | |
| Checkbox | `<component>` | |
| Radio group | `<component>` | |
| Switch / toggle | `<component>` | |
| Date picker | `<component>` | |
| File upload | `<component>` | |

Form layout: `<e.g. label above input, full width, 16px gap between fields>`.
Validation: `<e.g. inline error below field, red border, error icon>`.
Required field indicator: `<e.g. asterisk * after label>`.

### Tables and Data Grids

| Feature | Supported | Notes |
|---|---|---|
| Sorting | `<yes/no>` | |
| Filtering | `<yes/no>` | |
| Pagination | `<yes/no>` | `<page size options>` |
| Row selection | `<yes/no>` | |
| Inline actions | `<yes/no>` | |
| Empty state | `<yes/no>` | `<what to show>` |

Component: `<component name and import path>`.

### Navigation

| Pattern | Component | Notes |
|---|---|---|
| Top navigation bar | `<component>` | |
| Sidebar navigation | `<component>` | |
| Breadcrumbs | `<component>` | |
| Tabs | `<component>` | |
| Pagination | `<component>` | |

### Badges and Status Indicators

| Variant | Usage | Class / Component |
|---|---|---|
| Default | Neutral label | `<component>` |
| Success | Active, complete | `<component>` |
| Warning | Pending, at risk | `<component>` |
| Danger | Error, failed | `<component>` |
| Info | Informational | `<component>` |

### Loading States

| Pattern | Usage | Component |
|---|---|---|
| Skeleton screen | Content loading | `<component>` |
| Spinner | Action in progress | `<component>` |
| Progress bar | Known progress | `<component>` |

### Empty States

All empty states must include: an illustration or icon, a clear headline, a short description, and (where applicable) a primary action button.
Component: `<component name>`.

---

## Routing

| Concern | Approach | Notes |
|---|---|---|
| Router | `<library>` | |
| Route definition file | `<path>` | |
| Auth-protected routes | `<mechanism>` | |
| 404 / not found page | `<path>` | |
| Layout wrapping | `<how routes are wrapped in the shell>` | |

---

## State Management

| Concern | Approach | Notes |
|---|---|---|
| Global state tool | `<library or None>` | |
| Server/async state | `<e.g. React Query, SWR, None>` | |
| Form state | `<e.g. React Hook Form, local state>` | |
| Local component state | `<e.g. useState, ref>` | |

Rules:
- `<any project-specific state management rules>`

---

## Verification

| Check | Command |
|---|---|
| Unit and component tests | `<e.g. npm test>` |
| E2E / integration tests | `<e.g. npm run test:e2e>` |
| Accessibility audit | `<e.g. npx axe-cli http://localhost:3000>` |
| Visual / storybook | `<e.g. npm run storybook>` |
| Type check | `<e.g. npm run typecheck>` |
| Lint | `<e.g. npm run lint>` |
