---
name: vibe-write
description: "VibeSearch content drafting. Writes pages and posts engineered to rank in Google AND be cited by AI search engines (AI Overviews, ChatGPT, Perplexity), in the user's saved brand voice, with metadata and schema included. Use whenever the user runs /vibe write, asks to write or draft a blog post, article, landing page, or product description with search in mind, or asks how to get their content cited by AI."
---

# VibeSearch Write

One command in, one shippable package out: the draft, the metadata, the schema, the internal links. Written like a person, structured for machines.

## Step 1: Context

Read `.vibesearch/profile.md` (voice, audience, platform, goal, money pages). Then fetch the site's sitemap and skim existing titles so the new piece links into the site instead of floating alone, and so you never write a near-duplicate of something that already exists. If a close overlap exists, say so and propose strengthening that page instead; duplicate topics split ranking power.

## Step 2: Shape before words

Confirm in one short message: the working title, the one search intent it serves (a person types/asks what, expecting what?), the 4 to 7 question-phrased H2s, and target length. Length matches intent: a pricing question wants 600 focused words, a definitive guide wants 2,000+. Never pad to hit a number. Wait for a nod, then write.

## Step 3: Write to the dual standard

**For the human reader (this is also what quality raters and ranking systems reward):**
- The profile voice, consistently.
- First-hand experience on the page: real numbers, real examples, details only a practitioner would know. If the profile or the user's own words contain experience, weave it in; if not, ask for one concrete anecdote or data point before writing. This single element separates content that ranks from content that gets skipped.
- Specifics over filler. Every paragraph earns its place.

**For the machines (Google and AI engines both):**
- Each H2 is a question people actually ask; the first one or two sentences beneath it answer it completely and self-containedly. A model quoting just that passage gives a correct, attributed answer.
- The opening paragraph of the piece states plainly what/who the subject is before elaborating.
- Claims carry sources or dates. Time-sensitive facts get a visible "as of" anchor.
- Real HTML text, descriptive subheads, no walls: content a parser extracts cleanly.

**Humanize defaults (always on unless the profile overrides):**
- No em-dashes. Use commas, colons, or split the sentence.
- Vary sentence length; read one paragraph aloud in your head before keeping it.
- Banned openers: "In today's digital landscape", "In the ever-evolving world of", "Whether you're a beginner or an expert". Banned filler: "delve", "unlock", "elevate", "game-changer".
- Prose first. Bullets only where a true list lives (specs, steps).

## Step 4: Deliver the package

```markdown
# {Title}

{full draft}

---
## Ship-it kit
**Title tag:** {under ~60 chars}
**Meta description:** {under ~155 chars, the answer plus the hook}
**URL slug:** {short, words a searcher would use}
**Schema:** {complete Article/BlogPosting JSON-LD with headline, author from profile, datePublished, and image marked TODO if unknown}
**Internal links:** {2 or 3 real URLs from the sitemap with suggested anchor text}
**Image directions:** {2 or 3 originals to create, with descriptive file names and alt text. Original beats stock for experience signals.}
```

Platform note: on WordPress, label the title and description as the Yoast fields and offer the draft as paste-ready Classic editor HTML on request.

## Rules

- Never invent statistics, quotes, or experiences. Unverifiable claims get cut or replaced with the user's real material.
- Never promise rankings. Promise the piece is the best available answer to its question; that is the controllable part.
- One piece per intent. If the user asks for one post targeting five unrelated keywords, split it and say why.
- Close with the one next action (usually: publish, then add the 2 internal links pointing TO this piece from existing pages) and append to `.vibesearch/log.md`.
