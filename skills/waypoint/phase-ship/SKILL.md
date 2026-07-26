---
name: waypoint-ship
description: Prepares release artifacts from an approved implementation for version control and deployment. Ensures CI checks pass. Produces a Release Package.
disable-model-invocation: true
---

# Ship

**Step 5** of the *waypoint* workflow. Packages an approved implementation into release-ready artifacts. Includes documentation, changelog entry, commit message and pull request description.

---

## Process

1. Read the Alignment Brief, Implementation Plan, Implementation Report and Review Report.
   - Validate each artifact by invoking waypoints `util-artifact` skill.
2. Verify the Implementation Report records an approval.
   - If approval is absent or the implementation is rejected, stop and report that shipping cannot proceed.
3. Ensure the implementation passes all project-defined required CI checks.
   - If any check fails, notify the user which check failed
   - If it is possible to automatically fix it do so. Otherwise stop and report.
4. Produce a **Release Package** using waypoints `util-artifact` skill.
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

### Commit Message

Conventional commit message.

### PR Description

Structured pull request description for reviewers and QA, including summary and test plan.

### Semantic Versioning

The impact the change has on the current semantic version.

---

## Rules

- Communicate clearly and directly for human readers and maintainers.
- When this phase's artifact exists and the user continues to work on it in some way, always update affected artifacts using waypoints `util-artifact` skill.
- Do not infer, embellish, or introduce information that is not present upstream artifacts.

---

## Exit Criteria

Finish when:

- A **Release Package** has been produced.
