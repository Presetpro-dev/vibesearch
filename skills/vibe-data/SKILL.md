---
name: vibe-data
description: "VibeSearch performance data analysis with zero setup: reads Google Search Console exports (pasted rows or CSV files) and turns them into prioritized, paste-ready fixes: striking-distance title rewrites, CTR-gap fixes, decaying pages to refresh, indexing red flags. No OAuth, no API keys, no credential wizard. Use whenever the user runs /vibe data, mentions Search Console, GSC, impressions, clicks, average position, CTR, traffic drops, or uploads/pastes any search performance export."
---

# VibeSearch Data

The most valuable SEO dataset in the world is free and already belongs to the user: their Search Console. Other tools gate it behind OAuth credential wizards. VibeSearch reads the export.

Read `.vibesearch/profile.md` first (the goal decides what "opportunity" means).

## Getting the data (teach this in one breath)

Search Console → Performance → set the date range (last 3 months is the default ask) → Export → CSV. That download contains Queries and Pages tables. Paste rows into chat or attach the file. That is the entire setup.

If they can also export a comparison range (e.g., last 3 months vs previous 3 months), decay analysis unlocks. If they have a GA4 landing-page export with conversions, revenue-weighting unlocks. Both optional.

## The analyses (run all that the data supports)

**1. Striking distance (the money list).** Queries at average position roughly 5 to 20, sorted by impressions. Page one is within reach; the last meters are usually on-page. For each of the top opportunities deliver the actual fix: the rewritten title tag (under ~60 chars, the query's intent front and center), the rewritten meta description, the direct answer block to add near the top of the page, and 2 internal links to point at it (hand exact insertions to `/vibe links` if a big job).

**2. CTR gaps.** Pages with strong impressions whose CTR is clearly below what their position should earn: the listing is being seen and skipped. Fix is the title/meta rewrite, delivered, plus a check for a missing date or weak brand cue.

**3. Decay.** With two ranges: pages whose clicks fell meaningfully → the refresh list, each with the likely cause (outdated facts, lost freshness, a competitor moved) and the refresh move. Route big rewrites to `/vibe write`.

**4. Mismatch and cannibalization.** Queries where the ranking page is the wrong page for the intent, or where two URLs alternate. Fix: re-aim, consolidate, or sharpen the right page (coordinate with `/vibe keywords`).

**5. Red flags.** Money pages (from the profile) with near-zero impressions: that is an indexing or relevance problem, not a content problem → send to `/vibe check` for that URL.

## Output contract

```markdown
# Data report: {site}
Range: {dates} · Rows analyzed: {n}

## Top opportunities (max 10)
### 1. "{query}" — pos {x}, {n} impressions — {page}
**The fix (paste-ready):** {title / meta / answer block / links}
...

## Refresh list  |  ## Red flags
{short tables}

## Your one next action
{one item, usually opportunity #1}
```

Ten opportunities maximum. The rest exist; they are not the point. Ship the ten.

## Rules

- Zero-setup is the feature: never require OAuth, service accounts, or API keys. (An optional bring-your-own-key PageSpeed/GSC API tier is on the roadmap for automation; it will never be the default.)
- Analyze only rows actually provided. State the date range on every report. No extrapolated traffic claims.
- Append the run to `.vibesearch/log.md`.
