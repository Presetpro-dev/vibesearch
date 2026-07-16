# VibeSearch

**The complete SEO toolkit for Claude. Fixes, not findings.**

VibeSearch is a free, open-source SEO toolkit for [Claude Code](https://claude.com/claude-code) covering the whole discipline: technical, on-page, schema, content, keywords, internal links, competitors, local, performance data, and strategy, built for how people search now: Google, Google Maps, AI Overviews, ChatGPT, and Perplexity.

The difference is the output contract. Audit tools hand you findings; VibeSearch hands you the fix: exact replacement text, complete JSON-LD, a link insertion list with the sentences quoted, a finished draft, a capacity-sized plan. Copy, paste, ship.

No Python. No installer script. No OAuth wizard. Two commands and you're running:

```
/plugin marketplace add Presetpro-dev/vibesearch
/plugin install vibesearch@vibesearch
```

Then:

```
/vibe setup                       # 60 seconds, makes everything smarter
/vibe check https://your-site.com # top 5 issues, every one with its fix
```

## Ten commands, the whole job

| | Command | What you get |
|---|---|---|
| Start | `/vibe setup` | A 60-second interview saved to a profile every other command reads |
| Diagnose | `/vibe check <url>` | Six-lens audit capped at 5 issues, each with a paste-ready fix |
| Target | `/vibe keywords <topic>` | Intent-grouped keyword map, hub-and-spoke clusters, cannibalization fixes |
| Create | `/vibe write <topic>` | A draft engineered to rank and be cited by AI, plus title, meta, schema, links |
| Connect | `/vibe links` | An exact internal-link insertion list; honest backlink analysis from free exports |
| Compete | `/vibe competitors` | Side-by-side teardowns on verifiable facts, gap lists, vs/alternatives pages |
| Local | `/vibe local` | GBP post calendar, review responses in your voice, service-area pages with anti-doorway guardrails, citations, schema |
| Measure | `/vibe data` | Drop in a Search Console export, get the top 10 opportunities with rewrites done |
| Plan | `/vibe plan` | A 90-day roadmap sized to your real hours, every item mapped to its command |
| Protect | `/vibe watch` | Baseline pages as plain markdown, diff after every risky change |

Full discipline-by-discipline map: [docs/COVERAGE.md](docs/COVERAGE.md).

## The philosophy

**1. Fixes, not findings.** An audit that ends in a to-do list is homework. Every issue ships with its fix in paste-ready form.

**2. One next action.** Fifty findings produce zero changes. Every run ends with exactly one recommended move. Execution is the product.

**3. Memory built in.** A `.vibesearch/` folder in your project holds your profile, run log, plan, and page snapshots as plain markdown you can read, edit, and commit. Set your voice once; every artifact sounds like you.

**4. Zero dependencies, zero setup.** The core runs on Claude Code's built-in web tools. Even performance data needs no OAuth: export your Search Console CSV (30 seconds) and drop it in. Works the same on macOS, Linux, and Windows.

**5. Honest data or no data.** Your pages and competitors' pages get fetched and verified live. Rankings, volumes, and backlinks come from data you actually own, or they don't come at all. VibeSearch never prints an invented number, and where a metric can't be known it says so and points to the free source of truth.

## The memory folder

```
your-project/
└── .vibesearch/
    ├── profile.md      # who you are, who you serve, how you sound
    ├── plan.md         # the current 90-day roadmap
    ├── log.md          # every run, dated, with the action it recommended
    └── snapshots/      # per-page baselines for /vibe watch
```

Human-readable, git-friendly, yours. Delete the folder and VibeSearch forgets everything.

## Requirements

[Claude Code](https://claude.com/claude-code). That's the list.

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md): a bring-your-own-key Google API tier, a WordPress/Yoast adapter, `/vibe pitch` client proposals, deep e-commerce and hreflang modules, optional MCP extensions. The core stays free and dependency-free forever.

## License

MIT. See [LICENSE](LICENSE). Use it, fork it, build your agency on it.

## Author

Built by **Tim Martin** ([vibesearch.co](https://vibesearch.co)), operator of [PresetPro](https://www.presetpro.com) and [FreePresets](https://www.freepresets.com), running search-led businesses for over a decade. VibeSearch is the toolkit behind that work, packaged.
