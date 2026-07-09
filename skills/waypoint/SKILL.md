---
name: waypoint
description: Routes software engineering requests to the appropriate waypoint workflow phase.
---

# Waypoint

Entry point to the *waypoint* workflow. Determine the next workflow phase based on the user's request and any available workflow artifacts.

The workflow consists of five actions that each produce an artifact:

| Action | Artifact |
| ------- | ---------- |
| Align | Alignment Brief |
| Plan | Implementation Plan |
| Build | Implementation Report |
| Review | Review Report |
| Ship | Release Package |

---

## Process

1. Determine the furthest completed phase from the available information.
2. Select the earliest incomplete phase.
3. Explain the transition.

---

## Rules

- Route to the earliest phase whose required artifact is unavailable.
- A phase may be skipped only if the user provides equivalent inputs for the next phase.
- Do not perform work that belongs to another phase.
- Do not invent missing artifacts.
