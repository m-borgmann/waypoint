---
name: waypoint
description: Routes software engineering requests to the appropriate waypoint workflow phase, including revisions when waypoint artifacts already exist. Use only when the user explicitly invokes waypoint or asks to use the waypoint workflow.
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
2. Classify the request:
   - **Progress**: The user is advancing the workflow to the next incomplete phase.
   - **Revision**: The user is changing requirements, design or implementation for work that already has waypoint artifacts (including a new chat).
3. If **Progress**, select the earliest incomplete phase.
4. If **Revision**, select the furthest completed phase that owns the requested change.
5. Explain the transition.
6. Follow the selected phase skill. Apply waypoints `util-artifact` skill so affected artifacts stay in sync.

---

## Rules

- Apply this workflow only when the user explicitly requested waypoint.
- Route Progress requests to the earliest phase whose required artifact is unavailable.
- Route Revision requests back into the relevant completed phase.
- After Revision work, update every affected artifact using waypoints `util-artifact` skill.
- A phase may be skipped only if the user provides equivalent inputs for the next phase.
- Do not perform work that belongs to another phase.
- Do not invent missing artifacts.
