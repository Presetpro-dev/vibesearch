---
name: vibe-images
description: "VibeSearch image SEO. Two jobs: audit every image on a page (alt text, file names, dimensions, weight, lazy loading, originality) and generate the complete publish-ready metadata kit for images before upload: SEO file name, Photoshop File Info fields (title, description, keywords), and WordPress media fields (alt text, title, caption, description). Use whenever the user runs /vibe images, asks about image SEO, alt text, image metadata or keywords, image file names, Photoshop File Info, WordPress media library fields, Google Images traffic, or preparing photos for upload."
---

# VibeSearch Images

Images are the most skipped SEO work on the web because the metadata lives in three different places and nobody remembers all the fields. This skill covers both directions: diagnose what is wrong on a live page, and produce the complete kit for images about to be published.

Read `.vibesearch/profile.md` first (platform, voice, and business context shape every field).

Route on the argument after `images`:

## `audit <url>` — what is wrong with the images on this page

Fetch the page and inventory every image, then grade against:

- **Missing or empty alt text** on content images (accessibility and ranking signal both).
- **Useless alt text:** "image of...", "picture of...", keyword-stuffed strings, the same alt repeated across different images, or a file name pasted into the field.
- **Camera file names:** IMG_4got.jpg, DSC_0231.jpg, screenshot-2026.png. Search engines read file names; these say nothing.
- **Missing width and height attributes** (causes layout shift while loading).
- **No lazy loading** on below-the-fold images, or lazy loading applied to the hero (delays the largest paint).
- **Weight red flags:** obviously oversized sources scaled down in HTML, PNGs doing a photograph's job, no modern format in sight.
- **Meaningful text baked into images** with no HTML equivalent (invisible to search and assistive tech).
- **Decorative images with descriptive alt** (should be empty alt, `alt=""`, so screen readers skip them).
- **Originality:** a page of recognizable stock photography where original photos should carry the experience signal.

Output the standard contract: a short inventory table, then the **top 5 fixes** with the rewritten alt text or corrected attribute paste-ready per image, then **Your one next action**. Note honestly that true file-size and format data needs the network panel or PageSpeed Insights; flag only what the HTML proves.

## `kit` — the publish-ready metadata package

For images about to be uploaded. Ask the user to describe each image (or paste the context: what it shows, what page or post it belongs to, the subject or product). Batch input is welcome; output becomes a table.

For EACH image, produce all four layers in publish order:

**1. File name (set before upload; renaming after upload is a mess on most platforms)**
Descriptive, hyphenated, lowercase, the real subject plus one natural keyword: `kodak-portra-400-film-preset-portrait.jpg`. Never spaces, never underscores, never IMG_ anything.

**2. Photoshop File Info (File > File Info, travels inside the file as IPTC metadata)**
- **Document Title:** the image's name as a human phrase.
- **Description:** one or two natural sentences describing the image and its context.
- **Keywords:** 10 to 15, comma-separated, from specific to general (subject, style, technique, brand terms where true).
This metadata stays embedded when the file is downloaded, shared, or re-uploaded elsewhere: it keeps working for you off-site.

**3. WordPress Media Library fields (after upload)**
- **Alt text:** the one that matters most. Describe the image for someone who cannot see it, in natural language, one keyword where it genuinely fits, roughly under 125 characters. Never stuff, never repeat the caption.
- **Title:** the human-readable name (defaults from the file name; clean it).
- **Caption:** visible to readers under the image, so write it for them, in the profile voice. Optional; omit where it adds nothing.
- **Description:** fuller context for the attachment page; one short paragraph.

**4. Placement note**
One line on where the image supports the page (near which heading, as featured image, in the gallery) and a reminder to set width/height or let the theme handle it.

Adapt layer 3 to the profile's platform: Shopify calls alt text "image alt text" per image, Squarespace uses captions-as-alt in some blocks; name the actual fields for their platform.

## Rules

- Alt text describes what the image actually shows. If the honest description and the keyword conflict, the description wins.
- Decorative images get empty alt, not filler.
- Original photos beat stock, always; say so when the audit finds a stock wall, because originality is an experience signal a competitor cannot copy.
- Never invent what an image contains. If the user has not described it and the page does not make it clear, ask.
- Close every run with **Your one next action** and append to `.vibesearch/log.md`.
