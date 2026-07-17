---
name: vibe-local
description: "VibeSearch local search execution engine. Produces the actual local SEO work: a 30-day Google Business Profile post calendar, review responses in the owner's voice, service-area pages with anti-doorway guardrails, a citation audit checklist, and LocalBusiness JSON-LD. Use whenever the user runs /vibe local, mentions Google Business Profile or GBP, Google Maps ranking, the map pack, local citations, review responses, service-area or city pages, or being found by nearby customers."
---

# VibeSearch Local

Audit tools tell local businesses what is wrong. This skill does the work. Every subcommand ends in a shippable artifact.

Read `.vibesearch/profile.md` (voice, goal) and `.vibesearch/entity.md` (the canonical NAP) first. The exact business name, address, and phone in `entity.md` are canon: every artifact uses them character-for-character. If neither file exists, collect NAP before anything else, then offer `/vibe start` at the end.

Route on the argument after `local`:

## `posts` — 30-day Google Business Profile calendar

Ask only for what the profile lacks: current offers or seasonal angle, and 2 or 3 photos they could realistically take this month.

Produce a 30-day calendar, 2 to 3 posts per week (8 to 12 total), as a table: date, post type (update, offer, event), the full post text ready to paste (under 1,500 characters, front-load the point in the first 100 since that is what shows before the fold), photo direction (what to shoot, not stock), and the call-to-action button to pick. Rotate angles: proof of work (before/after, job stories), answers to real customer questions, offers, community/seasonal. Voice comes from the profile. No hashtag spam, no fake urgency.

## `reviews` — response drafts in the owner's voice

Ask the user to paste the reviews (text and star rating). For each, draft a response:

- **5 and 4 stars:** thank them by name, mention one specific detail from their review (proof a human read it), naturally include the service and city once if it fits without sounding stuffed, invite them back. Two to four sentences.
- **3 stars and below:** acknowledge the specific complaint without legalistic defensiveness, state one concrete thing you are doing about it, move the resolution offline with a real contact route. Never argue, never offer incentives for changing the review (against Google policy), never reveal customer details the reviewer did not share themselves.

Output all responses in one block, labeled, ready to paste into the GBP dashboard.

## `pages` — service-area pages with anti-doorway guardrails

This is where local SEO goes wrong most often, so the guardrails are non-negotiable:

- **Every page must contain at least 3 location-specific proof elements** the business actually has: jobs completed there, photos taken there, local landmarks or neighborhoods served, area-specific pricing or logistics, reviews from customers in that place. If the user cannot supply real local proof for a location, refuse to generate that page and say why: without proof it is a doorway page, and doorway pages are a documented spam violation that risks the whole site.
- **Warn at 10 locations. Stop and talk it through at 25.**
- Never generate two pages that differ only by the city name.

For each approved location, produce: full page copy in the profile voice (unique intro, the proof elements woven in, a short area-specific FAQ), title tag and meta description, one H1, LocalBusiness or Service JSON-LD scoped to that area, and 2 internal-link suggestions. Read `references/service-page-blueprint.md` for the section-by-section structure before writing.

## `citations` — NAP consistency kit

Produce two artifacts: (1) the canonical NAP block from `entity.md`, formatted exactly as it must appear everywhere, plus common wrong variants to hunt down (old address, tracking numbers, Ste vs Suite); (2) a prioritized checklist of the core citation surfaces to verify by hand: Google Business Profile, Apple Business Connect, Bing Places, Facebook, Yelp, then the user's industry and country directories (ask which country; for Canada include Yellow Pages Canada and 411.ca). Be honest that submission is manual work or a paid service; the kit makes it a checklist instead of a project.

## `schema` — LocalBusiness JSON-LD

Fetch the site's contact or home page, then emit one complete, valid JSON-LD block: the most specific applicable LocalBusiness subtype (Electrician, Photographer, Restaurant, and so on), name, address, phone, geo coordinates, URL, opening hours, areaServed, sameAs for real social profiles, and image. Only include aggregateRating if genuine on-page reviews exist. Mark anything unknown `TODO` rather than inventing it. Tell the user exactly where to paste it for their platform.

## No argument after `local`

Show the five subcommands with one line each, then recommend one based on the profile goal (leads and calls → start with `schema` then `posts`).

## Close every run

One next action, and append to `.vibesearch/log.md`.
