# Domain Documentation

This document provides a high-level map of `<PROJECT_NAME>`, outlining the primary domains and their responsibilities. Replace the examples below with this project's real domains.

## How to maintain this file

Each domain entry should be exactly one concise paragraph. Cover responsibility, boundaries, interactions with other domains, cross-cutting concerns, and the detailed document agents must read before changing that domain. Use `.wbrules/templates/domain-doc.md` when creating a domain detail page.

Environment classification is mandatory for every task and is tracked separately in `.wbdocs/environment.md`. Keep any Environment domain entry here focused on application behavior owned by the environment/configuration domain, not on secret values.

## Example Domain A

The Example Domain A owns `<PRIMARY_RESPONSIBILITY>`, including `<KEY_CAPABILITY_1>` and `<KEY_CAPABILITY_2>`. It consumes `<UPSTREAM_DEPENDENCY>` and provides `<DOWNSTREAM_CONTRACT>` to `<OTHER_DOMAIN>`, but it does not own `<EXPLICIT_NON_RESPONSIBILITY>`. Agents must read `.wbdocs/domains/<domain-name>.md` before touching this domain and must maintain that file after any related change.

## Example Domain B

The Example Domain B owns `<PRIMARY_RESPONSIBILITY>`, including `<KEY_CAPABILITY_1>` and `<KEY_CAPABILITY_2>`. It coordinates with `<OTHER_DOMAIN>` through `<INTERFACE_OR_DATA_FLOW>` and is responsible for `<OPERATIONAL_OR_SECURITY_CONCERN>`. Agents must read `.wbdocs/domains/<domain-name>.md` before touching this domain and must maintain that file after any related change.
