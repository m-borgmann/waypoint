---
name: util-artifact
description: Defines shared guidelines for creating, validating, and updating waypoint workflow artifacts. Use only when already executing a waypoint action or when the user explicitly asked to use waypoint.
---

# Util Artifact

These guidelines apply to every artifact of the *waypoint* workflow.

---

## Artifact Production

- Create the artifact in the workspace at `.waypoint/{slug}/{action}.md`.
- `{slug}` is derived from the issue or ticket key (for example, `ABC-123`).
- `{action}` is the current workflow action (for example, `align`, `plan`, `build`, `review`, or `ship`).
- Be concise when writing its content. Do not over-explain or repeat yourself.

### File Creation

- Create any missing directories.
- If an artifact already exists for the action, update its content to reflect the newest state.
- The artifact must contain only the action output in Markdown.

### After Production

- In the chat reply, link the artifact file first. Very briefly summarize its content.
- Advise the user to review the artifact before proceeding to the next action.

## Artifact Maintenance

- Whenever code or decisions change for a ticket that already has waypoint artifacts (including a new chat or follow-up outside the original action session), update every affected artifact to match the newest state.
- Affected artifacts include the current action artifact and any upstream or downstream artifacts invalidated by the change.
- Code and artifacts must always stay in sync.

---

## Artifact Validation

- If the artifact is missing or incomplete, request it and stop.
- Treat each action's artifact as the source of truth for that action.
- Treat upstream artifacts as authoritative.
