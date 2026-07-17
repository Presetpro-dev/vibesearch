# VibeSearch (repo development context)

This file is for working ON the plugin, not using it. Installed plugins ignore it.

## What this repo is

A Claude Code plugin built around one object: `.vibesearch/ledger.md`, the Answer Ledger. One `/vibe` coach command routes to seven skills (start, map, win, fix, images, local, watch) and two agents (vibe-page-auditor, vibe-question-prober). Zero runtime dependencies by design.

## Non-negotiable product rules

1. The ledger is the center of gravity; every skill reads or writes it.
2. Probes are live web-search visibility checks, dated, never a claim to have queried a specific AI chat product. State this every time a probe result is shown.
3. `/vibe win` never marks a question "won" from a draft alone; only a fresh probe earns that status.
4. Fixes and drafts are always paste-ready, never a to-do list. `/vibe fix` caps at 5 issues.
5. Every run ends with exactly one next action, and appends to `.vibesearch/log.md`.
6. Command surface is capped at the coach plus seven moves. New disciplines become lenses or reference files inside an existing skill before they earn a new command.
7. Anti-doorway guardrails in vibe-local remain safety rails, not suggestions.

## Conventions

- Skill bodies stay under ~220 lines; deep material goes in `references/`.
- American spelling. No em-dashes anywhere in this repo or its outputs by default.
- Version bumps update both manifests and CHANGELOG.md together.

## Testing a change locally

From the repo's parent directory in Claude Code: `/plugin marketplace add ./vibesearch` then `/plugin install vibesearch@vibesearch`. Run `/vibe start` against a real site, confirm the four files are written, then `/vibe` to confirm the coach picks a sensible move.
