# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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

[1.0.0]: https://github.com/m-borgmann/waypoint/releases/tag/v1.0.0
