---
name: waypoint-artifact
description: Defines shared guidelines for creating, validating, and updating waypoint workflow artifacts. Use only when already executing a waypoint action or when the user explicitly asked to use waypoint.
disable-model-invocation: true
---

# Artifact - Utility

These guidelines apply to every artifact of the *waypoint* workflow.

---

## Artifact Production

- Create the artifact in the workspace at `.waypoint/{slug}/{action}.md`.
  - `{slug}` is derived from the issue or ticket key (for example, `ABC-123`).
  - `{action}` is the current workflow action (for example, `align`, `plan`, `build`, `review`, or `ship`).
- The artifacts schema is defined in each skill's `references/schema.md`.
- Always be concise and avoid over-explaining or repeating yourself.
- The artifact body must contain only the action output in accordance with its schema, followed by the metadata footer.
- Do not restate content from upstream artifacts. Cross-reference them instead and only write this action's delta.

### Metadata Footer

Read the current version from [../waypoint/references/version.md](../waypoint/references/version.md).

On initial creation:

```
---
Generated with waypoint {current version}
```

On update:

- Same version — keep the existing `Generated with` line; do not add `Last updated with`.
- Different version — keep the original `Generated with` line and add `Last updated with waypoint {current version}` on the next line.

### After Production

- Link the artifact file in your reply. Briefly summarize its content.
- When other affected artifacts were updated, link those too.
- Advise the user to review and optionally tweak each output before proceeding.

## Artifact Maintenance

- Whenever code or decisions change for a ticket that already has waypoint artifacts (including a new chat or follow-up outside the original action session), update every affected artifact to match the newest state.
- Affected artifacts include the current action artifact and any upstream or downstream artifacts invalidated by the change.
- Code and artifacts must always stay in sync.

---

## Artifact Validation

- If the artifact is missing or incomplete, request it and stop.
- Treat each action's artifact as the source of truth for that action.
- Treat upstream artifacts as authoritative.
