---
name: waypoint-align
description: Clarifies requirements and user intent. Produces an Alignment Brief.
disable-model-invocation: true
---

# Align

**Step 1** of the *waypoint* workflow. Establish a shared understanding of **what** should be built.

---

## Process

1. Read the request.
   - If no specific request was provided, ask the user to describe the desired change.
   - If a referenced issue or ticket is available via tools, retrieve and use it. Otherwise proceed with user input.
2. Identify ambiguities, missing information, conflicts and edge cases.
3. Thoroughly ask clarifying questions about every aspect of the request.
   - Provide multiple choices.
   - Group related questions.
   - Number each question.
   - If you have access to a question tool, use it.
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
- Do not propose implementation details, architecture or code.
- Do not write any code.

---

## Exit Criteria

Finish when:

- An **Alignment Brief** has been produced.  
