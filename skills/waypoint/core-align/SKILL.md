---
name: waypoint-align
description: Clarifies requirements and user intent. Produces an Alignment Brief.
disable-model-invocation: true
---

# Align

**First core action** of the *waypoint* workflow. Establishes a shared understanding of **what** should be built.

---

## Process

1. Read the request.
   - If no specific request was provided, ask the user to describe the desired change.
   - If a referenced issue or ticket is available via tools, retrieve and use it. Otherwise proceed with user input.
2. Identify ambiguities, missing information, conflicts and edge cases.
3. Thoroughly ask clarifying questions about every aspect of the request.
   - For each question, briefly state relevant context to make it understandable.
   - Provide multiple choices.
   - Group related questions.
   - Number each question.
   - If you have access to an interactive question tool like AskQuestions, use it. Otherwise fallback to chat.
4. If clarification is required, stop and wait for user input.
   - If answers by the user surface new ambiguities, ask follow-up questions.
5. Once the requirements are clear, produce an **Alignment Brief** using waypoints `util-artifact` skill.

---

## Alignment Brief

### Problem Statement

In plain language: The problem that the user is facing, from the user's perspective.

## Solution

In plain language: The solution to the problem, from the user's perspective.

### User Stories

An extensive, numbered list of user stories with acceptance criteria nested under each story.
Together they cover all aspects of the request.

### Out of Scope

Anything explicitly excluded.

### Constraints

All stated limitations (technical, functional, business, or environmental).

---

## Rules

- Focus only on requirements, not implementation details.
- Explicitly state assumptions. If anything is unclear, ask before proceeding.
- When this action's artifact exists and the user continues to work on it in some way, always update affected artifacts using waypoints `util-artifact` skill.
- Do not propose implementation details, architecture or code.
- Do not write any code.

---

## Exit Criteria

Finish when:

- An **Alignment Brief** has been produced.  
