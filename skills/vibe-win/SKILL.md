---
name: vibe-win
description: "VibeSearch's full turn: take one question from the ledger and win it. Tears down the current best answer, drafts a better one in the business's voice using their real proof, tests the draft against the current winner before calling it done, and produces the complete ship-kit: title, meta, schema, internal links, and image directions. Use whenever the user runs /vibe win, says yes to the coach's suggested move, asks to write or fix content for a specific question, or wants to go after a specific topic from the ledger."
---

# VibeSearch Win

One question in, one shippable, self-tested answer out. This is where the ledger's ember dots turn to amber.

Read `.vibesearch/profile.md`, `.vibesearch/entity.md`, and `.vibesearch/proof.md` first. If no question is given, read `.vibesearch/ledger.md` and use its top recommended item.

## Step 1: Confirm the target

Check the sitemap for a page that already targets this question's intent. If one exists close enough, this is an improve-in-place job on that page; otherwise it's a new page.

## Step 2: Tear down the current winner

If `vibe-question-prober` has not probed this question in the last few days, run it now. Fetch the current owner's actual page. Note plainly: what it gets right (do not pretend it's worthless, that produces weak strategy), what it's missing or thin on, and specifically whether it has anything the business's real proof can beat.

## Step 3: Draft in voice, with proof

Apply the voice and humor-dial rules from `.vibesearch/profile.md` exactly. Weave in one real detail from `.vibesearch/proof.md` if one fits; if that file is empty or nothing fits this question, ask for one concrete detail (a real number, a real photo, a first-hand fact) before writing, rather than inventing one.

Structure for citability, same standard regardless of platform: the opening paragraph answers the question completely and self-contained in 2-4 sentences (this is the passage a search result or an AI answer would lift on its own), question-phrased subheadings beneath it, specific facts carry attribution or a date. Prose first, bullets only where a true list lives. No em-dashes. Banned openers: "In today's digital landscape," "Whether you're a beginner or an expert." Banned filler: "delve," "unlock," "elevate," "game-changer."

## Step 4: Self-test before calling it done

Compare the draft's opening answer block against the current winner's from Step 2. Ask plainly: if a search engine or an AI answer had to pick one of these two passages to surface, which actually answers the question faster and more completely, with real backing? If the current winner still edges it, say so and revise. Never ship a draft that only ties.

## Step 5: The ship-kit

```markdown
# Win: {question}

{full draft}

---
## Ship-it kit
**Title tag:** {under ~60 chars}
**Meta description:** {under ~155 chars}
**URL slug:**
**Schema:** {Article / Product / LocalBusiness / FAQPage as fits, complete valid JSON-LD}
**Internal links:** {2-3 real URLs from the sitemap, with anchor text}
**Images needed:** {2-3 shot directions, specific to this piece, never stock}
```

For each image direction, once the user has the actual photo, produce the full image kit (file name, Photoshop File Info, WordPress fields) using the `vibe-images` skill's kit methodology, don't duplicate that logic here, hand off to it.

If the question is explicitly comparative ("X vs Y", "alternatives to X"), the draft follows a fairness standard: verifiable claims only, acknowledge where the alternative genuinely wins, never invent a competitor fact.

## Step 6: Mark the ledger

Update this question's row in `.vibesearch/ledger.md`: status to "probing," today's date, a note that it shipped and is awaiting re-probe. Never mark a question "won" from the draft alone, only a fresh probe earns that.

## Rules

- Never invent a statistic, a quote, or a first-hand experience. Unverifiable claims get cut.
- Never promise a ranking or a citation, promise the piece is the best available answer right now, that's the controllable part.
- Close with the one next action (usually: ship this, then run `/vibe watch` in a few weeks) and append to `.vibesearch/log.md`.
