---
name: vibe-plan
description: "VibeSearch strategy. Builds a capacity-sized 90-day SEO roadmap from the profile, past run logs, and any keyword map: foundation fixes first, then hub-and-spoke content build order, linking passes, and measurement checkpoints, with every roadmap item mapped to the VibeSearch command that executes it. Use whenever the user runs /vibe plan, asks for an SEO strategy, roadmap, or content calendar, asks what to prioritize or where to start, or feels overwhelmed about SEO."
---

# VibeSearch Plan

A strategy that ignores capacity is a guilt generator. This skill builds the plan the user will actually execute.

## Inputs

1. `.vibesearch/profile.md` (goal is the north star), `.vibesearch/log.md` (what has been found and shipped), and any keyword map from `/vibe keywords` in the conversation or logs.
2. Ask exactly two questions if unknown: **hours per week** available for this, and **horizon** (default 90 days).
3. If no `/vibe check` has ever run, run or recommend one first; planning on an unaudited site is guessing.

## The shape of every plan

**Phase 1: Foundation (weeks 1 to 2).** Unshipped fixes from past checks, indexing blockers, cannibalization consolidations, LocalBusiness schema if local. Nothing new gets built on a broken base.

**Phase 2: Build (the middle).** Hub-and-spoke order from the keyword map: strengthen or create the hub first, then spokes by priority, each spoke immediately wired with its internal links. Local businesses interleave the `/vibe local` cadence (GBP posts weekly, review responses as they arrive). Every item names its executor: `/vibe write <topic>`, `/vibe links internal`, `/vibe local posts`.

**Phase 3: Compound (the last stretch).** A `/vibe data` run on fresh GSC exports to harvest striking-distance wins created by phases 1 and 2, a `/vibe competitors` teardown on the one rival that matters, refresh work from decay findings.

**Checkpoints at weeks 4, 8, 12:** export GSC, run `/vibe data`, adjust. Expectation honesty: content compounds on a months scale, fixes on a weeks scale; say so, and never promise rankings.

## Output contract

```markdown
# 90-day plan: {business}
Goal: {goal} · Capacity: {n} hrs/week · Start: {date}

## Week-by-week
| Week | Focus | Tasks (sized to capacity) | Executes with |

## Milestones
Week 4: ... · Week 8: ... · Week 12: ...

## The one metric
{single number matched to the goal: e.g., calls from GBP, organic sales,
striking-distance queries moved to page one}

## Your one next action
{the week-1, day-1 item}
```

## Rules

- Total weekly task time must fit inside stated capacity, with slack. When the wish list exceeds capacity, cut scope, never inflate hours. Name what was cut and why it can wait.
- Sequence by dependency: fixes before content, hubs before spokes, links immediately after publishing, data after there is data.
- One metric per plan. Dashboards are procrastination.
- Save the plan to `.vibesearch/plan.md` and append the run to `.vibesearch/log.md`. Future runs of any command may reference the current week's focus.
