<h1 align="center">Stock Trading Wisdom Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

A ready-to-use AI skill toolkit — it distills the human-nature-and-probability trading decision system of *The Wisdom of Stock Trading* (《炒股的智慧》) into 14 capability cards that can each be triggered on their own or composed together. Seven of them are promoted to standalone skills; the other seven are loaded on demand through a source router entry.

It is not a summary of the book and not a reading response. It breaks the book's reusable methodology into skill modules that can be triggered, executed and tested.

## What these skills solve

- A position pulls back for a few days and paper profit shrinks — normal pullback or distribution signal? Sell or hold?
- Price breaks out on volume and you want to chase, but you cannot state the entry trigger, the stop price, or the price at which the trade is void
- After a profit you do not know which level to raise the stop to, so "let profits run" turns into "let profits turn into losses"
- Position sizing, averaging down, margin leverage — decided by feel, and one oversized bet wipes out ten small wins
- You keep picking stocks while the broad market is bad; or the index rises while your stock does not, and you suspect the index is lying
- You know the discipline but cannot pull the stop, take profits too early, refuse to sell at a loss, and after a loss only say "next time I'll be careful"

## What was distilled

14 capability cards, organised as "locate the position first, then decide entry and exit, then manage money and yourself". Slugs map one-to-one to `bundle/verified.yaml`:

- **Entry and location**: `critical-point-buy-skill` (critical-point entry decisions, critical)
- **Holding and exit**: `motion-normality-skill` (is the move normal, critical), `sell-trailing-stop-skill` (exit rules and trailing stops, critical)
- **Money and risk**: `money-management-skill` (position sizing rules, critical)
- **Stock selection and market**: `stock-picking-skill` (three-step screening, high), `market-regime-skill` (broad-market checklist, high), `bubble-mania-skill` (mania identification, high)
- **Cards served through the router entry** (router, 7 cards): `cycle-phase` (four-stage cycle, medium), `psych-discipline` (discipline checklist, high), `stage-selftest` (learning-stage self-test, medium), `manipulation-signs` (operator footprints, medium), `return-allocation` (realistic return and allocation, medium), `ma250-system` (250-day MA minimal system, high), `fundamental-check` (quick fundamentals, medium)

7 promoted + 7 routed = 14 cards, matching the 14 files in `bundle/cards/` and the 14 capabilities in `bundle/verified.yaml`.

## Two packaging modes: single and pack

The same 14 cards are compiled twice at different granularity. The content is identical; the only difference is how many entry points an agent can see.

| | single (one entry) | pack (compact pack, many entries) |
|---|---|---|
| Discoverable entries | **1**: `stock-trading-wisdom-skill` | **8**: 1 source router + 7 promoted standalone skills |
| Where the 14 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time per the routing table | The 7 promoted cards are standalone skills; the other 7 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching, then the routing table dispatches | 7 high-frequency capabilities are matched directly by their own description, one hop fewer |
| Upgrading | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in pack:

- `motion-normality-skill` — is the move normal
- `critical-point-buy-skill` — critical-point entry decisions
- `sell-trailing-stop-skill` — exit rules and trailing stops
- `money-management-skill` — position sizing rules
- `stock-picking-skill` — three-step screening
- `market-regime-skill` — broad-market checklist
- `bubble-mania-skill` — mania identification

### Which one to install

Pick by how you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 entry, no capability missing |
| Your daily questions cluster around "hold or sell / can I chase / where is the stop / how much to buy / what to buy / how is the market / is this a bubble" | pack | Those 7 are exactly the promoted skills, matched directly |
| You distribute to several agents or a team that each need a subset | pack | Install only the standalone skills you need, not the whole pack |
| You want to install once and not maintain many directories | single | Upgrading means replacing 1 directory |

> Both variants are compiled from the same Bundle and hold the same capability content. **Installing both will double-trigger** — please install only one.

## Examples

### Example 1: a 10% pullback after a rally — normal pullback or distribution?

**User question**

"I hold this stock; it ran from 20 to 27, pulled back to 24 in the last few days, and volume is less than half of what it was during the rally. Is this a normal pullback or distribution? Should I sell half?"

**How the skill decides**

