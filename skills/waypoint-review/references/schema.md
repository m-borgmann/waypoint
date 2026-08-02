# Review Findings

## Snapshot

Git snapshot of the implementation this review pass evaluated.

- `HEAD`: The first 12 characters of SHA over `HEAD`
- `DIFF`: The first 12 characters of SHA over `git diff HEAD` plus the path and content of each untracked file
  - Otherwise `clean` when there are no staged, unstaged, or untracked changes vs `HEAD`

## Summary

High-level assessment of the current review pass.

## Findings

A living list. Keep fixed and dismissed findings for history; do not delete them.

For each finding include:

- ID (stable, e.g. `F1`)
- Axis (`specification` or `standards`)
- Severity (`critical`, `major`, `minor`, or `info`)
- Status (`open`, `fixed`, or `dismissed`)
- Location (file, symbol, or area when known)
- Reason (why it matters)
- Proposed fix
- Resolution (required when `fixed` or `dismissed`: what changed, or why it was dismissed)

Severity:

- `critical` / `major` — blocking
- `minor` / `info` — non-blocking (`info` needs no action)

## Status

- `Approved` — no open blocking findings (open `minor` / `info` may remain)
- `Rejected` — one or more open blocking findings remain

Include open blocking and open non-blocking counts.
