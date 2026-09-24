---
name: waypoint
description: Clarifies requirements and user intent through round-based questions. Produces a durable spec.md file. Use only when the user explicitly invokes the waypoint skill.
disable-model-invocation: true
---

# waypoint

Establishes a shared understanding of what should be built and writes it to `.waypoint/{slug}/spec.md`.
The `spec.md` file is the source of truth for **what we want**. Existing code is the source of truth for **what we have**.

---

## Process

1. Determine the slug from the issue or ticket key (for example, `ABC-123`). If none is provided, ask for one or agree on a short slug with the user.
2. Read the request.
   - If no specific request was provided, ask the user to describe the desired change.
   - If a referenced issue or ticket is available via connected tools, retrieve it for additional context. Otherwise proceed with user input.
   - If `.waypoint/{slug}/spec.md` already exists, read it and treat further work as updating that spec.
3. Identify gaps in the request by thinking through multiple lenses:
   - Ambiguities and missing information
   - Conflicts and contradictions
   - Scope and boundaries
   - User journeys and edge cases
   - Success criteria
4. Ask clarifying questions in rounds until requirements are clear.
   - Briefly state relevant context, recommendations and tradeoffs for each question.
   - Provide multiple choices.
   - Group related questions.
   - Number each question.
5. Stop and wait for user input after each round.
   - If answers surface new ambiguities, ask follow-up questions in another round.
6. Once requirements are clear, write `.waypoint/{slug}/spec.md`.
   - Follow [references/schema.md](references/schema.md).
   - Be concise; avoid over-explaining or repeating yourself.
   - Body must contain only the spec content per the schema.
7. Link the file in your reply, briefly summarize it, and ask the user to review.
8. Stop and wait for explicit human approval of the spec.
   - If the user requests changes, update `.waypoint/{slug}/spec.md` and ask for approval again.
9. After approval, tell the user to open a **fresh chat** and continue with **Plan Mode**, with the `.waypoint/{slug}/spec.md` attached. Suggest this prompt, with the real slug filled in: "Switch to plan mode and create an implementation plan for @.waypoint/{slug}/spec.md"

---

## Rules

- If you have access to an interactive question tool, use it. Otherwise fallback to chat.
- Surface assumptions you are making and let the user decide before resolving them into the relevant sections.
- Do not write implementation details, architecture, or code into `.waypoint/{slug}/spec.md`.
- Do not write any code.

---

## Exit Criteria

Finish when:

- `.waypoint/{slug}/spec.md` exists and the user has explicitly approved it.
- The user has been pointed at a fresh chat, with the plan prompt.
