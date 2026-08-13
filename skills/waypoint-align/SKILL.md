---
name: waypoint-align
description: Clarifies requirements and user intent. Produces an Alignment Brief.
disable-model-invocation: true
---

# Align - Core Action

First core action of the waypoint workflow. Establishes a shared understanding of what should be built.

---

## Process

1. Read the request.
   - If no specific request was provided, ask the user to describe the desired change.
   - If a referenced issue or ticket is available via connected tools, retrieve it for additional context. Otherwise proceed with user input.
2. Identify gaps in the request by thinking through multiple lenses:
   - Ambiguities and missing information
   - Conflicts and contradictions
   - Scope and boundaries
   - User journeys and edge cases
   - Success criteria and boundaries
3. Thoroughly ask questions to clarify and close those gaps.
   - Briefly state relevant context, recommendations and tradeoffs for each question.
   - Provide multiple choices.
   - Group related questions.
   - Number each question.
   - If you have access to an interactive question tool, use it. Otherwise fallback to chat.
4. If clarification is required, stop and wait for user input.
   - If answers by the user surface new ambiguities, ask follow-up questions.
5. Once the requirements are clear, produce an Alignment Brief using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
   - Follow the schema defined in [references/schema.md](references/schema.md).

---

## Rules

- Focus only on requirements, not implementation details.
- Surface assumptions you are making and let the user decide before resolving them into the relevant sections.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
- Do not propose implementation details, architecture or code.
- Do not write any code.

---

## Exit Criteria

Finish when:

- An Alignment Brief has been produced.
