---
name: waypoint-ship
description: Prepares release artifacts from an approved implementation for version control and deployment. Ensures CI checks pass. Produces a Release Package.
disable-model-invocation: true
---

# Ship - Action

**Optional action** of the *waypoint* workflow. Packages an approved implementation into release-ready artifacts. Includes documentation, changelog entry, commit message options and pull request description. Invoke when you want to ship.

---

## Process

1. Read the Alignment Brief, Implementation Plan, Build Log and Review Findings.
   - Validate each artifact using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
2. Verify the Review Findings **Status** is `Approved`.
   - If approval is absent, stop and report that shipping cannot proceed.
3. Ensure the implementation passes project-defined required CI checks.
   - Skip checks whose surfaces did not change.
   - If any check fails, notify the user which check failed.
   - If it is possible to automatically fix it do so. Otherwise stop and report.
4. Produce a **Release Package** using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
   - Follow the schema defined in [references/artifact.md](references/artifact.md).
   - Populate it using only information contained in the upstream artifacts.

---

## Rules

- Communicate clearly and directly for human readers and maintainers.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
- Do not infer, embellish, or introduce information that is not present upstream artifacts.

---

## Exit Criteria

Finish when:

- A **Release Package** has been produced.
