---
name: vibe-check
description: "VibeSearch page and site audit that ships fixes, not findings. Checks how findable, structured, answerable, and trustworthy a page is across Google, Maps, and AI search (AI Overviews, ChatGPT, Perplexity), then hands over paste-ready fixes for the top issues only. Use whenever the user runs /vibe check, asks to audit a page or site, asks why a page is not ranking or not being cited by AI, or asks what is wrong with their SEO."
---

# VibeSearch Check

The core promise: **top 5 issues, every one with its fix, one next action.** Never a wall of findings.

## Step 0: Context

Read `.vibesearch/profile.md` if it exists (business type, platform, voice, money pages). If it does not, detect the business type from the page itself and offer `/vibe setup` at the end.

## Step 1: Gather

Using built-in web fetch (no external tools needed):

1. The target URL's full HTML
2. `robots.txt` and the XML sitemap (follow the sitemap reference in robots.txt)
3. If auditing a site rather than a single page: the homepage plus the money pages from the profile, up to 5 pages total. If subagents are available, dispatch the `vibe-page-auditor` agent per page in parallel and synthesize.

## Step 2: Score six lenses

Evaluate only what you can actually verify from the fetched sources. Each lens gets a one-word grade: **solid / needs work / broken**.

**1. Findable** (can search engines get in and understand the map?)
- Not blocked in robots.txt; no stray `noindex`; canonical present and self-referencing (or intentionally pointing elsewhere); page present in the sitemap; one H1; title and meta description present, unique, and not truncating (title roughly under 60 characters, description roughly under 155); clean URL; no obvious duplicate-content competitors on the same domain (check the sitemap for near-identical slugs, this is where cannibalization shows).

**2. Structured** (does the page describe itself in machine language?)
- JSON-LD present and valid for the page type. Match schema to reality: Organization or LocalBusiness on the home/contact pages, Article/BlogPosting on posts, Product with Offer on product pages, BreadcrumbList where a hierarchy exists.
- Flag deprecated or dead-end schema honestly: HowTo rich results are gone (September 2023), and FAQ rich results no longer show for ordinary sites. FAQPage markup can still help machines understand the page, but never promise rich results from it.
- Every gap gets a complete, valid, paste-ready JSON-LD block built from the page's real content. Never emit placeholder values without marking them `TODO`.

**3. Answerable** (would an AI engine cite this page?)
- Headings phrased as the questions people actually ask, with a direct, self-contained answer in the first one or two sentences beneath each. A reader (or model) landing on that passage alone should get a complete answer.
- Clear entity statements: the page says plainly who/what the subject is ("X is a ...") rather than assuming context.
- Facts carry attribution (dates, sources, first-hand experience markers). Vague claims get cut or sourced.
- Content is extractable: real HTML text, not text baked into images or loaded only after interaction.

**4. Trustworthy** (E-E-A-T signals a rater or a model can see)
- Author or business identity visible; contact route findable within one click; HTTPS; dates on time-sensitive content; first-hand experience evident (original photos, real numbers, specifics only a practitioner would know). Thin, generic, could-be-anyone content gets called out as the ranking risk it is.

**5. Fast enough** (honest heuristics only)
- From HTML alone you can spot: uncompressed or oversized images, missing lazy-loading, render-blocking third-party scripts, no image dimensions (layout shift), heavy embeds above the fold (iframes especially: recommend the thumbnail-that-links-out pattern).
- Be honest: real Core Web Vitals (LCP, INP, CLS) need field data. Give the user their exact PageSpeed Insights URL (`https://pagespeed.web.dev/analysis?url=...`) rather than inventing scores.

**6. Local** (only when the profile or page says local)
- Name, address, phone visible in crawlable HTML and matching the profile exactly; LocalBusiness schema with address, geo, opening hours; a Google Business Profile link present; city/service-area language in titles and H1s where natural. Deeper local work routes to `/vibe local`.

## Step 3: Report

Output exactly this structure:

```markdown
# VibeSearch Check: {url}
{date} · Business type: {type} · Platform: {platform}

## Scoreboard
Findable {grade} · Structured {grade} · Answerable {grade} · Trustworthy {grade} · Fast enough {grade} [· Local {grade}]

## Top issues (max 5)

### 1. {Plain-language issue name} — {lens}
**Why it matters:** one or two sentences, concrete consequence.
**The fix (paste-ready):**
{exact replacement text / complete JSON-LD / exact lines, in a code block}
**Where it goes:** {platform-specific: the Yoast title field, theme.liquid, the <head>, etc.}

... (repeat, hard cap 5)

## Parked for later
{One line each for anything real but lower priority. No fixes here, just names.}

## Your one next action
{Exactly one item. The single highest-leverage move. Usually issue #1.}
```

## Priority order when choosing the top 5

1. Anything blocking indexing (robots, noindex, canonical mistakes) always wins.
2. Then whatever most directly affects the profile's stated goal (leads → trust and local; AI visibility → answerable; sales → product schema and money-page issues).
3. Then everything else by effort-to-impact.

## Platform-aware fixes

If the profile says WordPress: reference the actual fields (Yoast SEO title/description fields, category pages, media library alt text) and give shortcode/HTML the user can paste into the Classic editor. Shopify: theme.liquid and product templates. Unknown: plain HTML with a note on where the `<head>` lives.

## Rules

- Never fabricate data you did not fetch. No invented traffic numbers, no invented rankings, no invented Lighthouse scores.
- Never recommend deprecated schema for rich results.
- Five issues maximum. If you found twelve, the other seven go under "Parked for later" as names only. Overwhelm kills execution, and execution is the product.
- Close by appending the run to `.vibesearch/log.md`.
