---
name: dispatch
description: Runs relevant checks and commits the current change. Use only when the user explicitly invokes the dispatch skill.
disable-model-invocation: true
---

# dispatch

Runs the checks that apply to this change, offers conventional commit messages and commits the one the user picks.

`.waypoint/{slug}/spec.md` is the source of truth for **what we want** when present. Code is the source of truth for **what we have**.

---

## Process

1. Determine the slug from the issue or ticket key when available.
2. Inspect the current git state for what is being shipped.
   - If there is nothing to commit, say so and stop.
3. Run the project's relevant checks for the surfaces that changed.
   - If a check fails and the fix is straightforward, fix it and re-run that check.
   - Otherwise stop and report which check failed.
4. Present multiple commit messages in the chat
   - Follow the conventional commit message format. Example: "feat({slug}): add new feature"
   - Each message should be one line, differ in emphasis and must still describe the change accurately.
   - Ground the messages in `.waypoint/{slug}/spec.md` (when present), the code and git state.
   - Stop and wait for the user to pick one. Do not commit before they do.
5. Commit the current change with the selected message.
6. After the commit, include a brief reply.
   - If the change revealed something worth documenting, note it.
   - Include any needed configuration changes or commands that need to run for the change to be active and fully working on another system.

---

## Rules

- If you have access to an interactive question tool, use it. Otherwise fallback to chat.
- Do not infer, embellish, or introduce information that is not supported by `.waypoint/{slug}/spec.md` (when present), the code or the git state.
- Do not commit unless the user picked a message.

---

## Exit Criteria

Finish when:

- The user selected a commit message and that commit exists, or you stopped earlier because checks failed, or there was nothing to commit.
