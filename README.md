# VibeSearch

**When someone asks AI about your business, does it say your name?**

VibeSearch is a free, open-source Claude Code plugin built around one idea: search is no longer ten blue links, it's an answer, and either your business is the answer or it isn't. VibeSearch keeps a scoreboard, the Answer Ledger, of the real questions your customers ask, checks who currently owns each one, and helps you win them one at a time. No dashboard, no login, no API bill: it runs on your own Claude Code, in your own project folder.

```
/plugin marketplace add Presetpro-dev/vibesearch
/plugin install vibesearch@vibesearch
```

Then:

```
/vibe start   # ~15 minutes: builds your question list and runs the first check
/vibe         # any time after: the coach tells you today's best move
```

## One coach, seven moves

| | Command | What it does |
|---|---|---|
| Coach | `/vibe` | Reads your ledger, picks today's one best move |
| Setup | `/vibe start` | Builds your 30-50 question list, runs the first live probe, writes your four files |
| Board | `/vibe map` | Shows the ledger, adds questions, imports real Search Console queries, sprint mode for several at once |
| Win | `/vibe win <question>` | Tears down the current best answer, drafts a better one in your voice, self-tests it, hands you the full ship-kit |
| Fix | `/vibe fix <url>` | Repairs an already-live page: 5 issues max, every one with its paste-ready fix |
| Images | `/vibe images` | Audits a page's images, or builds the publish kit: file name, Photoshop File Info, alt text, caption |
| Local | `/vibe local` | GBP posts, review responses, service-area pages, citations, schema |
| Watch | `/vibe watch` | Confirms whether a shipped win actually landed, flags stale content for a real refresh |

`win` and `fix` also call the images skill automatically whenever a piece needs photos.

## The philosophy

**One scoreboard, not eleven tools.** Every command reads or writes the same ledger. A month of using VibeSearch remembers what a month of using VibeSearch tried.

**Fixes and drafts, not findings.** Nothing ships without the paste-ready version attached: exact text, complete schema, exact fields.

**Probes are honest.** A probe is a live web-search visibility check, dated and labeled as exactly that, never a claim to have queried ChatGPT or any specific AI product. Where something can't be verified, VibeSearch says so instead of inventing a number.

**Self-testing.** `/vibe win` doesn't just draft, it compares its own draft against whoever currently wins the question before calling the job done.

**Command surface capped at one coach and seven moves, forever.** New disciplines become lenses inside an existing skill before they earn a new command.

**Zero dependencies, zero setup.** Runs entirely on Claude Code's built-in tools. Nothing to install beyond Claude Code itself, nothing to break.

## The memory folder

```
your-project/
└── .vibesearch/
    ├── profile.md    # business, audience, goal, voice, humor dial, money pages
    ├── entity.md     # your name-tag: the canonical "who is this" answer, NAP if local
    ├── ledger.md     # every question tracked: status, owner, last probed
    ├── proof.md      # your real, original, citable facts and numbers
    ├── log.md        # every run, dated
    └── snapshots/    # per-page baselines for /vibe watch
```

Plain markdown, human-readable, git-friendly, yours. Delete the folder and VibeSearch forgets everything.

## Requirements

[Claude Code](https://claude.com/claude-code). That's the list.

## Roadmap

See [docs/ROADMAP.md](docs/ROADMAP.md). Coverage map from the earlier discipline-based design: [docs/COVERAGE.md](docs/COVERAGE.md).

## License

MIT. See [LICENSE](LICENSE). Use it, fork it, build your agency on it.

## Author

Built by **Tim Martin** ([vibesearch.co](https://vibesearch.co)), operator of [PresetPro](https://www.presetpro.com) and [FreePresets](https://www.freepresets.com), running search-led businesses for over a decade. VibeSearch is the toolkit behind that work, packaged.

---
*VibeSearch is an independent open-source project built for Claude Code. Not affiliated with or endorsed by Anthropic.*
