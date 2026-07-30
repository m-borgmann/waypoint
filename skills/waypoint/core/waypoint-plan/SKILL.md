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
   - Validate it by using `waypoint-artifact`.
2. Identify relevant architecture, patterns, components and conventions in the existing codebase.
3. Select an implementation approach consistent with the existing codebase.
   - Always search for the simplest possible solution that meets the requirements.
   - Question each implementation decision before proceeding.
4. Break the work into ordered, small and independent tasks.
5. Identify significant implementation risks.
6. Produce an **Implementation Plan** using `waypoint-artifact`.

---

## Implementation Plan

### Goal

Summarize the implementation objective.

### Approach

A list of implementation decisions that were made.
Explain why this approach fits the existing codebase better than reasonable alternatives.
Do not include specific file paths or code snippets.

### Tasks

An ordered list of implementation tasks.

For each task include:

- Objective
- Dependencies
- Verification

### Testing Strategy

If tests are required or advised for the requested change, define what and how it will be tested.

### Risks

Technical risks or constraints that could affect implementation, their impact and mitigation.

---

## Rules

- Prefer extending existing architecture and patterns over introducing new ones.
- Favor simple, incremental changes.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using `waypoint-artifact`.
- Do not write or modify code.
- Do not revisit or question established decisions of the Alignment Brief.

---

## Exit Criteria

Finish when:

- An **Implementation Plan** has been produced.
