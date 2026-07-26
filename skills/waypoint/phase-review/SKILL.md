---
name: waypoint-review
description: Reviews an implementation for quality, simplicity, and readiness to ship. Produces a Review Report.
disable-model-invocation: true
---

# Review

**Step 4** of the *waypoint* workflow. Evaluates whether the implementation fulfils the **Alignment Brief** and **Implementation Plan** using the simplest implementation that correctly solves the problem.

---

## Process

1. Read the **Alignment Brief**, **Implementation Plan** and **Implementation Report**.
   - Validate each artifact by invoking waypoints `util-artifact` skill.
2. Critically review the implementation along two axes:
   - Specification Axis
      - Functional correctness
      - Faithful adherence to the upstream artifacts
      - Scope discipline
   - Standards Axis
      - Typical code smells defined by Martin Fowler
      - Conformation with existing codebase
      - Safety and reliability
3. Run both review axes as parallel sub-agents. Aggregate their findings.
4. Decide whether the implementation is ready to ship.
   - Approve, when there are no blocking issues.
   - Approve with minor issues, when there are one or more non-blocking issues.
   - Rejected, when there is one or more blocking issues.
      - A blocking issue is a high-confidence defect with significant impact
5. Produce a **Review Report** using waypoints `util-artifact` skill.

---

## Review Report

### Summary

High-level assessment

### Issues

For each finding include:

- Severity (blocking or non-blocking)
- Reason (why does it matter)

#### Specification

Any specification issues. Omit section if none were found.

#### Standards

Any standards issues. Omit section if none were found.

### Decision

Whether the implementation is:

- Approved
- Approved, with minor issues
- Rejected

---

## Rules

- Prefer the simplest implementation that correctly satisfies the requirements.
- Question any additional changes that do not clearly contribute to the requested behavior.
- When this phase's artifact exists and the user continues to work on it in some way, always update affected artifacts using waypoints `util-artifact` skill.
- Do not implement fixes or expand the scope in any way beyond the stated requirements.
- Do not report speculative issues. Assume the implementation is acceptable unless clear evidence to the contrary.

---

## Exit Criteria

Finish when:

- A **Review Report** has been produced.
