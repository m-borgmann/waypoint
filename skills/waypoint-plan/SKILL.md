---
name: waypoint-plan
description: Produces an *Implementation Plan* from an existing Alignment Brief.
disable-model-invocation: true
---

# Plan - Core Action

**Second core action** of the *waypoint* workflow. Determines **how** the requested change should be implemented.

---

## Process

1. Read the Alignment Brief.
   - Validate it using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
2. Identify relevant architecture, patterns, components and conventions in the existing codebase.
3. Select an implementation approach consistent with the existing codebase.
   - Always search for the simplest possible solution that meets the requirements.
   - Question each implementation decision before proceeding.
4. Break the work into ordered, small and independent tasks.
5. Identify significant implementation risks.
6. Produce an **Implementation Plan** using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
   - Follow the schema defined in [references/artifact.md](references/artifact.md).

---

## Rules

- Prefer extending existing architecture and patterns over introducing new ones.
- Favor simple, incremental changes.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
- Do not write or modify code.
- Do not revisit or question established decisions of the Alignment Brief.

---

## Exit Criteria

Finish when:

- An **Implementation Plan** has been produced.
