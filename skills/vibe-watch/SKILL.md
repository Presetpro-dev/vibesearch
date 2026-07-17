---
name: vibe-watch
description: "VibeSearch drift monitoring and the loop-closer. Snapshots a page's SEO-critical elements to plain markdown now, diffs against it later, and flags what changed with severity. Also re-probes the Answer Ledger to check whether questions shipped via /vibe win actually flipped to won, and runs the citation-freshness refresh calendar. Use whenever the user runs /vibe watch, asks what changed on a page, wants to check if a shipped page won its question yet, suspects a plugin/theme/redesign broke something, wants a baseline before making changes, or asks what content needs refreshing."
---

# VibeSearch Watch

Git-style change tracking for on-page SEO, stored as human-readable markdown files you can read, edit, and commit. No database. This is also where a win gets confirmed: `/vibe win` ships an answer, `/vibe watch` is what tells you it actually landed.

Route on the argument after `watch`:

## `reprobe [question]` — did the win land?

The loop-closer. Delegates to `vibe-map reprobe`: re-runs `vibe-question-prober` on every ledger row marked "probing," or on one named question, and updates status to won, contesting, or still unowned based on today's fresh result, never from the shipped draft alone. Report only real movement. This is the natural default to run a few weeks after any `/vibe win`.

## `refresh` — the freshness calendar

Citation eligibility fades with age; content answering a question well six months ago can quietly stop being cited as newer material overtakes it. Scan `.vibesearch/ledger.md` for "won" questions whose underlying page hasn't been touched (per the sitemap's lastmod, or the most recent snapshot) in 90+ days, and flag them for a real refresh, meaning new facts, new numbers, or new proof added, never just a bumped date with no real change. Output a short prioritized list: question, page, last touched, what's likely gone stale.

## `baseline <url>` — snapshot now

Fetch the URL and write `.vibesearch/snapshots/{slug}.md` (slug from the URL path; homepage becomes `home`). If a snapshot already exists, append a new dated section; never overwrite history.

```markdown
## Snapshot: YYYY-MM-DD
- URL:
- HTTP status:
- Title: (verbatim)
- Meta description: (verbatim)
- Canonical:
- Robots meta:
- H1: (verbatim)
- Headings map: (H2/H3 text, in order)
- Schema types present: (list of @type values)
- Word count (main content, approximate):
- Internal links (count) / External links (count):
- Images missing alt (count):
- Notes: (anything unusual)
```

Confirm in one line per page. Offer to baseline the profile's money pages in the same run; if subagents are available, snapshot them in parallel with the `vibe-page-auditor` agent.

## `compare <url>` — what changed

Fetch the URL fresh, diff against the most recent snapshot section, and report only real changes:

```markdown
# Watch report: {url}
Baseline {date} → today

## Changes
🔴 {breaking: noindex appeared, canonical changed, title gone, H1 removed, schema type dropped, status not 200}
🟡 {worth a look: title/description rewritten, heading structure changed, word count moved >20%, links dropped}
🟢 {fine: minor copy edits, counts within noise}

## Verdict
{One or two sentences: nothing to worry about / fix X before it costs you.}
```

Every 🔴 comes with its paste-ready fix, same standard as `/vibe fix`: usually "restore this exact previous value", which the snapshot conveniently contains verbatim. Then append the new state as a fresh dated section so the history stays continuous.

## `history <url>` — the timeline

Read the snapshot file and summarize the dated sections as a short timeline of when each element changed.

## No argument

List existing snapshots with their last date, flag any older than 30 days as stale, and suggest `compare` on the most important one.

## The habit to teach

Baseline before every risky change (theme update, plugin update, redesign, migration), compare after. Mention this once when relevant; do not nag.

Close every run with the one next action and append to `.vibesearch/log.md`.
