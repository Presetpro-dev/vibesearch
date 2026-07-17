---
name: vibe-map
description: "VibeSearch board and probe engine. Shows the current Answer Ledger (share of answers, per-question status), re-probes questions to check for movement, adds new questions (from a topic, a Search Console export, or manual input), and powers sprint mode for running several questions at once. Use whenever the user runs /vibe map, asks to see the board or the ledger, wants to add questions, mentions Search Console or GSC queries, asks for their share of answers, or wants a batch or sprint of several questions at once."
---

# VibeSearch Map

The ledger is the product. This skill is how it grows and how you read it.

Read `.vibesearch/ledger.md`, `.vibesearch/profile.md`, and `.vibesearch/entity.md` first. Probe semantics live in `skills/vibe-start/references/probe-methodology.md`; apply them exactly.

## The ledger file format (canonical, every skill reads and writes exactly this)

`.vibesearch/ledger.md` is one markdown table plus a header line:

```markdown
# Answer Ledger: {business}
Share of answers: {won}/{total} · Last full probe: {date}

| Question | Status | Owner | Probed | Note |
|---|---|---|---|---|
| how much does emergency pump repair cost | unowned | competitor.com | 2026-07-16 | outdated 2023 pricing, no urgency info |
```

Exactly four statuses, no others: **unowned** (someone else wins), **contesting** (you appear, someone else still wins), **probing** (a win shipped via /vibe win, awaiting a fresh re-probe), **won** (a dated probe confirmed you as the answer). The Note field carries why the current owner wins, or "GSC evidence" for imported queries, or ship dates.

Route on the argument after `map`:

## No argument — show the board

Render the ledger as a scannable summary: share of answers up top, then questions grouped by status, won first (it's the proof this works), then contesting, then unowned sorted oldest-probed first. Flag anything unprobed in 30+ days as stale.

## `add <topic or question>` — grow the board

Given a topic, expand it into 5-10 real question variants the way `/vibe start` does (direct, cost, comparison, urgent, local). Given a literal question, use it as-is. Confirm the additions, probe them via `vibe-question-prober` (parallel dispatch), append to the ledger with today's date.

## `import` — seed from real evidence

Accept pasted rows or a CSV from Google Search Console (Performance report, Queries tab) or Bing Webmaster. These are real questions real people already typed to find this business, the highest-confidence additions the ledger can get. For each query with meaningful impressions: check if it is already tracked; if not, add and probe it. Flag queries where the business already ranks organically but is not winning the probe, that gap is often the fastest path to "won," since the authority is half-built already.

## `reprobe` — check for movement

Re-run the prober on every question marked "probing," or the whole board if asked. Compare each result to its last recorded status. Report only real changes: newly won, newly lost, still contesting. Usually delegated from `/vibe watch` on a schedule, but runs any time on demand.

## `sprint [n]` — batch mode

For agencies, or anyone who wants more than one move a day. Select the top N unowned or contesting questions by winnability (real proof available, current owner is weak, or high real-world demand from a GSC import), default N=5. Hand each one to `vibe-win` in sequence, producing a full ship-kit per question in one run. State plainly that shipping N drafts still means N humans-worth of pasting into the CMS, the software does not publish anything on its own.

## Output contract for the board view

```markdown
# VibeSearch Board: {business}
Share of answers: {won}/{total} · Last full probe: {date}

## Won ({n})
{question} — owned since {date}

## Probing ({n}), shipped and awaiting re-probe
{question} — shipped {date} — run /vibe watch reprobe to confirm

## Contesting ({n})
{question} — you're present but {owner} still wins — {why}

## Unowned ({n}), oldest probe first
{question} — {owner} wins — {why} — probed {date}

## Your one next action
{the single best move, same logic /vibe uses}
```

## Rules

- Never fabricate a probe result; every status change requires an actual `vibe-question-prober` run carrying today's date.
- GSC-imported queries are labeled as real evidence in the note field, distinct from AI-generated question variants.
- Close every run by appending to `.vibesearch/log.md`.
