---
name: waypoint-review
description: Reviews an implementation in a living findings loop until no open blocking issues remain. Produces Review Findings.
disable-model-invocation: true
---

# Review

**Fourth core action** of the *waypoint* workflow. Evaluates whether the implementation fulfils the **Alignment Brief** and **Implementation Plan** using the simplest implementation that correctly solves the problem. Continues until no open blocking findings remain.

---

## Process

1. Read the **Alignment Brief**, **Implementation Plan** and **Build Log**.
   - Validate each artifact by invoking waypoints `util-artifact` skill.
2. Load existing **Review Findings** if present.
   - If absent, run a **full review** of the entire implementation.
   - If present, run an **incremental review**: re-verify every open finding against the current code, then review only changes since the last pass.
3. Critically review along two axes as parallel sub-agents. Aggregate their findings.
   - Specification Axis
      - Functional correctness
      - Faithful adherence to the upstream artifacts
      - Scope discipline
   - Standards Axis
      - Security and privacy
      - Stability and reliability
      - Data integrity and integration boundaries
      - Performance and scalability
      - Maintainability, code smells, and conformance with the existing codebase
4. Merge results into the living findings list.
   - Mark findings **fixed** when the current code clearly addresses them.
   - Mark findings **dismissed** only when the user explicitly dismisses them.
   - Add new findings as **open**. Do not reopen fixed or dismissed findings without new evidence.
5. Update **Review Findings** using waypoints `util-artifact` skill.
   - Set **Status** to **Approved** only when there are no open blocking findings.
   - Otherwise set **Status** to **Changes requested**.
6. If **Changes requested**, resolve open blocking findings one at a time.
   - Present the finding and keep the user involved when judgment is required.
   - Apply the smallest correct fix. Do not expand scope.
   - Verify the fix, mark the finding **fixed**, then return to step 2 for an incremental review.
7. Finish when **Status** is **Approved**.

---

## Review Findings

### Summary

High-level assessment of the current review pass.

### Findings

A living list. Keep fixed and dismissed findings for history; do not delete them.

For each finding include:

- ID (stable, e.g. `F1`)
- Axis (`specification` or `standards`)
- Severity (`critical`, `major`, `minor`, or `info`)
- Status (`open`, `fixed`, or `dismissed`)
- Location (file, symbol, or area when known)
- Reason (why it matters)
- Resolution (required when `fixed` or `dismissed`: what changed, or why it was dismissed)

Severity:

- `critical` / `major` — blocking
- `minor` / `info` — non-blocking (`info` needs no action)

### Status

- `Approved` — no open blocking findings (open `minor` / `info` may remain)
- `Changes requested` — one or more open blocking findings remain

Include open blocking and open non-blocking counts.

---

## Rules

- Prefer the simplest implementation that correctly satisfies the requirements.
- Question any additional changes that do not clearly contribute to the requested behavior.
- Report only high-confidence issues with clear evidence. Do not speculate.
- Keep findings current: every review pass must refresh statuses against the code.
- Fix only open blocking findings inside this action, and only with surgical changes.
- Leave open non-blocking findings unless the user asks to address them.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using waypoints `util-artifact` skill.
- Do not revisit product or architectural decisions from upstream artifacts.
- Do not expand scope beyond the stated requirements.
- Do not duplicate findings.

---

## Exit Criteria

Finish when:

- **Review Findings** exist with **Status** `Approved`.
