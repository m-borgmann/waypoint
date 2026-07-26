---
name: waypoint-build
description: Executes an Implementation Plan and produces a Build Log.
disable-model-invocation: true
---

# Build

**Third core action** of the *waypoint* workflow. Executes the **Implementation Plan** one task at a time, continuously verifying progress until implementation is complete.

---

## Process

1. Read the Implementation Plan.
   - Validate it by invoking waypoints `util-artifact` skill.
2. Execute tasks sequentially, one at a time.
   - Implement only what the task requires.
   - Actively keep the user involved in implementation decisions when judgment is required.
   - Whenever clarification is needed, stop and wait for user feedback.
   - Add concise code comments where behavior is non-obvious.
3. After each task:
   - Verify that the implementation fulfils the task.
   - Determine wether the implementation can be simplified.
   - Run the smallest meaningful verification available.
   - Resolve failures before continuing.
4. Once all tasks are complete, produce a **Build Log** using waypoints `util-artifact` skill.

---

## Build Log

### Completed Tasks

For each task include:

- Summary
- Changes
- Verification

### Deviations

Any necessary deviations from the Implementation Plan, including justification.

---

## Rules

- Make only surgical changes directly required by a task.
- Prefer the simplest correct solution.
- Give little weight to development effort when making technical decisions.
- If changes result in orphaned code, verify whether it is used elsewhere and remove it if it is not.
- Match existing code style, naming conventions and comment language.
- Verify each task before proceeding.
- If you encounter dead code, debug logs, or dumps, explicitly flag them. Do not remove them without user confirmation.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using waypoints `util-artifact` skill.
- Do not revisit product or architectural decisions.
- Do not make incidental improvements, refactor unrelated code or expand the scope in any way.

---

## Exit Criteria

Finish when:

- A **Build Log** has been produced.
