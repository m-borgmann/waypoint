---
name: waypoint-ship
description: Prepares release artifacts from an approved implementation for version control and deployment. Ensures the current state passed review and CI checks. Produces a Release Package.
disable-model-invocation: true
---

# Ship - Action

Optional action of the waypoint workflow. Packages an approved implementation into release-ready artifacts. Includes documentation, changelog entry, commit message options and pull request description. Invoke when you want to ship.

---

## Process

1. Read the Alignment Brief, Implementation Plan, Build Log and Review Findings.
   - Validate each artifact using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
2. Verify Review Findings:
   - Compute the current snapshot as defined in the Review Findings schema
   - Treat review as stale when Review Findings are absent or either snapshot value differs from the current snapshot.
   - If stale, run an incremental review using the [`waypoint-review`](../waypoint-review/SKILL.md) skill before continuing.
3. Ensure the implementation passes project-defined required CI checks.
   - Re-run checks when review was stale in step 2.
   - Skip checks whose surfaces did not change.
   - If any check fails, notify the user which check failed.
   - If it is possible to automatically fix it do so. Otherwise stop and report.
4. Produce a Release Package using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
   - Follow the schema defined in [references/schema.md](references/schema.md).
   - Populate it using only information contained in the upstream artifacts.

---

## Rules

- Communicate clearly and directly for human readers and maintainers.
- Do not infer, embellish, or introduce information that is not present upstream artifacts.
- Do not ship code that has not passed review for its current state.

---

## Exit Criteria

Finish when:

- A Release Package has been produced.
