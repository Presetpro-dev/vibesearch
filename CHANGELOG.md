# Changelog

## 0.4.0 (unreleased)

Complete redesign around one object: the Answer Ledger.

- New core model: `.vibesearch/ledger.md` tracks the real questions a business should be the answer to (status: won/contesting/unowned, owner, last probed)
- New: `entity.md` (the name-tag dossier) and `proof.md` (real, original, citable facts) join profile.md as core memory
- New `vibe-question-prober` agent: live web-search visibility probing, dispatched in parallel across a question batch
- Command surface collapses from 11 to one coach plus seven moves: `/vibe` (the coach), `start`, `map`, `win`, `fix`, `images`, `local`, `watch`
- `/vibe start`: onboarding now includes reference-site tone extraction, a per-content-type humor dial, the 30-50 question build, and the first live probe
- `/vibe map`: the board view, question adding, GSC-export import as real evidence, reprobe, and `sprint [n]` batch mode for agencies
- `/vibe win`: the full turn — tears down the current winner, drafts in voice with proof, self-tests the draft against the incumbent before shipping, full ship-kit including delegated image kit
- `/vibe fix`: renamed and extended from vibe-check — same six-lens audit and 5-issue cap, adds a lazy-load false-positive guard (JS lazy-loader detection) and an internal-link insertion mode
- `/vibe watch`: extended with `reprobe` (closes the win-then-verify loop) and `refresh` (a citation-freshness calendar)
- Retired as standalone commands (absorbed, not lost — see docs/COVERAGE.md for the full mapping): vibe-setup, vibe-check, vibe-keywords, vibe-write, vibe-links, vibe-competitors, vibe-data, vibe-plan
- Every probe result is explicitly labeled as a live search-visibility check, never a claim to have queried a specific AI chat product

## 0.3.0

- New: `vibe-images` — two modes: `audit <url>` grades every image on a live page (alt quality, file names, dimensions, lazy loading, originality) with paste-ready fixes; `kit` produces the complete publish-ready metadata package per image: SEO file name, Photoshop File Info (IPTC title, description, keywords), and WordPress media fields (alt, title, caption, description), platform-aware
- Router, README, manifests, and coverage map updated to eleven commands

## 0.2.0

Full SEO coverage. VibeSearch spans the whole discipline; see docs/COVERAGE.md.

- New: `vibe-keywords`, `vibe-links`, `vibe-competitors`, `vibe-data`, `vibe-plan`
- New: docs/COVERAGE.md
- Router: ten commands, state-aware recommendation on bare /vibe
- Manifests bumped to 0.2.0

## 0.1.0

Initial scaffold.

- `/vibe` command with first-run onboarding and routing
- `vibe-setup`, `vibe-check`, `vibe-local`, `vibe-write`, `vibe-watch`
- `vibe-page-auditor` agent for parallel multi-page runs
- `.vibesearch/` plain-markdown memory (profile, log, snapshots)
