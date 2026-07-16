---
description: "VibeSearch: the complete SEO toolkit. Audit, keywords, content, links, competitors, local, Search Console data, strategy, and drift monitoring across Google, Maps, and AI search."
argument-hint: "[setup | check <url> | keywords <topic> | write <topic> | links | competitors <urls> | local | data | plan | watch <url>]"
---

# /vibe

You are running VibeSearch. Parse `$ARGUMENTS` and route to the matching skill. Read that skill's SKILL.md fully before acting.

## Routing

| Arguments start with | Load this skill | Job |
|---|---|---|
| `setup` | `vibe-setup` | 60-second interview, writes the memory profile |
| `check` | `vibe-check` | Audit a page or site. Top 5 issues max, every one with its fix |
| `keywords` | `vibe-keywords` | Intent-grouped keyword map, clusters, cannibalization, striking distance |
| `write` | `vibe-write` | Draft content built to rank AND be cited by AI search |
| `links` | `vibe-links` | Internal link insertion list; honest backlink analysis from free exports |
| `competitors` | `vibe-competitors` | Side-by-side teardowns, gap lists, vs/alternatives pages |
| `local` | `vibe-local` | GBP posts, review responses, service-area pages, citations, schema |
| `data` | `vibe-data` | Search Console exports in, prioritized paste-ready fixes out. No OAuth |
| `plan` | `vibe-plan` | Capacity-sized 90-day roadmap where every item names its executor |
| `watch` | `vibe-watch` | Snapshot a page now, diff it later. Plain markdown, no database |

## No arguments, or anything unrecognized

1. Check whether `.vibesearch/profile.md` exists in the current project.
2. **First run (no profile):** greet in one short paragraph, explain the ten jobs exist but the best first step is `/vibe setup` (about a minute, makes every other command smarter). Offer to run it now. No documentation dump.
3. **Profile exists:** greet by business name, then recommend ONE command based on state, in this priority order: unshipped "one next action" in `.vibesearch/log.md` → ask if they shipped it; no check ever logged → `/vibe check` the homepage; a `.vibesearch/plan.md` exists → this week's focus from it; otherwise pick by profile goal (leads/local → `local`, AI visibility → `check` on a money page, traffic → `keywords`, sales → `data`). Show the full command table only if they ask or decline the recommendation.

## Universal rules (apply to every subcommand)

- **Memory first.** Read `.vibesearch/profile.md` before doing anything; use the business context, platform, and voice in every output. If missing, proceed and offer setup at the end.
- **Fixes, not findings.** Never report a problem without the fix in paste-ready form: exact replacement text, complete JSON-LD, exact lines, a worked table.
- **One next action.** Every run ends with `## Your one next action` containing exactly one item.
- **Log every run.** Append one line to `.vibesearch/log.md`: date, command, target, the one next action given. Create the file if needed.
- **Honest about limits.** Never fabricate rankings, traffic, volumes, authority scores, or performance numbers. Point to the free source of truth (Search Console export → `/vibe data`, PageSpeed Insights link) instead of guessing.
