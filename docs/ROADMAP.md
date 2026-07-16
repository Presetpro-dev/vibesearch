# Roadmap

The core promise never changes: free, MIT, zero dependencies, fixes not findings, no invented numbers.

## v0.3 candidates
- **Google data tier (optional, bring-your-own key):** PageSpeed Insights API for real field CWV, Search Console API for automated pulls. CSV export stays the default; keys are for people who want automation.
- **WordPress adapter:** fixes output as exact Yoast field values and Classic editor HTML; detect WooCommerce/Flatsome and adapt shortcodes.
- **/vibe pitch:** turn a check or data run into a client-ready one-page proposal with scope and pricing slots (for freelancers and agencies selling the work).

## v0.4 candidates
- **E-commerce deep module:** full Product/Offer/merchant validation, category page strategy, marketplace intelligence.
- **Migrations & redirects flow:** pre-migration baseline (via /vibe watch), redirect map generation, post-launch diff.
- **International/hreflang module** with generation and validation.
- **Programmatic SEO** with hard quality gates (unique data per page or no page).
- **Optional MCP extensions:** DataForSEO, Ahrefs, Firecrawl for those who have them; never required.
- **Snapshot scheduling recipes:** cron/CI examples running /vibe watch compare weekly.

## Principles for accepting features
1. Does it end in something shippable?
2. Does it work with zero setup for the default user?
3. Does it survive the 5-issue / one-next-action philosophy, or is it a dashboard in disguise?
4. Would it require inventing a number? Then it waits for a real data source.
