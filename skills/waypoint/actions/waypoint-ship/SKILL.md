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
   - Validate each artifact by using `waypoint-artifact`.
2. Verify the Review Findings **Status** is `Approved`.
   - If approval is absent, stop and report that shipping cannot proceed.
3. Ensure the implementation passes project-defined required CI checks.
   - Skip checks whose surfaces did not change.
   - If any check fails, notify the user which check failed.
   - If it is possible to automatically fix it do so. Otherwise stop and report.
4. Produce a **Release Package** using `waypoint-artifact`.
   - Populate it using only information contained in the upstream artifacts.

---

## Release Package

### Summary

User-facing description of the change.

### Changes

List of all changes. Follow the "Keep A Changelog" format.
Omit empty categories.

### Technical Notes

Migrations, configuration or dependency changes.
Omit section if there is nothing relevant.

### Deployment Notes

Rollback strategy, feature flag usage, or rollout considerations.
Omit section if there is nothing relevant.

### Commit Messages

Three different conventional commit message options for the user to choose from.

### PR Description

Structured pull request description for reviewers and QA, including summary and test plan.

### Semantic Versioning

The impact the change has on the current semantic version.

### Learnings

Concrete documentation suggestions for what this ticket newly revealed about the project or codebase.
Omit section if there is nothing to capture.

---

## Rules

- Communicate clearly and directly for human readers and maintainers.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using `waypoint-artifact`.
- Do not infer, embellish, or introduce information that is not present upstream artifacts.

---

## Exit Criteria

Finish when:

- A **Release Package** has been produced.
