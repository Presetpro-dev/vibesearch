---
name: vibe-fix
description: "VibeSearch repair shop for pages that already exist. Six-lens audit (findable, structured, answerable, trustworthy, fast enough, local) capped at the top 5 issues, every one with a paste-ready fix, plus an internal-link insertion mode. Use whenever the user runs /vibe fix, asks to audit or fix a page or site, asks why a page is not ranking or not being cited, wants an internal linking pass, or asks what is wrong with an existing page."
---

# VibeSearch Fix

Winning new ground is `/vibe win`. This is for what's already live and underperforming: top 5 issues, every one with its fix, one next action.

Read `.vibesearch/profile.md` and `.vibesearch/entity.md` if they exist.

## Step 1: Gather

Fetch the target URL's HTML, robots.txt, and sitemap. For a site-wide pass, dispatch `vibe-page-auditor` per page in parallel, up to 5 pages (money pages from the profile plus the homepage).

## Step 2: Grade six lenses

Each gets solid / needs work / broken, using only what was actually fetched.

**Findable:** not blocked in robots.txt, no stray noindex, self-referencing canonical, present in sitemap, one H1, unique title/description within length, clean URL, no cannibalizing near-duplicate slugs.

**Structured:** valid JSON-LD matched to page type; flag deprecated schema honestly (HowTo rich results gone since September 2023, FAQ rich results retired for all sites; FAQPage/QAPage still helps machine parsing, never promise rich results from it).

**Answerable:** question-phrased headings with a complete, self-contained answer in the first sentences beneath; clear entity statements; extractable real HTML text, not text locked in images or behind interaction.

**Trustworthy:** apply the Who/How/Why test plainly: who created this (visible byline, credentials where readers would expect them), how was it created (first-hand evidence, not generic filler), why does it exist (to help the reader, not to hit a word count or chase a click). Weak on all three is a real ranking risk, say so directly. Contact route findable within one click, HTTPS, dates visible.

**Fast enough:** honest HTML-only heuristics, oversized or undersized images, missing dimensions, heavy above-fold embeds. Below-fold images missing lazy-loading is a real flag, but check the lazy-loading signal properly first: `loading="lazy"` is one path, but data-attribute patterns (`data-src`, `data-lazy-src`, `data-original`) plus a `lazy`/`lazyload` class indicate a JS-based lazy-loader, common on WordPress via plugins, that intentionally omits the native attribute. Only flag "not lazy-loaded" when neither signal is present; flagging a JS-lazy-loaded image as broken is a false positive. Give the user their PageSpeed Insights URL for real field data rather than inventing a score.

**Local:** only when the profile or page says local. NAP visible and matching `.vibesearch/entity.md` exactly, LocalBusiness schema, GBP link present. Deeper local work routes to `/vibe local`.

## Step 3: Internal links (on request, or when a lens finds a starving money page)

Sample up to 15 pages (sitemap plus recent posts), extract internal links and anchors, find orphan pages, one page hoarding disproportionate inlinks, starving money pages, wasted anchor text. Produce a table: page, the exact existing sentence to edit, the link to add, the anchor text. Quote a real sentence per row so the edit takes seconds.

## Step 4: Images

If image issues are found, don't duplicate the full analysis here: name the count and severity, then hand off to the `vibe-images` skill's audit mode for the detailed per-image breakdown and fixes.

## Report

```markdown
# VibeSearch Fix: {url}
{date} · Findable {grade} · Structured {grade} · Answerable {grade} · Trustworthy {grade} · Fast enough {grade} [· Local {grade}]

## Top issues (max 5)
### 1. {issue} — {lens}
**Why it matters:**
**The fix (paste-ready):**
**Where it goes:** {platform-specific field/file}

## Parked for later
{names only, no fixes}

## Your one next action
```

## Rules

- Never fabricate data not actually fetched. Five issues maximum, no exceptions.
- Never recommend deprecated schema for rich results.
- Close by appending the run to `.vibesearch/log.md`.
