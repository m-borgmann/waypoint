---
name: waypoint
description: Routes software engineering requests to the appropriate waypoint workflow action, including revisions when waypoint artifacts already exist. Use only when the user explicitly invokes waypoint or asks to use the waypoint workflow.
disable-model-invocation: true
---

# Waypoint

Version: [references/version.md](references/version.md)

Entry point to the waypoint workflow. Determine the next workflow action based on the user's request and any available workflow artifacts.

The workflow is built from actions. Each core action produces an artifact.

Core actions form the default progression:

| Action | Skill | File | Artifact |
| ------- | ---------- | ---------- | ---------- |
| Align | [`waypoint-align`](../waypoint-align/SKILL.md) | `align.md` | Alignment Brief |
| Plan | [`waypoint-plan`](../waypoint-plan/SKILL.md) | `plan.md` | Implementation Plan |
| Build | [`waypoint-build`](../waypoint-build/SKILL.md) | `build.md` | Build Log |
| Review | [`waypoint-review`](../waypoint-review/SKILL.md) | `review.md` | Review Findings |

Optional actions are invoked when the user wants them. They are not required for progressing through the core sequence:

| Action | Skill | File | Artifact |
| ------- | ---------- | ---------- | ---------- |
| Ship | [`waypoint-ship`](../waypoint-ship/SKILL.md) | `ship.md` | Release Package |

---

## Process

1. Determine the furthest completed core action from the available information.
   - Review is complete only when Review Findings exist with Status `Approved`.
2. Classify the request:
   - Progress: The user is advancing the workflow to the next incomplete core action.
   - Revision: The user is changing requirements, design or implementation for work that already has waypoint artifacts.
   - Optional: The user explicitly requests an optional action (for example, ship).
3. If Progress, select the earliest incomplete core action.
4. If Revision, select the furthest completed action that owns the requested change.
5. If Optional, select that action only when the user asked for it and its prerequisites are met.
6. Explain the transition.
7. Read and follow the selected action skill. Use the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill so affected artifacts stay in sync.

---

## Rules

- Apply this workflow only when the user explicitly requested waypoint.
- Routing to another skill counts as explicit user intent because the user invoked waypoint.
- Route Progress requests to the earliest core action whose required artifact is unavailable, or whose Review Findings are not `Approved`.
- Route Revision requests back into the relevant completed action.
- Route optional actions only when the user explicitly requests them.
- After Revision work, update every affected artifact using the [`waypoint-artifact`](../waypoint-artifact/SKILL.md) skill.
- Do not perform work that belongs to another action.
- Do not invent missing artifacts.
