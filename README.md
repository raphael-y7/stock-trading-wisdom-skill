<h1 align="center">炒股的智慧 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把陈江挺《炒股的智慧：在华尔街炒股为生的体验（第四版）》里那套"保本 + 小注分仓 + 在临界点买卖 + 截短亏损让利润奔跑"的交易体系，蒸馏成 14 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 手里的票有利润后回调了两天，分不清是"正常缩量回调该安坐"还是"放量出货该走人"——书里给的是走势线、支撑阻力、突破点确认、均线位置四个维度加量价配合的核对口径，四项逐项判通过或破坏，不靠感觉
- 看到放量突破前高想追，又怕买在假突破上——买点和止损点是同一条定义的两半：触发价、止损价、失败判据三个价必须同时定下来，缺一个这笔交易就不成立
- 浮盈不知道什么时候卖：保本第一（把止损上移到成本之上）、亏小钱、遇有暴利拿了再说、量增价滞、移动止损沿浪谷一级级往上推，六招各有自己的触发条件
- 不知道该拿多少钱下这一注：本金分几份、60% 胜算和 80% 胜算各下多大、1:3 的风险报酬比门槛卡在哪、为什么亏损时摊平是"破产的捷径"
- 把大市、板块、个股三层的顺序弄反了——"大市不好时，别买任何股票"是否决级前提，选股要按"大市 → 牛劲最足的类别 → 该类别的龙头"三步走
- 分不清眼前这波热炒是不是泡沫，或者明知是泡沫还想参与——书里的六特性清单能定位它处在哪个阶段，并逼你在进场前先把退出纪律写下来

## 蒸馏了什么

14 张能力卡，按"先过大市、再选对象、然后定位置、最后管仓位"的顺序组织：

- **前提与对象**：`market-regime`（大市判定清单）、`stock-picking`（选股三步过滤）
- **位置：在哪买、在哪卖**：`critical-point-buy`（临界点买点决策）、`sell-trailing-stop`（卖点与移动止损体系）
- **持仓与下注**：`motion-normality`（股票运动正常性判定）、`cycle-phase`（周期四阶段定位）、`money-management`（资金管理与仓位规则）
- **环境与底层校验**：`bubble-mania`（泡沫（疯）识别）、`manipulation-signs`（大户操纵痕迹识别）、`fundamental-check`（基本面快速审视）
- **纪律、预期与极简系统**：`psych-discipline`（心理纪律执行清单）、`stage-selftest`（学股阶段自测与排障）、`return-allocation`（合理回报与战略定位）、`ma250-system`（250 天线简易操作系统）

## 两种打包模式：single 与 pack

