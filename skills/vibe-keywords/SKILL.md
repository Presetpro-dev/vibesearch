---
name: vibe-keywords
description: "VibeSearch keyword research, topic clustering, and keyword-to-page mapping. Builds intent-grouped keyword maps, hub-and-spoke cluster plans, finds cannibalization (multiple pages targeting one intent), and mines striking-distance wins from pasted Search Console data. Use whenever the user runs /vibe keywords, asks what keywords to target, wants keyword research or a content plan for a topic, mentions topic clusters or hub and spoke, or asks why two of their pages compete with each other."
---

# VibeSearch Keywords

Job: turn a topic (or the user's real Search Console data) into a keyword map where every intent has exactly one target page.

Read `.vibesearch/profile.md` first. Then fetch the site's sitemap so the map lands on real URLs, not a fantasy site.

## Mode A: from a seed topic — `/vibe keywords <topic>`

1. **Expand.** Generate the query space around the topic the way real people search it: questions, comparisons ("x vs y"), best/top lists, price/cost queries, how-to, near-me and city variants if the profile is local, brand-adjacent terms. Aim for 30 to 60 candidates.
2. **Group by intent, not by string.** Every group answers one job: informational, commercial investigation, transactional, or local. Keywords that would be satisfied by the same page belong in the same group. This is the whole game: **one page per intent, never one page per keyword.**
3. **Estimate demand honestly.** Label each group High / Medium / Low relative demand based on how commonly that need is expressed. Never print invented monthly search volumes. Tell the user the two free ways to verify: their own Search Console queries, and Google Keyword Planner ranges (free with any Google Ads account).
4. **Map to the sitemap.** Assign each intent group to an existing URL or mark it NEW. Two existing URLs claiming the same intent is cannibalization: name the winner (stronger, more linked, better matched), and give the fix (consolidate and 301 the loser, or re-aim the loser at a genuinely different intent).

## Mode B: from real data — user pastes or uploads a Search Console export

Accept pasted rows or a CSV (Performance report, Queries tab). Then mine:

- **Striking distance:** queries at average position roughly 5 to 20 with meaningful impressions. These are the fastest wins on the entire site; the fix is usually a sharper title, a direct answer block, and 2 internal links, which you specify concretely per query.
- **Missing pages:** query themes with impressions but no page truly aimed at them → NEW page entries in the map.
- **Mismatches:** a page ranking for an intent it does not serve → re-aim or create the right page.

## Output (both modes)

```markdown
# Keyword map: {topic or site}
{date} · one page per intent · demand labels are relative, verify in GSC/Keyword Planner

## Cluster: {hub name}
Hub page: {existing URL or NEW: proposed slug}
| Intent group (example queries) | Intent | Demand | Target page | Status | Priority |

## Cannibalization found
{page A vs page B → winner, and the exact consolidation fix}

## Build order
{numbered: hub first or strengthen existing hub, then spokes by priority ×
effort. Each line names the command that executes it, usually /vibe write.}

## Your one next action
{one item}
```

Structure clusters hub-and-spoke: one hub page owning the broad intent, spokes owning the specific ones, and note that every spoke links to the hub and the hub links to every spoke (hand the actual insertions to `/vibe links`).

## Rules

- Never fabricate volume numbers, difficulty scores, or CPCs. Relative labels plus the free verification path.
- Cap the map at what the user can build: read capacity from the profile or ask; a 40-page map for a solo operator is a demotivation device.
- Close with the one next action and append to `.vibesearch/log.md`.
