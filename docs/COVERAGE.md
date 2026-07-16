# VibeSearch Coverage Map

Every SEO discipline, where it lives in VibeSearch, and how honest the data behind it is.

**Legend:**
✅ Verified live — VibeSearch fetches your (or competitors') actual pages and works from them.
📋 Your free data — you export or paste data you already own (Search Console, Bing Webmaster, GA4); zero setup, no OAuth.
🗺️ Roadmap — planned, see docs/ROADMAP.md.

| Discipline | Where it lives | Data |
|---|---|---|
| Technical SEO (indexability, robots, canonicals, sitemaps) | `/vibe check` → Findable lens | ✅ |
| On-page SEO (titles, metas, headings, URLs) | `/vibe check` + rewrites in `/vibe data` | ✅ 📋 |
| Schema / structured data (detect, validate, generate; deprecation-aware) | `/vibe check` → Structured lens, `/vibe local schema` | ✅ |
| AI search / GEO (AI Overviews, ChatGPT, Perplexity citability) | `/vibe check` → Answerable lens, built into `/vibe write` | ✅ |
| Content quality & E-E-A-T | `/vibe check` → Trustworthy lens, enforced in `/vibe write` | ✅ |
| Content creation (posts, pages, briefs, ship-it kit) | `/vibe write` | ✅ |
| Keyword research & intent mapping | `/vibe keywords` (relative demand, honestly labeled) | ✅ 📋 |
| Topic clustering / hub-and-spoke | `/vibe keywords` → build order → `/vibe plan` | ✅ |
| Cannibalization detection & consolidation | `/vibe keywords`, `/vibe data`, sitemap pass in `/vibe check` | ✅ 📋 |
| Internal linking (orphans, equity, insertion list) | `/vibe links internal` | ✅ |
| Backlinks (analysis of GSC/Bing/paid exports, earnable targets) | `/vibe links backlinks` | 📋 |
| Competitor analysis (teardowns, gaps, vs/alternatives pages) | `/vibe competitors` | ✅ |
| Rank & performance tracking (positions, clicks, CTR, decay) | `/vibe data` on GSC exports | 📋 |
| Striking-distance optimization | `/vibe data` → paste-ready rewrites | 📋 |
| Local SEO (GBP, NAP, citations, reviews, service-area pages) | `/vibe local` | ✅ 📋 |
| Page speed & Core Web Vitals | `/vibe check` heuristics + your PageSpeed Insights link | ✅ (lab-honest) |
| Image SEO (alt, dimensions, weight, originality) | `/vibe check`, image directions in `/vibe write` | ✅ |
| E-commerce SEO (Product/Offer schema, category pages) | `/vibe check` on product pages, `/vibe write` for product copy; deep module | ✅ 🗺️ |
| Drift monitoring / regression protection | `/vibe watch` | ✅ |
| SEO strategy & prioritization | `/vibe plan` (capacity-sized 90-day roadmap) | ✅ |
| Redirects & migrations | flagged in `/vibe check`, sequenced in `/vibe plan`; dedicated flow | 🗺️ |
| International / hreflang | 🗺️ | 🗺️ |
| Programmatic SEO (with quality gates) | 🗺️ | 🗺️ |
| Client reporting / proposals (`/vibe pitch`) | 🗺️ | 🗺️ |
| Live SERP / volume / paid-index data | optional MCP extensions | 🗺️ |

## The two halves of SEO, and how VibeSearch handles each

**Half one: what can be verified by fetching pages.** Your pages, competitor pages, sitemaps, robots, schema, content, links between pages. This is roughly 70% of real SEO work, it is fully covered today, and it needs zero accounts, keys, or installs.

**Half two: what needs measurement data.** Search volume, your actual rankings and clicks, backlink indexes. No tool gets this without a data source, and tools that print these numbers without one are making them up. VibeSearch's answer: the free sources you already own (Search Console, Bing Webmaster) read via a 30-second export instead of an OAuth wizard, plus optional paid extensions later for those who have them. Where a number cannot be known, VibeSearch says so instead of inventing it. That honesty is a feature, not a gap.
