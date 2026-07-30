# Domain Documentation

This document provides a high-level map of `wb-ai-rules`, outlining the primary domains and their responsibilities.

## Agent Rules

The Agent Rules domain owns reusable agent operating rules, milestone checklists, documentation-first requirements, safety gates, templates, and companion instructions under `.wbrules/`, `AGENTS.md`, `CLAUDE.md`, and `GEMINI.md`. Agents must read `.wbdocs/domains/agent-rules.md` before changing rule behavior or templates and must keep that domain doc current after related changes.
