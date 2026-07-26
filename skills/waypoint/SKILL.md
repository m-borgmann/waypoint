---
name: waypoint
description: Routes software engineering requests to the appropriate waypoint workflow action, including revisions when waypoint artifacts already exist. Use only when the user explicitly invokes waypoint or asks to use the waypoint workflow.
---

# Waypoint

Entry point to the *waypoint* workflow. Determine the next workflow action based on the user's request and any available workflow artifacts.

The workflow is built from **actions**. Each core action produces an artifact.

**Core actions** form the default progression:

| Action | Artifact |
| ------- | ---------- |
| Align | Alignment Brief |
| Plan | Implementation Plan |
| Build | Build Log |
| Review | Review Findings |

**Optional actions** are invoked when the user wants them (for example, Ship). They are not required for progressing through the core sequence:

| Action | Artifact |
| ------- | ---------- |
| Ship | Release Package |

---

## Process

1. Determine the furthest completed core action from the available information.
   - Review is complete only when **Review Findings** exist with **Status** `Approved`.
2. Classify the request:
   - **Progress**: The user is advancing the workflow to the next incomplete core action.
   - **Revision**: The user is changing requirements, design or implementation for work that already has waypoint artifacts (including a new chat).
   - **Optional**: The user explicitly requests an optional action (for example, ship).
3. If **Progress**, select the earliest incomplete core action.
4. If **Revision**, select the furthest completed action that owns the requested change.
5. If **Optional**, select that action only when the user asked for it and its prerequisites are met.
6. Explain the transition.
7. Follow the selected action skill. Apply waypoints `util-artifact` skill so affected artifacts stay in sync.

---

## Rules

- Apply this workflow only when the user explicitly requested waypoint.
- Route Progress requests to the earliest core action whose required artifact is unavailable, or whose Review Findings are not `Approved`.
- Route Revision requests back into the relevant completed action.
- Route optional actions only when the user explicitly requests them.
- After Revision work, update every affected artifact using waypoints `util-artifact` skill.
- A core action may be skipped only if the user provides equivalent inputs for the next core action.
- Do not perform work that belongs to another action.
- Do not invent missing artifacts.
