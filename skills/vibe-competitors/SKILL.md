---
name: vibe-competitors
description: "VibeSearch competitor analysis. Fetches the user's page and the competitors' pages competing for the same search intent, tears them down side by side on verifiable facts (structure, depth, schema, answerability, proof), and produces the gap list plus a brief to win. Also builds legitimate comparison and alternatives pages. Use whenever the user runs /vibe competitors, asks why a competitor outranks them, wants a competitor teardown or gap analysis, or wants an 'X vs Y' or 'alternatives to X' page."
---

# VibeSearch Competitors

Everything here is built on pages actually fetched, never on invented metrics. Competitor pages are public; that is the data source.

Read `.vibesearch/profile.md` first.

## `teardown` (default) — `/vibe competitors <your-url> vs <their-url> [<their-url-2>]`

If the user only names a competitor domain, ask which of their pages competes for the same intent as which of yours, or find the closest match by fetching their sitemap. Compare pages that target the same search intent; comparing a homepage to a blog post tells you nothing.

Fetch every page (parallel `vibe-page-auditor` dispatch when available), then compare on verifiable axes only:

| Axis | What to look at |
|---|---|
| Intent match | Whose page answers the searcher's actual question faster and more completely |
| Depth | Coverage of subtopics (headings map), not raw word count worship |
| Answerability | Question headings, self-contained answer blocks, extractable HTML: who would an AI engine cite |
| Proof | First-hand experience, original images, real numbers, named authors, dates |
| Structure | Title/H1 quality, scannability, internal links into and out of the page |
| Schema | Types present, valid, matched to the page |
| Freshness | Visible dates, currency of facts |

Output: the side-by-side table, then **Gaps you can close (max 5)**, each with the concrete move and effort level, then the win condition in one sentence ("their page wins on original data; yours wins the moment you publish your own numbers"). If the right move is new or rewritten content, end by offering the ready-made brief to `/vibe write`.

**Never do:** invent their traffic, rankings, domain authority, or revenue. If asked, name the honest sources (their public pages, GSC for your own side, paid tools for theirs) instead of guessing.

## `page` — comparison and alternatives pages

The "X vs Y" and "alternatives to X" formats are legitimate and high-converting when honest. Build:

- **Fairness first.** Every claim about a competitor must be verifiable from their public pages or marked as opinion. False claims about competitors are a legal and trust risk; accuracy is also what makes these pages rank and get cited.
- Structure: a real answer in the first paragraph (who each option is actually for), an honest feature/price comparison table from fetched facts, where the competitor genuinely wins (yes, include it: it is what makes the page credible), where you win, and who should choose which. FAQ block with the questions buyers actually ask.
- Ship-it kit as in `/vibe write`: title, meta, slug, Article JSON-LD, internal links.

## Close every run

One next action and append to `.vibesearch/log.md`.
