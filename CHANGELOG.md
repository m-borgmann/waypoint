# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [2.0.0] - 2026-07-26

### Added

- README notes that *waypoint* is designed for and most tested with Cursor, plus Claude Code install guidance
- Recommended Tooling now includes Figma MCP and clarifies browser self-verification (Cursor built-in vs Browser MCP)
- README acknowledgments for Vercel Labs Skills and CodeRabbit

### Changed

- Renamed workflow vocabulary from phases to actions; skill folders are now `action-*`
- Artifact paths are now `.waypoint/{slug}/{action}.md` (one living file per action; dates removed)
- Core actions are align, plan, build, and review; ship is an optional action invoked on demand
- `waypoint` router distinguishes Progress (core), Revision, and Optional routing
- README explains actions vs phases and the core/optional split
- Renamed build artifact to Build Log and review artifact to Review Findings
- Reworked `waypoint-review` into a living findings loop with severity, status, and approval when no open blocking findings remain
- Strengthened and clarified wording `waypoint-build` and `waypoint-review` mainly to enforce simplification
- `waypoint-ship` Release Package now offers three conventional commit message options
- `waypoint-ship` Release Package includes a Learnings section for project knowledge worth documenting
- After producing an artifact, reply with only a file link and ask the user to review before the next action
- `waypoint-align` clarifying questions include brief context and why they are asked
- `waypoint-align` asks only until the Alignment Brief is unambiguous, not about every aspect of the request
- `waypoint-build` matches surrounding comment density and idiom instead of prescribing when to comment

## [1.1.0] - 2026-07-26

### Added

- Artifact maintenance in `util-artifact` so follow-ups and revisions keep every affected artifact in sync, including new chats
- Progress vs Revision routing in the `waypoint` entry skill, so changes to existing work can reopen the owning phase
- Phase skills now require updating affected artifacts when work continues after the phase artifact exists

### Changed

- `waypoint` is documented and described as explicit opt-in only; ordinary requests without that context use the normal agent flow
- README covers Progress/Revision routing, opt-in usage, and living artifact sync
- Minor banner color and weight tweaks (`assets/banner.html`, `assets/banner.webp`)

## [1.0.1] - 2026-07-15

### Changed

- Redesigned repository banner (`assets/banner.html`, `assets/banner.webp`) with a dark visual theme
- Polished README wording and recommended tooling section
- Clarified `waypoint-align` question flow (choices, optional question tool, follow-ups)
- Streamlined `waypoint-ship` CI verification wording
- Normalized phase skill descriptions to plain artifact names

### Added

- `waypoint-build` now checks whether each task's implementation can be simplified after verification

## [1.0.0] - 2026-07-09

Initial release of *waypoint*, an opinionated workflow for agentic engineering.

### Added

- `waypoint` router skill that selects the next workflow phase based on available artifacts
- `waypoint-align` skill for requirements clarification; produces an Alignment Brief
- `waypoint-plan` skill for implementation planning against the existing codebase; produces an Implementation Plan
- `waypoint-build` skill for sequential task execution with per-task verification; produces an Implementation Report
- `waypoint-review` skill for specification and standards review via parallel sub-agents; produces a Review Report
- `waypoint-ship` skill for release packaging, CI verification, and shipping artifacts; produces a Release Package
- `util-artifact` skill with shared artifact creation, validation, and storage conventions under `.waypoint/{ticket-slug}/{phase}/{YYYY-MM-DD}.md`
- README with installation via the Vercel Skills CLI, workflow overview, best practices, recommended MCP tooling, and artifact layout
- Repository banner assets (`assets/banner.html`, `assets/banner.webp`)
- MIT License

[2.0.0]: https://github.com/m-borgmann/waypoint/releases/tag/v2.0.0
[1.1.0]: https://github.com/m-borgmann/waypoint/releases/tag/v1.1.0
[1.0.1]: https://github.com/m-borgmann/waypoint/releases/tag/v1.0.1
[1.0.0]: https://github.com/m-borgmann/waypoint/releases/tag/v1.0.0
