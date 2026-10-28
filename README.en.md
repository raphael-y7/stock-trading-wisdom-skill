<h1 align="center">Stock Trading Wisdom Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the trading system in Chen Jiangting's *The Wisdom of Stock Trading: Experience of Making a Living by Trading Stocks on Wall Street (4th Edition)* — "protect your capital + bet small and split your positions + trade only at critical points + cut losses short and let profits run" — into 14 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- Your position has a profit and then pulls back for two days; you cannot tell a normal low-volume pullback you should sit through from distribution you should exit — the book gives you a four-dimension check (trend line, support and resistance, confirmation of the breakout point, position against the moving average) plus volume-price confirmation, judged item by item instead of by feel
- You see a high-volume breakout of a prior high and want to chase, but fear a false breakout — the entry and the stop are two halves of the same definition: trigger price, stop price and failure criterion must all be fixed together, and a trade with one of them missing is not a complete trade
- You do not know when to sell a winner: protect capital first (move the stop above your cost), lose only a little, take windfall profits when they come, watch for rising volume with a stalling price, and trail the stop up through each successive wave trough — six rules, each with its own trigger
- You do not know how much to bet on this one trade: how many slices to cut your capital into, how much to bet at 60% conviction versus 80%, where the 1:3 risk-reward threshold sits, and why averaging down on a loser is "the shortcut to bankruptcy"
- You have the order of the three layers backwards — "when the broad market is bad, do not buy any stock" is a veto-level premise, and stock selection runs market → strongest sector → the leader in that sector
- You cannot tell whether the current mania is a bubble, or you know it is one and still want in — the six-characteristic checklist locates the stage and forces you to write your exit discipline down before you enter

## What was distilled

14 capability cards, organized in the order "clear the market first, pick the target second, fix the location third, size the bet last":

