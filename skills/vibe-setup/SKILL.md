---
name: vibe-setup
description: "VibeSearch onboarding. Interviews the user for about 60 seconds and writes .vibesearch/profile.md, the memory file every other VibeSearch command reads. Use whenever the user runs /vibe setup, asks to set up or configure VibeSearch, wants to change their saved business info or brand voice, or when any VibeSearch command runs and no profile exists yet."
---

# VibeSearch Setup

Goal: produce `.vibesearch/profile.md` with the least possible effort from the user. Detect first, confirm second, ask last.

## Step 1: Detect before you ask

Ask for the website URL first (or take it from the arguments). Then fetch the homepage and try to detect on your own:

- Business name (title tag, logo alt, Organization schema)
- What they do (hero copy, meta description)
- Platform (WordPress fingerprints like `/wp-content/`, Shopify's `cdn.shopify.com`, Squarespace, Wix, Webflow, or custom)
- Whether they are local (address in footer, LocalBusiness schema, service-area language)
- Existing schema types present

Present what you found as short confirmations ("Looks like a WordPress site for a photography preset shop. Right?") rather than blank questions.

## Step 2: Ask only what you cannot detect

Keep it to at most these, in one compact message, skipping any you already know:

1. **Who do you serve, and where?** (defines local vs. national vs. global, and the audience voice)
2. **What is the goal?** One of: more traffic, more leads/calls, more sales, more AI visibility (being the cited answer in ChatGPT/AI Overviews). Pick one primary.
3. **Voice:** three adjectives, or ask them to paste a paragraph of writing they love from their own site. If they paste, extract the voice yourself.
4. **Money pages:** the 1 to 3 URLs that actually make them money.

## Step 3: Write the profile

Create `.vibesearch/profile.md` exactly in this shape:

```markdown
# VibeSearch Profile
Updated: YYYY-MM-DD

## Business
- Name:
- What it does (one sentence):
- Site:
- Platform:
- Local business: yes/no (if yes: name, address, phone exactly as they should appear everywhere)

## Audience and goal
- Who we serve:
- Where:
- Primary goal:

## Voice
- Adjectives:
- Rules: (e.g., no em-dashes, no jargon, American spelling)
- Sample sentence in-voice:

## Money pages
1.
2.
3.

## Do-not-touch
- (anything the user says never to change: brand terms, legal copy, existing rankings to protect)
```

Also create `.vibesearch/log.md` with a header line if it does not exist.

## Step 4: Close the loop

Confirm the profile in two sentences, then tell them the natural next step is `/vibe check <their homepage>` and offer to run it now.

## Rules

- Sixty seconds of their time is the budget. If they are terse, fill gaps with sensible defaults and mark them `(assumed)` in the profile so they can correct later.
- Never ask a question the homepage already answers.
- If a profile already exists, show the current values and ask what changed instead of re-interviewing from scratch.
