# VibeSearch Coverage Map

VibeSearch reorganized in v0.4 from eleven discipline-based commands into seven built around one object: the Answer Ledger. Nothing was dropped, it moved.

| Old command (v0.1-v0.3) | Now lives in |
|---|---|
| vibe-setup | `/vibe start` |
| vibe-check | `/vibe fix` |
| vibe-keywords | `/vibe start` (initial question list) + `/vibe map` (ongoing) |
| vibe-write | `/vibe win` |
| vibe-images | unchanged, its own skill; called directly, or automatically by `/vibe win` and `/vibe fix` |
| vibe-links | folded into `/vibe fix` (internal-link insertion mode) |
| vibe-competitors | the teardown step inside `/vibe win` |
| vibe-local | unchanged, `/vibe local` |
| vibe-data | GSC import inside `/vibe map` |
| vibe-plan | the coach itself, bare `/vibe` |
| vibe-watch | unchanged and extended: now also re-probes the ledger and runs the refresh calendar |

## What's new in v0.4, not a port of anything

- The Answer Ledger and the honest probe methodology (`.vibesearch/ledger.md`)
- The entity dossier (`entity.md`) and proof inventory (`proof.md`)
- Sprint mode for running several questions in one sitting
- Self-testing: `/vibe win` compares its own draft against the current winner before calling it done
- The freshness/refresh calendar inside `/vibe watch`

## Still open (see ROADMAP.md)

E-commerce schema depth, international/hreflang, a dedicated satisfaction lens, deeper proof-mining prompts, the public probe widget for vibesearch.co.
