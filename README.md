<h1 align="center">炒股的智慧 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把《炒股的智慧》里那套"以人性与概率为核心"的交易决策体系，蒸馏成 14 张可单独触发、也可组合调用的能力卡。其中 7 张晋级为独立 skill，另外 7 张经来源路由入口按需加载。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 持仓回调了几天、纸上利润在缩水，分不清是正常回调还是出货危险信号，卖还是不卖
- 看到放量突破前高想追，却说不清入场触发价、止损价、跌破哪个价这笔交易就作废
- 有利润之后不知道该在哪一级上移止损，结果"让利润奔跑"跑成了"让利润变亏损"
- 单笔该下多大注、能不能补仓摊平、融资加杠杆能不能上——全凭感觉，一次重仓赔掉前面十次小胜
- 大盘不好时仍在一只只挑股票；或者反过来，指数涨自己的票不涨，怀疑指数失真
- 纪律明明都懂，止损就是下不了手、赚点就跑、套牢不卖，亏损后只会说一句"下次注意"

## 蒸馏了什么

14 张能力卡，按"先看位置、再定买卖、最后管钱管人"组织。slug 与 `bundle/verified.yaml` 一一对应：

- **买入与位置**：`critical-point-buy-skill`（临界点买点决策，critical）
- **持仓与卖出**：`motion-normality-skill`（股票运动正常性判定，critical）、`sell-trailing-stop-skill`（卖点与移动止损体系，critical）
- **钱与风险**：`money-management-skill`（资金管理与仓位规则，critical）
- **选股与大市**：`stock-picking-skill`（选股三步过滤，high）、`market-regime-skill`（大市判定清单，high）、`bubble-mania-skill`（泡沫识别，high）
- **经路由入口调用的能力卡**（router，共 7 张）：`cycle-phase`（周期四阶段定位，medium）、`psych-discipline`（心理纪律执行清单，high）、`stage-selftest`（学股阶段自测与排障，medium）、`manipulation-signs`（大户操纵痕迹识别，medium）、`return-allocation`（合理回报与战略定位，medium）、`ma250-system`（250 天线简易操作系统，high）、`fundamental-check`（基本面快速审视，medium）

7 张晋级 + 7 张路由 = 14 张，与 `bundle/cards/` 的 14 个文件、`bundle/verified.yaml` 的 14 条 capabilities 数量一致。

## 两种打包模式：single 与 pack