- **Premise and target**: `market-regime` (broad-market checklist), `stock-picking` (three-step stock selection)
- **Location: where to buy, where to sell**: `critical-point-buy` (critical-point entry decision), `sell-trailing-stop` (sell rules and the trailing-stop system)
- **Holding and betting**: `motion-normality` (is the stock's movement normal), `cycle-phase` (four-stage cycle positioning), `money-management` (position sizing and betting rules)
- **Environment and ground-level checks**: `bubble-mania` (bubble/mania identification), `manipulation-signs` (traces of large-operator manipulation), `fundamental-check` (quick fundamental review)
- **Discipline, expectations and a minimal system**: `psych-discipline` (psychological discipline checklist), `stage-selftest` (learning-stage self-test and troubleshooting), `return-allocation` (reasonable returns and strategic positioning), `ma250-system` (the 250-day moving-average minimal system)

## Two packaging modes: single and pack

The same 14 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `stock-trading-wisdom-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 14 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the routing table | 7 high-frequency cards become standalone skills; all 14 also keep a source copy under the router's `references/`, and the 7 that were not promoted are reachable only through the router |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `motion-normality-skill` — is the stock's movement normal
- `critical-point-buy-skill` — critical-point entry decision
- `sell-trailing-stop-skill` — sell rules and the trailing-stop system
- `money-management-skill` — position sizing and betting rules
- `stock-picking-skill` — three-step stock selection
- `market-regime-skill` — broad-market checklist
- `bubble-mania-skill` — bubble/mania identification

The 7 that stay in the router and are reachable only through the routing entry: `cycle-phase`, `psych-discipline`, `stage-selftest`, `manipulation-signs`, `return-allocation`, `ma250-system`, `fundamental-check`.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "should I still hold / can I chase / should I sell / how much / which stock / is the market okay / is this a bubble" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: a high-volume breakout from a range — can I chase it?

**User question**

"This stock has been stuck between 19.8 and 20.2 for three months. Today it closed at 20.80 on heavy volume — a breakout. Can I chase it? And if I do, where does the stop go?"

**How the skill reasons**

- First the veto gate in `critical-point-buy`: if the broad market is bad, buy nothing and the flow terminates; if the stock is in a clear downtrend, "never enter a declining trend" terminates it too. Only when both pass does entry identification start
- Entry type, one of five: this is type ② "high-volume break of a resistance line". Trigger = standing above the resistance line on volume; stop 0.5–1 yuan below the line (the book's own example: 15 yuan resistance → stop at 14.50 or 14); failure criterion = a close back below the resistance line, i.e. a false breakout, exit. **A breakout without volume is not a valid breakout** and terminates the flow
- Stop compliance: the book's convention is an ideal loss within 10%, with a hard cap of 20% under any circumstances; low-priced stocks get more absolute room (a 5 yuan stock gets 0.75 yuan → stop at 4.25)
- Sizing goes to `money-management`: ask "can I afford to lose this", then apply the slice convention (6–8 slices for a beginner, another book convention of 5–10 slices, and the 2016 reprint system's single bet ≤ 10% of capital — three conventions coexist, take the intersection), the conviction tiers (60% → about 10%, 80% → 30%–50%), and the **G/L ≥ 3** risk-reward threshold

**Sample answer**

> Answer two things before we talk about chasing. First, how is the broad market? The book's premise is veto-level — when the market is bad, even a beautiful critical point does not get acted on. Second, is this a breakout or a volume-less fake? Only standing above 20.20 on volume qualifies as a type ② entry.
>
> Assuming both pass: the trigger sits just above 20.20, and the stop goes 0.5–1 yuan below the resistance line per the book's practice, so 19.20–19.70 — a 5%–8% loss, inside the "ideally within 10%" band. Write the failure criterion down as one hard line: a close back below 20.20 means a false breakout, you leave, you do not add and you do not average down.
>
> Then check whether the trade is worth taking at all. G is target minus entry, L is entry minus stop, and the book's threshold is G/L of at least 1:3; below that, drop the trade or find another target. One gap in the book has to be stated plainly: **it gives no algorithm for the target price**. The target can only come from a chart reference (a prior high, a resistance line above), so that G is drawn by you — write down where you drew it and do not move it afterwards.
>
> Finally, sizing. Under the slice convention, with 200,000 of capital at the beginner tier, a single bet is roughly 20,000; split it 200:400:400, where the first batch is only a probe and the second is added once the movement confirms. Note that A-shares have daily limits and T+1, so a breakout day may not even be buyable — the book does not discuss that execution friction, so leave room for it yourself.

### Example 2: a pullback after a profit — hold or take the money?

**User question**

"I bought this at 20, it ran to 27, then pulled back on light volume to 24 and my paper profit shrank. Should I sell first?"

**How the skill reasons**

- `motion-normality` establishes direction first: rising peaks and troughs → uptrend; drifting aimlessly in a range → "no trend, no trade", flow terminates; a clear downtrend → hand over to `sell-trailing-stop` for the exit
- Four dimensions, checked one by one; any one broken marks it "not normal": ① trend line (peaks and troughs stepping up, price above the line) ② support and resistance (the pullback after a breakout has not fallen back below the resistance line) ③ double-shoulder / head-and-shoulders (does it continue after crossing the breakout point) ④ moving average (in an uptrend price is above the 200-day; below it, do not buy and do not hold)
- Volume-price verification: is the advance on expanding volume, is the pullback clearly shrinking, does the recovery make a new high on volume, is this advance no weaker than the previous one
- Danger-signal quick check (a terminating branch): a sudden vertical spike after a slow rise + a burst in volume + a sharp intraday reversal → straight to danger signal, skipping the composite judgement, liquidate everything
- All four dimensions plus volume-price pass with no danger signal → "normal movement", action is to hold and sit still; adding size goes to `money-management`

**Sample answer**

> This is exactly the high-frequency beginner mistake the book names: once you have a profit, every pullback means less paper profit, and the first instinct is to sell and take it. The author uses the 20→27→24→35 sequence to make the point repeatedly — a low-volume pullback to 24 is normal, and you must not sell into it.
>
> So do not start with "should I sell". Run the four-dimension check: is price still above the trend line? Did this pullback fall back below the price where the last advance broke out? Is it still above the 200-day? Then check volume: was the advance on expanding volume, and is this pullback clearly shrinking? If all four pass, volume-price agrees and there is no danger signal, the conclusion is "normal movement" and the action is to hold and sit still.
>
> Two elasticities have to be stated honestly. First, **the book gives no percentage threshold for "how much of a pullback counts as broken"**; the judgement is positional — has price fallen back below the previous wave trough, the breakout point, or the trend line — not "exit on an 8% or 10% drop". Second, **the book gives no single definition of how to draw the trend line or how to mark peaks and troughs**, so the same person can draw it differently a week later. Fix your drawing convention first and write it into the plan, otherwise you will recognise the same stock inconsistently.
>
> When does it flip to an exit? A danger signal is unconditional: a sudden spike after a slow rise, a burst in volume, and a sharp reversal (the book's template is 62 yuan giving back to a 58 close in the last half hour), or a high-volume decline, or a break of support or the moving average that is not recovered. Those do not wait for the four dimensions to be worked through one by one.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application. This stage also fixes the selection standard: every capability unit is judged by whether it helps analyse a stock or the market and form a buy/sell decision
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text; this book yielded 190 candidates (44 frameworks + 146 principles)
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (V1 source sufficiency), the ability to answer questions the book never explicitly addresses (V2 executability, by paper walkthrough), and not being common sense (V3 task gain). All 190 candidates received a disposition, and they converged into 14 capability units
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots); the B section specifically records the author's blind spots and period limitations
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table, with an explicit boundary between neighbouring cards (for example "which stock" belongs to selection, "when to buy" to the critical-point card, "how much" to the money card)
6. **Trigger and output testing** — write trigger blind tests for every card (including decoys: fire when they should, stay silent when they should not) plus execution evaluation tasks; failing cards go back for rework on the description and the A2 language signals, then through regression verification

## Testing and verification

This repository publishes the test material from the generation process alongside the skills: `evals/test-prompts__*.json` holds the trigger cases for the 8 discoverable entries, `evals/trigger_*.json` holds the raw blind-test records, and `evals/test-results.md` is the item-by-item scoring log including the rework — it keeps the failures, not just the passes.

- **Trigger blind tests**: 45 cases across 8 entries (7 skill suites plus one router-reachability suite), answered by an independent subagent that had to choose one entry among all 8 discoverable ones. First round: 42 as expected, 3 ambiguous triggers
- **How the 3 deviations were handled**: by fixing the skills, not the tests — "margin/leverage" had no owner, so the `money-management` description and the router dispatch table gained the leverage signal; "does a cyclical stock flat for two years count as an accumulation phase" was being grabbed by `stock-picking`, so the distinction "single-stock stage judgement belongs to `cycle-phase`" was added; the third was judged a defensible boundary case and, after router re-testing confirmed correct dispatch, recorded as such. After regression: **45/45 as expected**
- **Execution tests**: 13 tasks (including 4 missing-input / out-of-scope scenarios), each checked for reproducible output, refusal where refusal is required and questions where questions are required; the report concludes 13/13 passed with no failures
- **Missing-input scenarios**: "is the market about to turn" with no data, "can I buy Moutai now" with no price levels, trailing stops with no cost basis — all asked for the required inputs first and none silently guessed

## Repository layout

```text
stock-trading-wisdom-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification conclusions for the 14 capability units
├── single/                        ← single-entry build
│   └── stock-trading-wisdom-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 14 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── stock-trading-wisdom-skill-router/
│   │   ├── SKILL.md               ← source router entry
│   │   └── references/            ← 14 cards + indexes, called by the router
│   ├── motion-normality-skill/
│   │   └── SKILL.md
│   ├── critical-point-buy-skill/
│   │   └── SKILL.md
│   ├── sell-trailing-stop-skill/
│   │   └── SKILL.md
│   ├── money-management-skill/
│   │   └── SKILL.md
│   ├── stock-picking-skill/
│   │   └── SKILL.md
│   ├── market-regime-skill/
│   │   └── SKILL.md
│   └── bubble-mania-skill/
│       └── SKILL.md
└── evals/                         ← trigger blind tests and execution evaluation records
    ├── test-results.md            ← item-by-item scoring and rework log
    ├── test-prompts__motion-normality.json
    ├── test-prompts__critical-point-buy.json
    ├── test-prompts__sell-trailing-stop.json
    ├── test-prompts__money-management.json
    ├── test-prompts__stock-picking.json
    ├── test-prompts__market-regime.json
    ├── test-prompts__bubble-mania.json
    ├── test-prompts__chaogu-zhihui-router.json
    ├── trigger_T1.json
    ├── trigger_T2.json
    ├── trigger_T3.json
    └── trigger_retest.json
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/stock-trading-wisdom-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r stock-trading-wisdom-skill/single/stock-trading-wisdom-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\stock-trading-wisdom-skill\single\stock-trading-wisdom-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

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

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "I have a profit on this stock and it just pulled back on light volume — should I sell first?" If the agent enters the four-dimension plus volume-price check and returns something like "normal movement → hold and sit still" with item-by-item evidence, instead of generic technical commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *The Wisdom of Stock Trading* by Chen Jiangting
- Distilled from the whole book, producing 14 capability cards

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (the 10% and 20% stop bounds, the 1:3 risk-reward ratio, the 60%–70% win rate, 6–8 slices of capital, the 250-day average with a 5%–8% stop, "nine wins out of ten") are the author's case- and experience-based rules without statistical backtesting; test them on your own instruments and declare the convention you use. Nothing in this repository is investment advice.

## License

[MIT](https://opensource.org/licenses/MIT)
