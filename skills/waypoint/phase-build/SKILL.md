---
name: waypoint-build
description: Executes an *Implementation Plan* and produces an *Implementation Report*.
disable-model-invocation: true
---

# Build

**Step 3** of the *waypoint* workflow. Execute the **Implementation Plan** one task at a time, continuously verifying progress until implementation is complete.

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
   - Run the smallest meaningful verification available.
   - Resolve failures before continuing.
4. Once all tasks are complete, produce an **Implementation Report** using waypoints `util-artifact` skill.

---

## Implementation Report

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
- Do not revisit product or architectural decisions.
- Do not make incidental improvements, refactor unrelated code or expand the scope in any way.

---

## Exit Criteria

Finish when:

- An **Implementation Report** has been produced.
