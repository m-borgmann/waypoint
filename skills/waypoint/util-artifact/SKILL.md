---
name: util-artifact
description: Defines shared guidelines for workflow artifacts.
---

# Util Artifact

These guidelines apply to every artifact of the *waypoint* workflow.

---

## Artifact Production

- Create the artifact in the workspace at `.waypoint/{ticket-slug}/{phase}/{YYYY-MM-DD}.md`.
- `{ticket-slug}` is derived from the issue or ticket key (for example, `ABC-123` → `abc-123`).
- `{phase}` is the current workflow phase (for example, `align`, `plan`, `build`, `review` or `ship`).
- Be concise when writing its content. Do not over-explain or repeat yourself.

### File Creation

- Create any missing directories.
- If an artifact already exists for the same date, update its content to reflect the newest agreed upon state.
- The artifact must contain only the phase output in Markdown.

---

## Artifact Validation

- If the artifact is missing or incomplete, request it and stop.
- Treat the most recent artifact version as the source of truth.
- Treat upstream artifacts as authoritative.