同一套 14 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`stock-trading-wisdom-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 14 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张晋级卡各自独立成 skill；其余 7 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `motion-normality-skill` — 股票运动正常性判定
- `critical-point-buy-skill` — 临界点买点决策
- `sell-trailing-stop-skill` — 卖点与移动止损体系
- `money-management-skill` — 资金管理与仓位规则
- `stock-picking-skill` — 选股三步过滤
- `market-regime-skill` — 大市判定清单
- `bubble-mania-skill` — 泡沫识别

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"还能不能拿 / 能不能追 / 止损放哪 / 买多少 / 买什么 / 大市怎么样 / 是不是泡沫" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：涨了一波回调 10%，是正常回调还是出货

**用户问题**

"我持有的这只票从 20 元一路涨到 27 元，这几天回调到 24 元，量比上冲时少了一大半。是正常回调还是出货？要不要先卖一半？"

**skill 如何判断**

- 入口按路由表分流：这是持仓健康检查，进 `motion-normality-skill`
- 四维逐项核对：走势线（20→21→22→27 波峰逐级抬高，回调 24 未跌破前一波谷）、支撑阻力（未跌回上一突破点之下）、突破确认、均线（股价在 200 天线上方）
- 量价验证：上冲放量（可为均量一两倍）、回调显著缩量、收复失地放量创新高
- 危险信号快检：缓升途中突然暴升 + 成交量猛增 + 冲高大幅回落，本例未触发

**最终回答示例**

> 先按四维走一遍，别急着用"跌了 10%"当结论。波峰波谷还在逐级抬高、回调没有跌回上一突破点之下、股价仍在 200 天线上方，量也是上冲放大、回调缩小——四项和量价都没破坏，属于正常回调，按书中口径这时候的动作是持有安坐，不是卖一半。要提醒的是：判定依据是形态语义，不是涨跌幅，"涨得多"不是卖出理由，"跌破了"才是。真正该动手的条件是跌破上一波谷，或出现"缓升途中突然暴升、量猛增、冲高大幅回落"这类危险信号——那时不是减一半，是全部脱手，几天后四维和量价重新达标再考虑重入。至于"卖一半"这种分批兑现的价位安排，属于卖点与移动止损那张卡的事，你要定具体价位我再按那张卡的规则算。

### 示例 2：放量突破箱体，能不能追、止损放哪

**用户问题**

"这只票横盘三个月，箱体 19.8–20.2，今天放量到均量 2.5 倍，收在 20.80。能不能追？止损放哪？"

**skill 如何判断**

- 前置否决先过：大市不好则什么都不买；个股处于明确跌势不入市
- 买点类型识别：属"放量突破阻力线"，无量突破不作有效突破，本例量能达标
- 三价齐备：触发价 20.20 上方；止损放在阻力线下方 0.5–1 元（19.70，约 -5.3%，落在 10% 以内的理想区，硬上限 20%）；失败判据＝收盘跌回 20.20 下方即假突破，止损离场
- 八条买入要点核对：不以"跌了很多"或"有好消息"为买入理由
- 建仓路径：A 点先进计划量的 20–30%，B 点（回调后再突破上一波高点）确认后补足；注码大小转 `money-management-skill`（至少 1:3 风险报酬比才投一份）

**最终回答示例**

> 可以按规则做，但先把三个价写下来再下单：触发价 20.20 上方（也就是现在就已在触发区，追高的话成交价按实际算）、止损 19.70（箱顶下方，距现价约 -5.3%，在 10% 以内的理想区间）、失败判据是收盘跌回 20.20 下方——那就是假突破，别找理由，走。仓位不要一次打满：A 点先进计划量的两三成，等它回调后再突破上一波高点（B 点）再补。还有两件事得说清楚：一是大市不好时这套全部作废，"大市不好，别买任何股票"是否决级前提；二是目标端原书没有公式，只能用前高或上方阻力线做定性参照，1:3 的风险报酬比要你自己按这个参照核算，算不过就不做。以上是规则推演，不构成投资建议。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解，产出 `BOOK_OVERVIEW.md`
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元，本书共 190 条候选
3. **三重验证筛选**——每个候选必须通过三项检验：来源充分性（原文逐条定位）、可执行性（纸面演练走一遍）、任务增益（对原书任务有没有增量），本书 14 个能力单元全部通过
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表，并据复用性与触发可分性决定哪些卡晋级为独立 skill
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与执行测试，未通过的卡回炉重做，回炉后再做回归验证

## 测试与验证

本仓库连生成过程的测试材料一起发布：`evals/` 下有 8 套触发用例（7 张独立 skill 各一套 + 路由可达性一套，共 52 条）、逐项评分报告 `test-results.md`，以及报告引用的回归复测记录 `trigger_retest.json`。

- **触发盲测**：报告口径首轮 45 例中 42 例符合预期、3 例触发歧义；3 例均按"修 skill 不修测试"处理（补 description 与 keywords、补相邻区分条目），回归复测后 45/45 全部符合预期，诱饵容错 0（跨书内混淆诱饵全部正确避开或经路由分发）
- **执行测试**：13 个任务场景（含 4 个边界/缺输入场景），13/13 通过；缺输入时全部先询问补齐，未静默猜值
- **未通过项**：无
- **遗留注记**："资金行为 + 技术问题"的复合场景由路由入口分发、再由资金管理卡兜底拒绝，属设计行为

## 仓库结构

```text
stock-trading-wisdom-skill/
├── README.md                          ← 你正在看的
├── README.en.md                       ← English version
├── LICENSE                            ← MIT
├── BOOK_OVERVIEW.md                   ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                        ← 14 个能力单元的三重验证结论
├── INDEX.md                           ← skill 地图：能力总表、依赖关系、加载顺序
├── bundle/                            ← 蒸馏中间产物（能力卡原稿 + 验证清单）
│   ├── verified.yaml                  ← 14 条 capability 的权威定义
│   ├── cards/                         ← 14 张能力卡原稿
│   │   ├── bubble-mania-skill.md
│   │   ├── critical-point-buy-skill.md
│   │   ├── cycle-phase-skill.md
│   │   ├── fundamental-check-skill.md
│   │   ├── ma250-system-skill.md
│   │   ├── manipulation-signs-skill.md
│   │   ├── market-regime-skill.md
│   │   ├── money-management-skill.md
│   │   ├── motion-normality-skill.md
│   │   ├── psych-discipline-skill.md
│   │   ├── return-allocation-skill.md
│   │   ├── sell-trailing-stop-skill.md
│   │   ├── stage-selftest-skill.md
│   │   └── stock-picking-skill.md
│   └── book/
│       ├── glossary.md
│       └── overview.md
├── single/                            ← 单一入口模式
│   └── stock-trading-wisdom-skill/
│       ├── SKILL.md                   ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json        ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md            ← 整书概览
│           ├── capability-index.md    ← 完整意图与关键词索引
│           ├── cheatsheet.md          ← 决策规则速查
│           ├── glossary.md            ← 术语表
│           └── capabilities/          ← 14 张能力卡（与 bundle/cards 内容对应）
│               ├── bubble-mania-skill.md
│               ├── critical-point-buy-skill.md
│               ├── cycle-phase.md
│               ├── fundamental-check.md
│               ├── ma250-system.md
│               ├── manipulation-signs.md
│               ├── market-regime-skill.md
│               ├── money-management-skill.md
│               ├── motion-normality-skill.md
│               ├── psych-discipline.md
│               ├── return-allocation.md
│               ├── sell-trailing-stop-skill.md
│               ├── stage-selftest.md
│               └── stock-picking-skill.md
├── pack/                              ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json   ← 14 条能力的去向表
│   ├── stock-trading-wisdom-skill-router/
│   │   ├── SKILL.md                   ← 来源路由入口
│   │   └── references/                ← 索引四件套 + 14 张卡，供 router 内部调用
│   │       ├── overview.md
│   │       ├── capability-index.md
│   │       ├── cheatsheet.md
│   │       ├── glossary.md
│   │       └── capabilities/
│   │           ├── bubble-mania-skill.md
│   │           ├── critical-point-buy-skill.md
│   │           ├── cycle-phase.md
│   │           ├── fundamental-check.md
│   │           ├── ma250-system.md
│   │           ├── manipulation-signs.md
│   │           ├── market-regime-skill.md
│   │           ├── money-management-skill.md
│   │           ├── motion-normality-skill.md
│   │           ├── psych-discipline.md
│   │           ├── return-allocation.md
│   │           ├── sell-trailing-stop-skill.md
│   │           ├── stage-selftest.md
│   │           └── stock-picking-skill.md
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
└── evals/                             ← 触发用例与测试结果
    ├── test-results.md                ← 逐项评分与偏差修复记录
    ├── trigger_retest.json            ← 修复后的回归复测记录
    ├── test-prompts__motion-normality.json
    ├── test-prompts__critical-point-buy.json
    ├── test-prompts__sell-trailing-stop.json
    ├── test-prompts__money-management.json
    ├── test-prompts__stock-picking.json
    ├── test-prompts__market-regime.json
    ├── test-prompts__bubble-mania.json
    └── test-prompts__stock-trading-wisdom-skill-router.json
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/stock-trading-wisdom-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r stock-trading-wisdom-skill/single/stock-trading-wisdom-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\stock-trading-wisdom-skill\single\stock-trading-wisdom-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

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

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"我这只票放量跌破支撑又拉回来了，是洗盘还是出货、还能不能拿"，看 agent 是否直接进入 `motion-normality-skill` 的四维加量价核对，而不是给你一段泛泛的技术分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《炒股的智慧》陈江挺 著

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（止损 10% 理想 / 20% 硬顶、200 天与 250 天均线、1:3 风险报酬比、新手本金分 6~8 份等）都是作者经验归纳，原书未提供统计回测背书，使用时需按标的自行测试并声明所用口径。本仓库内容不构成投资建议。

## License

[MIT](./LICENSE)
