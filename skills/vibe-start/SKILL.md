---
name: vibe-start
description: "VibeSearch onboarding and first probe. One sitting: detect the business, capture voice (paste-a-paragraph or point at reference sites), build the 30-50 question list a business should be the answer to, run the first live probe across all of them, and write the four files every other command reads: profile.md, entity.md, ledger.md, proof.md. Use whenever the user runs /vibe start, asks to set up or configure VibeSearch, wants to change saved business info or voice, or when any VibeSearch command runs and no ledger exists yet."
---

# VibeSearch Start

Goal: leave this sitting with a working scoreboard, not just a filled-in form. Detect first, confirm second, ask last, probe before you're done.

## Step 1: Detect before you ask

Take the URL (from arguments or ask once). Fetch the homepage and detect: business name, what they do, platform (WordPress/Shopify/etc. fingerprints), local vs. national/global (address, LocalBusiness schema, service-area language), existing schema types. Present findings as confirmations, not blank questions.

## Step 2: Ask only what you cannot detect

In one compact message:

1. **Who do you serve, and where?**
2. **Primary goal:** more traffic, more leads/calls, more sales, or more AI visibility.
3. **Voice, either path:** paste a paragraph you love from your own writing, OR give 1-3 URLs of sites whose tone you admire. If URLs are given, fetch each and extract the pattern (sentence length, humor level, structure) rather than asking them to describe it in words.
4. **Humor dial:** ask once, apply by content type, not globally. Default: on for personality and comparison content, off for trust-and-safety or pricing content, where a joke can undercut authority. Let them override either default.
5. **Money pages:** 1-3 URLs that actually make them money.
6. **If local:** exact NAP (name, address, phone) as it should appear everywhere, and real profile links only (sameAs) for schema. Never invent a profile URL that was not given.

## Step 3: Build the question list (30-50)

This is the ledger's raw material. Generate the way real customers actually ask, not the way a marketer phrases a keyword:

- Direct service or product questions ("how do I fix a leaking pipe")
- Cost questions ("how much does X cost")
- Comparison and vs. questions if clear alternatives exist
- Urgent or emergency variants if the business has them, this is usually where local service businesses find their fastest wins
- At least one "what is / who is" question about the business itself, the name-tag question, always included
- Local modifiers (city, "near me") if local

Present the list, ask them to confirm, cut anything irrelevant, add anything missing. Do not skip confirmation even when the list looks obviously right; this is what the business runs on for months.

## Step 4: The first probe

Read `references/probe-methodology.md` before running a single probe.

Dispatch the `vibe-question-prober` agent once per question, in parallel where the environment supports it, passing the question text and the business's own domain. Collect every result before writing the ledger.

**Honesty rule, non-negotiable:** a probe is a live web-search visibility check, not a claim to have queried a specific AI product like ChatGPT or Perplexity. Every ledger row carries the date it was probed and stays labeled as a search-visibility signal, never a manufactured "AI score."

## Step 5: Write the four files

```
.vibesearch/profile.md   business, audience, goal, voice + humor dial, money pages, do-not-touch
.vibesearch/entity.md    the name-tag: one-line "who is X" answer, NAP if local, real sameAs only
.vibesearch/ledger.md    every question probed, with status/owner/date/note
.vibesearch/proof.md     inventory of real, original, citable assets; seed with anything volunteered
                          during setup, otherwise leave the template empty for them to fill in
```

Use the canonical ledger file format defined in the `vibe-map` skill (four statuses: unowned, contesting, probing, won) so every skill reads and writes it identically. Also create `.vibesearch/log.md` with a header line if it does not exist.

## Step 6: Close the loop

Report the opening score plainly: "X of Y questions already yours." Then hand off: "Type `/vibe` any time and I'll tell you the best next move." Do not dump the full board here, that is what `/vibe` and `/vibe map` are for.

## Rules

- Budget: under fifteen minutes including the probe. Terse answers get sensible defaults marked `(assumed)`, correctable later.
- Never invent a sameAs profile, a proof asset, or a probe result. If something is unknown, the file says so.
- If a ledger already exists, show current values and ask what changed rather than re-running the whole interview.