同一套 14 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`stock-trading-wisdom-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 14 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张高频卡各自独立成 skill；14 张卡在 router 的 `references/` 里都留有原文副本，其中没晋级的 7 张只能经 router 调用 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `motion-normality-skill` — 股票运动正常性判定
- `critical-point-buy-skill` — 临界点买点决策
- `sell-trailing-stop-skill` — 卖点与移动止损体系
- `money-management-skill` — 资金管理与仓位规则
- `stock-picking-skill` — 选股三步过滤
- `market-regime-skill` — 大市判定清单
- `bubble-mania-skill` — 泡沫（疯）识别

留在 router 里、只经路由入口调用的 7 张：`cycle-phase`、`psych-discipline`、`stage-selftest`、`manipulation-signs`、`return-allocation`、`ma250-system`、`fundamental-check`。

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"还能拿吗 / 能不能追 / 该卖了吗 / 下多少 / 买哪只 / 大市行不行 / 是不是泡沫" | pack | 这 7 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：箱体放量突破，能不能追

**用户问题**

"这票在 19.8–20.2 之间横了三个月，今天放量收在 20.80，突破了。现在能不能追？追了止损放哪？"

**skill 如何判断**

- 先过 `critical-point-buy` 的前置否决：大市不好 → 什么都不买，流程直接终止；个股处在明确跌势 → "绝不要在跌势时入市"，同样终止。只有两项都过关，才进入买点识别
- 买点类型五选一：这是第 ② 类"放量突破阻力线"。触发 = 放量站上阻力线；止损设在阻力线下方 0.5–1 元（书里的原例是 15 元阻力线 → 止损 14.50 或 14 元）；失败判据 = 收盘跌回阻力线之下，视为假突破，止损离场。**无量突破不算有效突破**，直接终止
- 止损合规检查：书里的口径是亏损幅度 10% 以内为理想，任何情况不超过 20% 的硬上限；低价股按绝对值放宽（5 元股给 0.75 元空间 → 止损 4.25 元）
- 仓位转 `money-management`：先问"我亏得起吗"，再按份数口径（新手 6–8 份、家训另一口径 5–10 份、2016 再版系统单笔 ≤ 本金 10%，三个口径并存，取交集）、胜算档位（60% → 约 10%，80% → 30%~50%）、以及 **G/L ≥ 3** 的风险报酬比门槛核算

**最终回答示例**

> 先回答两件事再谈追不追。第一，大市怎么样？书里的前提是否决级的——大市不好时，再漂亮的临界点也不动手。第二，这是突破还是无量假动作？只有放量站上 20.2 才算第 ② 类买点。
>
> 假设这两条都过：触发价就在 20.20 上方，止损按书里的做法放在阻力线下方 0.5–1 元，也就是 19.20–19.70 这一档，对应亏损 5%~8%，落在"10% 以内为理想"的区间里。失败判据写死一条：收盘跌回 20.20 之下就是假突破，走人，不加仓不摊平。
>
> 然后算这笔值不值得做。G 是目标价减买入价，L 是买入价减止损价，书里的门槛是 G/L 至少 1:3，达不到就放弃这笔或另找标的。这里必须说明一处原书缺口：**书里没有给目标价的算法**，目标只能取自图形参照（前高、上方阻力线），所以这个 G 是你自己画的，画在哪要写进计划，别事后改。
>
> 最后是下多少。按份数口径，20 万本金、新手档，单笔大约 2 万；分批按 200:400:400 展开，第一批只是试盘，走势符合预想才加第二批。注意 A 股有涨停和 T+1，突破当日可能根本买不到，这个执行摩擦书里没讨论，得你自己预留。

### 示例 2：有利润后回调，该拿着还是落袋

**用户问题**

"这票我从 20 块拿到现在，冲到 27 之后缩量回调到 24，纸上利润少了一截。是不是该先卖了？"

**skill 如何判断**

- `motion-normality` 先定方向：波峰波谷逐级抬高 → 升势；区间漫无目的游动 → "无势不炒"，流程终止；明确跌势 → 转 `sell-trailing-stop` 处理离场
- 四维逐项核对，任一项破坏即判"不正常"：① 走势线（波峰波谷逐级抬高、运行在走势线之上）② 支撑阻力（突破后回调未跌回阻力线下）③ 双肩头肩（穿越突破点后是否延续）④ 均线（升势中股价在 200 天线上方；200 天线下方原则上不买不持）
- 量价验证：上冲是否放量、回调是否显著缩量、收复失地是否放量创新高、本轮上冲强度是否不弱于上一轮
- 危险信号快检（判停分支）：缓升途中突然暴升 + 交易量猛增 + 冲高大幅回落 → 直接判危险信号，跳过综合判定，全部脱手
- 四维与量价全过且无危险信号 → 结论"正常运动"，动作是持有安坐不动；要加注则转 `money-management`

**最终回答示例**

> 这正是书里点名的"新手高频错误"：入场后每次回调都意味着纸上利润变少，第一反应就是卖掉获利。作者用 20→27→24→35 这个序列反复讲：缩量回调到 24 是正常的，这时候千万不要卖。
>
> 所以别先问"该不该卖"，先做四维核对：股价还在走势线上方吗？这轮回调有没有跌回上一波突破的那个价位之下？还在 200 天线上方吗？再对量：上冲那几天是不是放量，这轮回调是不是明显缩量。四项全过、量价也配合、又没有危险信号，结论就是"正常运动"，动作是持有安坐。
>
> 但要照实说两处弹性。第一，**书里没有给"回调多少算破位"的百分比阈值**，判定靠的是"有没有跌回前一波谷/突破点/走势线之下"这种位置关系，不是跌 8% 或 10% 就离场。第二，**走势线怎么画、波峰波谷怎么划，原书没给统一定义**，同一个人隔一周画都可能不一样——所以你得先把画法定下来并写进预案，否则同一只票会忽认忽不认。
>
> 什么情况下改判离场？出现危险信号就无条件走：缓升途中突然暴升、量猛增、冲高又大幅回落（书里的样板是 62 元尾盘半小时跌回 58 元收盘），或者放量下跌、跌破支撑或均线收不回来。这类信号不需要等四个维度慢慢核对。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解，先定下"一切能力单元都以能不能辅助个股/大市判断并形成买卖决策为准绳"的取舍标准
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元；本书共产出 190 条候选（框架 44 条 + 原则 146 条）
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（V1 来源充分性）、能回答书中未明说的新问题（V2 可执行性，纸面演练）、不是常识（V3 任务增益）；190 条候选全部有去向，最终收敛为 14 个能力单元
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化，B 段专门记录作者的盲点与时代局限
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表，并显式写明每张卡与相邻卡的区分（例如"买什么"归选股卡、"何时买"归临界点卡、"下多大"归资金卡）
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与执行评测任务，未通过的卡回炉改 description 与 A2 语言信号，改完再做回归验证

## 测试与验证

本仓库把生成过程的测试材料一起发布：`evals/test-prompts__*.json` 是 8 个可发现入口的触发用例，`evals/trigger_*.json` 是盲测的原始记录，`evals/test-results.md` 是逐项评分与回炉修复的完整过程——包含失败项，不是只留通过记录。

- **触发盲测**：8 个入口共 45 例（7 套 skill 用例 + 1 套 router 可达性用例），由独立子代理在全部 8 个可发现入口间多选一作答。首轮 42 例符合预期，3 例触发歧义
- **3 例偏差的处理**：都是改 skill 而不是改测试——"融资加杠杆"无人承接 → 在 `money-management` 的 description 与 router 分发表补杠杆信号；"周期股横盘算不算蓄劲期"被 `stock-picking` 抢触发 → 补上"单票阶段判定用 `cycle-phase`"的区分句；第三例判定为可辩护的边界场景，经 router 复测确认分发正确后记录在案。回归复测后 **45/45 全部符合预期**
- **执行测试**：13 个任务（含 4 个缺输入/越界场景），逐项核对是否给出可复算的输出、该拒答时是否拒答、该追问时是否追问，报告结论为 13/13 通过、无未通过项
- **缺输入场景**：无行情数据问"要变盘吗"、无价位问"茅台现在能买吗"、无持仓成本问移动止损——均按要求先索要输入，没有静默猜值

## 仓库结构

```text
stock-trading-wisdom-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 14 个能力单元的三重验证结论
├── single/                        ← 单一入口模式
│   └── stock-trading-wisdom-skill/
│       ├── SKILL.md               ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json    ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md        ← 整书概览
│           ├── capability-index.md  ← 完整意图与关键词索引
│           ├── cheatsheet.md      ← 决策规则速查
│           ├── glossary.md        ← 术语表
│           └── capabilities/      ← 14 张能力卡
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── stock-trading-wisdom-skill-router/
│   │   ├── SKILL.md               ← 来源路由入口
│   │   └── references/            ← 14 张卡 + 索引，供 router 内部调用
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
└── evals/                         ← 触发盲测与执行评测记录
    ├── test-results.md            ← 逐项评分与回炉修复记录
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

装完问一句"我这票有利润了，缩量回调要不要先卖"，看 agent 是否直接进入"四维 + 量价"的核对流程并给出"正常运动 → 持有安坐"这类带逐项依据的结论，而不是给你一段泛泛的技术分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《炒股的智慧》陈江挺 著
- 全书蒸馏，共产出 14 张能力卡

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（止损 10% 与 20% 的上下限、1:3 风险报酬比、胜率 60–70%、本金 6–8 份、250 天线与 5–8% 止损、"十次中有九次赚钱"等）都是作者的案例与经验归纳，原书未提供统计回测背书，使用时需按标的自行测试并声明所用口径。本仓库内容不构成投资建议。

## License

[MIT](https://opensource.org/licenses/MIT)