- The entry dispatches by its routing table: this is a position health check, so it enters `motion-normality-skill`
- Four dimensions checked one by one: trend line (peaks rise 20→21→22→27 and the 24 pullback has not broken the prior trough), support/resistance (price has not fallen back below the last breakout point), breakout confirmation, moving average (price above the 200-day line)
- Volume check: advances on expanding volume (one to two times average), pullbacks on clearly shrinking volume, recoveries on expanding volume to new highs
- Danger-signal quick check: a sudden surge in a slow uptrend plus a volume spike plus a sharp intraday reversal — not triggered here

**Sample final answer**

> Run the four dimensions before you run with "it dropped 10%". Peaks and troughs are still rising, the pullback has not fallen back below the last breakout point, price is still above the 200-day line, and volume expanded on the advance and shrank on the pullback — nothing is broken, so this is a normal pullback and the book's action here is to sit tight, not to sell half. One caveat: the test is the shape of the move, not the percentage — "it went up a lot" is not a sell reason, "it broke down" is. The conditions that actually call for action are a break below the prior trough, or a danger signal such as a sudden surge in a slow uptrend with a volume spike and a sharp reversal — and then it is not half, it is the whole position out, with re-entry only after the four dimensions and volume qualify again a few days later. As for scaling out at specific prices, that belongs to the exit and trailing-stop card; give me the levels and I will run that card's rules.

### Example 2: a volume breakout from a box — chase it, and where is the stop?

**User question**

"This stock has been ranging for three months in a 19.8–20.2 box. Today it broke out on 2.5 times average volume and closed at 20.80. Can I chase it? Where do I put the stop?"

**How the skill decides**

- The veto gate comes first: if the broad market is bad, buy nothing; never enter a stock in a clear downtrend
- Entry type: this is a "volume breakout through resistance"; a breakout without volume is not a valid breakout, and volume here qualifies
- Three prices required: trigger above 20.20; stop 0.5–1.0 below the resistance line (19.70, about -5.3%, inside the ideal 10% band and far under the 20% hard cap); failure criterion = a close back below 20.20 means a false breakout, exit
- The eight entry checkpoints: "it has fallen a lot" and "there is good news" are not buy reasons
- Staging: take 20–30% of the planned size at point A, add the rest after point B (a pullback followed by a break of the prior swing high); sizing goes to `money-management-skill` (only invest one unit at a 1:3 risk-reward or better)

**Sample final answer**

> You can follow the rules, but write the three prices down before you click. Trigger above 20.20 (you are already in the trigger zone, so your fill is whatever you actually get), stop at 19.70 (just under the box top, about -5.3% from here, inside the ideal 10% band), and the failure criterion is a close back below 20.20 — that is a false breakout, no excuses, out. Do not take the full size at once: take two or three tenths of the planned size at point A and add after point B, a pullback followed by a break of the prior swing high. Two things must be said plainly. First, if the broad market is bad the whole plan is void — "when the market is bad, buy nothing" is a veto-level premise. Second, the book gives no formula for the target; you can only anchor it qualitatively to the prior high or the resistance above, and you must check the 1:3 risk-reward yourself against that anchor — if it does not clear, do not take the trade. The above is rule-based reasoning, not investment advice.

## How these skills were generated

These skills were generated with the RIA-TV++ pipeline of **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)**, in six stages:

1. **Whole-book understanding (Adler analysis)** — Mortimer Adler's analytical reading method, four steps (structural, interpretive, critical, applied), producing `BOOK_OVERVIEW.md`
2. **Parallel extraction** — several specialised extractors (frameworks, principles, cases, counter-examples, terminology) pull candidate methodology units from the text; 190 candidates for this book
3. **Triple verification** — every candidate must pass source sufficiency (each quote located in the text), executability (a paper walkthrough), and task gain (does it add anything to the book's own tasks); all 14 capability units passed
4. **RIA++ construction** — structured along six dimensions: R (quotation) / I (rewritten in our own words) / A1 (case from the book) / A2 (future trigger scenarios) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — dependencies, contrasts and compositions between cards are mapped into a capability index and routing table, and reuse plus trigger separability decide which cards are promoted to standalone skills
6. **Trigger and output testing** — trigger blind tests per card (including decoys: trigger when it should, stay silent when it should not) plus execution tests; failing cards go back for rework and are regression-tested

## Testing and verification

The test material ships inside each skill directory: the 8 entry directories under `pack/` and the `single/` entry each carry a `test-prompts.json` (9 files, 61 cases in total; the `single/` entry and the router entry hold two copies of the same suite, 52 distinct cases). The per-item scoring report is `test-results.md` at the repository root.

- **Trigger blind tests**: the report records 45 cases in the first round, 42 as expected and 3 with trigger ambiguity; all 3 were fixed by changing the skill rather than the test (description and keywords, adjacent-capability distinctions), and after regression 45/45 matched expectations, with zero decoy tolerance failures (every in-book confusion decoy was either correctly avoided or correctly routed)
- **Execution tests**: 13 task scenarios including 4 boundary / missing-input cases, 13/13 passed; every missing-input case asked for the data instead of guessing
- **Failures**: none
- **Known note**: combined "money behaviour + technical question" scenarios are dispatched by the router entry and then declined by the money-management card — that is by design

## Repository structure

```text
stock-trading-wisdom-skill/
├── README.md              ← Chinese version
├── README.en.md           ← you are reading this
├── LICENSE                ← MIT
├── BOOK_OVERVIEW.md       ← stage 0 output: Adler whole-book analysis
├── DIGEST.md              ← stage 5 output: reader-facing distilled long-form essay
├── INDEX.md               ← stage 3 output: skill map + dependencies
├── verified.md            ← 14 units that passed triple verification
├── coverage-audit.md      ← stage 1.5 output: coverage audit of the book's key tasks
├── needs-review.md        ← stage 1.5 output: open questions and known gaps
├── TEST_SUMMARY.md        ← stage 4 output: stress-test summary
├── CANGJIE_ADAPTATION.md  ← cangjie adaptation notes
├── GITHUB_REPO.md         ← repository metadata
├── test-results.md        ← test result records
├── candidates/            ← stage 1 output: raw candidate pool
│   ├── frameworks.md      ← framework and method candidates
│   ├── principles.md      ← principle / rule / calculation candidates
│   ├── cases.md           ← case candidates from the book
│   ├── counter-examples.md← counter-example and boundary candidates
│   └── glossary.md        ← terminology candidates
├── rejected/              ← stage 1.5 output: rejected units + reasons
├── bundle/                ← compilation source of truth
│   ├── verified.yaml      ← capability metadata, criteria and destinations
│   ├── cards/             ← capability card sources (six sections)
│   └── book/              ← overview.md + glossary.md
├── single/                ← single-mode build (one entry + all capability cards)
│   └── stock-trading-wisdom-skill/SKILL.md  ← entry: triggers + routing table + loading rules
└── pack/                  ← pack-mode build (one router + 7 promoted skills)
    └── */SKILL.md         ← 8 skills, each shipping a test-prompts.json
```

## How to use

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/stock-trading-wisdom-skill.git
```

### Install single (try this first)

```bash
# macOS / Linux
cp -r stock-trading-wisdom-skill/single/stock-trading-wisdom-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\stock-trading-wisdom-skill\single\stock-trading-wisdom-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain `SKILL.md`; do not copy the two json files under `pack/` into your skills directory:

```bash
# macOS / Linux
cd stock-trading-wisdom-skill/pack
cp -r stock-trading-wisdom-skill-router \
      motion-normality-skill \
      critical-point-buy-skill \
      sell-trailing-stop-skill \
      money-management-skill \
      stock-picking-skill \
      market-regime-skill \
      bubble-mania-skill ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\stock-trading-wisdom-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('stock-trading-wisdom-skill-router','motion-normality-skill','critical-point-buy-skill','sell-trailing-stop-skill','money-management-skill','stock-picking-skill','market-regime-skill','bubble-mania-skill') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (Claude Code, for example, uses `~/.claude/skills`).

### How to check it works

After installing, ask "this stock broke support on volume and snapped back — washout or distribution, can I keep holding it?" and see whether the agent goes straight into the four-dimension plus volume check of `motion-normality-skill` instead of giving you generic technical analysis. With single installed it reads the entry first and then loads a card by the routing table; with pack installed the capability is matched directly.

## Source

- *The Wisdom of Stock Trading* (《炒股的智慧》) by 陈江挺

## Notice

This repository publishes only the distilled skills, indexes and quick-reference material. It contains no PDF, EPUB, OCR files, screenshots or full-book transcript. Quotations inside the cards serve solely to attribute the methodology and keep it auditable.

Every numeric rule in the book (10% ideal stop / 20% hard cap, the 200-day and 250-day moving averages, the 1:3 risk-reward ratio, splitting a beginner's capital into 6–8 units, and so on) is an empirical generalisation by the author. The book offers no statistical backtest, so test any rule on your own instruments and state the convention you use. Nothing in this repository is investment advice.

## License

[MIT](./LICENSE)
