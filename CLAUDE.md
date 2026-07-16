# VibeSearch (repo development context)

This file is for working ON the plugin, not using it. Installed plugins ignore it.

## What this repo is
A Claude Code plugin: one `/vibe` command routing to ten skills plus one agent, covering the complete SEO discipline (see docs/COVERAGE.md). Zero runtime dependencies by design; the core must never require Python, Node packages, an install script, or OAuth.

## Non-negotiable product rules (enforce in every skill edit)
1. Fixes, not findings: no issue without a paste-ready fix.
2. Hard caps: 5 issues per check, 10 opportunities per data run; one next action per run, always.
3. Memory: skills read `.vibesearch/profile.md` first and append to `.vibesearch/log.md` last.
4. Honest data: never fabricate rankings, volumes, traffic, authority scores, or performance numbers. Free-source pointers instead.
5. Anti-doorway guardrails in vibe-local are safety rails, not suggestions.
6. Commands are organized by job-to-be-done (diagnose, target, create, connect...), never by SEO discipline. New disciplines extend existing verbs before earning a new one.

## Conventions
- Skill bodies stay under ~200 lines; deep material goes in `references/`.
- Frontmatter descriptions are "pushy": what the skill does AND every phrasing that should trigger it.
- American spelling. No em-dashes anywhere in this repo or its outputs by default.
- Version bumps update `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`, and CHANGELOG.md together.

## Testing a change locally
From the repo's parent directory in Claude Code: `/plugin marketplace add ./vibesearch` then `/plugin install vibesearch@vibesearch`. Run all ten commands against a real site; confirm each ends with one next action and a log append, and that no output contains an invented metric.
