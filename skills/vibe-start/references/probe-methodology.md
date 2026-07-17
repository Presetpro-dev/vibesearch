# Probe Methodology

What a "probe" is, and is not, stated once here so every skill applies it identically.

## What it is

A live web search for the question as a real person would ask it, read for who currently surfaces as the best answer. This is a genuine, defensible signal: search visibility draws on the same authority, structure, and freshness signals that AI answer engines weigh when deciding what to cite, even though it is not a direct readout of any one AI product's answer.

## What it is not

Not a transcript of ChatGPT, Perplexity, or Google's AI Overview. VibeSearch has no special access to those products' outputs. Never phrase a result as "ChatGPT said..." or "the AI recommended...". Phrase it as "the search-visibility check for this question currently surfaces...".

## What every probe result carries

- The question, verbatim
- Status: won / contesting / unowned
- Current owner (a real domain that actually appeared, or "you")
- One concrete line on why the current owner wins
- The date probed

## Re-probing

A question only moves from "probing" to "won," or stays "unowned," on a fresh probe carrying today's date. Never assume a win from a shipped draft alone; the ledger only updates on a verified re-probe result, via `/vibe watch` or `/vibe map reprobe`.

## When results are thin

If a question returns no coherent picture (too obscure, thin search results, or a malformed question), say so plainly in the ledger note rather than forcing a verdict.
