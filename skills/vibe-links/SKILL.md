---
name: vibe-links
description: "VibeSearch linking engine. Maps internal links across the site to find orphan pages, equity hoarding, and under-linked money pages, then produces an exact paste-ready link insertion list (source page, sentence, target, anchor text). Also analyzes backlink exports from free sources and competitor link gaps. Use whenever the user runs /vibe links, mentions internal linking, orphan pages, link equity, anchor text, backlinks, link building, or asks why one page gets all the traffic."
---

# VibeSearch Links

Internal links are the highest-leverage SEO work nobody does, because the deliverable is usually "improve internal linking" instead of an actual list of edits. This skill produces the list of edits.

Read `.vibesearch/profile.md` first (money pages matter most here).

## `internal` (default) — the insertion list

1. **Sample the site.** Fetch the sitemap, then fetch up to 15 pages: the money pages, the highest-level hubs, and the most recent posts. If subagents are available, dispatch `vibe-page-auditor` per page in parallel. Be explicit that large sites get a sample-based map, and say which pages were sampled.
2. **Build the link map.** From each fetched page, extract internal links and anchors. Now diagnose:
   - **Orphans:** in the sitemap, but no sampled page links to them.
   - **Hoarders:** one page (usually the homepage or a single hit post) holding a wildly disproportionate share of inlinks while money pages starve. Traffic concentration on one URL is fragility, not success.
   - **Starving money pages:** the pages that make money with the fewest inlinks.
   - **Wasted anchors:** "click here", "read more", bare URLs where descriptive anchors should be.
   - **Broken hub-and-spoke:** spokes that never link to their hub, hubs that never link down.
3. **Deliver the insertion list.** The artifact is a table the user works through top to bottom:

```markdown
| # | On this page | Find this passage | Add link to | Anchor text | Why |
```

Quote a real existing sentence per row so the edit takes seconds. Ten to twenty insertions, ordered by impact (money pages and orphan rescues first). On WordPress, remind them this is a Classic editor find-and-edit job, no plugin needed.

## `backlinks` — honest mode

There is no free live backlink index, so say so, then work with what is genuinely free:

- **Get the data:** Google Search Console → Links report (top linked pages, top linking sites, export), and Bing Webmaster Tools' backlink report (free, includes some competitor comparison). The user exports or pastes; you analyze.
- **Analyze a pasted/exported list:** which pages earn links (make more like those), which money pages have none (internal links from the link-earners are the immediate fix), obviously spammy domains (with the calming truth: Google mostly ignores spam links, and disavow is rarely worth touching; do not panic-disavow).
- **Earnable targets:** fetch 2 or 3 competitor pages the user names and identify link-worthy formats they used (original data, tools, definitive guides) that the user could genuinely out-do, then hand the brief to `/vibe write`.

Never fabricate domain ratings, authority scores, or backlink counts. If the user has a paid tool export (Ahrefs, Semrush, Moz), accept and analyze it happily.

## Close every run

One next action (usually: "make insertions 1 through 5 today") and append to `.vibesearch/log.md`.
