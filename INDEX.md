# Skill 地图 — 炒股的智慧

一句话说明：本文件由 `bundle/verified.yaml` 生成，是这套 skill 的能力地图——全书 14 张能力卡，7 张晋级为独立 skill（promoted），7 张由来源路由入口统一承接（router），下表是它们的 ID、slug、标题、重要度与去向。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `cap.stock-trading-wisdom-skill.motion-normality-skill` | `motion-normality-skill` | 股票运动正常性判定 | critical | promoted → 独立 skill `motion-normality-skill` |
| `cap.stock-trading-wisdom-skill.critical-point-buy-skill` | `critical-point-buy-skill` | 临界点买点决策 | critical | promoted → 独立 skill `critical-point-buy-skill` |
| `cap.stock-trading-wisdom-skill.sell-trailing-stop-skill` | `sell-trailing-stop-skill` | 卖点与移动止损体系 | critical | promoted → 独立 skill `sell-trailing-stop-skill` |
| `cap.stock-trading-wisdom-skill.money-management-skill` | `money-management-skill` | 资金管理与仓位规则 | critical | promoted → 独立 skill `money-management-skill` |
| `cap.stock-trading-wisdom-skill.stock-picking-skill` | `stock-picking-skill` | 选股三步过滤 | high | promoted → 独立 skill `stock-picking-skill` |
| `cap.stock-trading-wisdom-skill.market-regime-skill` | `market-regime-skill` | 大市判定清单 | high | promoted → 独立 skill `market-regime-skill` |
| `cap.stock-trading-wisdom-skill.bubble-mania-skill` | `bubble-mania-skill` | 泡沫（疯）识别 | high | promoted → 独立 skill `bubble-mania-skill` |
| `cap.stock-trading-wisdom-skill.cycle-phase` | `cycle-phase` | 周期四阶段定位 | medium | router → 路由入口 |
| `cap.stock-trading-wisdom-skill.psych-discipline` | `psych-discipline` | 心理纪律执行清单 | high | router → 路由入口 |
| `cap.stock-trading-wisdom-skill.stage-selftest` | `stage-selftest` | 学股阶段自测与排障 | medium | router → 路由入口 |
| `cap.stock-trading-wisdom-skill.manipulation-signs` | `manipulation-signs` | 大户操纵痕迹识别 | medium | router → 路由入口 |
| `cap.stock-trading-wisdom-skill.return-allocation` | `return-allocation` | 合理回报与战略定位 | medium | router → 路由入口 |
| `cap.stock-trading-wisdom-skill.ma250-system` | `ma250-system` | 250天线简易操作系统 | high | router → 路由入口 |
| `cap.stock-trading-wisdom-skill.fundamental-check` | `fundamental-check` | 基本面快速审视 | medium | router → 路由入口 |

合计 14 张：promoted 7 张、router 7 张。

## 依赖关系（also_read）

`also_read` 是每张卡建议补读的相邻能力——不是硬依赖，而是判定跨域时该接着看哪张卡。

| 能力卡 | also_read（建议补读） |
|---|---|
| `motion-normality-skill` | `sell-trailing-stop-skill`（卖点与移动止损体系）、`cycle-phase`（周期四阶段定位）、`market-regime-skill`（大市判定清单）、`manipulation-signs`（大户操纵痕迹识别） |
| `critical-point-buy-skill` | `motion-normality-skill`（股票运动正常性判定）、`sell-trailing-stop-skill`（卖点与移动止损体系）、`money-management-skill`（资金管理与仓位规则）、`stock-picking-skill`（选股三步过滤）、`ma250-system`（250天线简易操作系统） |
| `sell-trailing-stop-skill` | `motion-normality-skill`（股票运动正常性判定）、`money-management-skill`（资金管理与仓位规则）、`psych-discipline`（心理纪律执行清单） |
| `money-management-skill` | `critical-point-buy-skill`（临界点买点决策）、`return-allocation`（合理回报与战略定位）、`sell-trailing-stop-skill`（卖点与移动止损体系） |
| `stock-picking-skill` | `market-regime-skill`（大市判定清单）、`critical-point-buy-skill`（临界点买点决策）、`fundamental-check`（基本面快速审视） |
| `market-regime-skill` | `stock-picking-skill`（选股三步过滤）、`bubble-mania-skill`（泡沫（疯）识别）、`motion-normality-skill`（股票运动正常性判定） |
| `bubble-mania-skill` | `market-regime-skill`（大市判定清单）、`motion-normality-skill`（股票运动正常性判定） |
| `cycle-phase` | `motion-normality-skill`（股票运动正常性判定）、`critical-point-buy-skill`（临界点买点决策）、`market-regime-skill`（大市判定清单） |
| `psych-discipline` | `sell-trailing-stop-skill`（卖点与移动止损体系）、`money-management-skill`（资金管理与仓位规则） |
| `stage-selftest` | `psych-discipline`（心理纪律执行清单）、`money-management-skill`（资金管理与仓位规则） |
| `manipulation-signs` | `motion-normality-skill`（股票运动正常性判定）、`critical-point-buy-skill`（临界点买点决策）、`bubble-mania-skill`（泡沫（疯）识别） |
| `return-allocation` | `money-management-skill`（资金管理与仓位规则）、`market-regime-skill`（大市判定清单） |
| `ma250-system` | `critical-point-buy-skill`（临界点买点决策）、`sell-trailing-stop-skill`（卖点与移动止损体系）、`money-management-skill`（资金管理与仓位规则） |
| `fundamental-check` | `stock-picking-skill`（选股三步过滤） |

共 39 条补读关系。被引用最多的是 `motion-normality-skill`、`money-management-skill`（各 6 次），说明它们是这套体系里的枢纽卡。

## 加载顺序

1. **先读入口 SKILL.md**——single 模式是 `single/stock-trading-wisdom-skill/SKILL.md`，pack 模式是 `pack/stock-trading-wisdom-skill-router/SKILL.md`。入口只负责两件事：判断是否属于本书能力域、按路由表分流。
2. **再按路由表加载 1–2 张卡**——单域任务只加载 1 张；任务明确跨域（例如"这个突破能不能追、该下多少注"）时最多 2 张，先加载主判定的卡，再按上表的 `also_read` 补读。
3. **不加载卡的情形**——书名/作者/章节/整书概览类问题用入口的「核心原则」与 `references/overview.md` 回答；术语查 `references/glossary.md`；只要规则速查查 `references/cheatsheet.md`；路由表与 `capability-index.md` 都命不中的意图，明确告知超出本书范围，不要硬套。
4. **判停优先于给结论**——数据不足以支撑判定（无价格/量能/均线信息）时先询问补齐；用户要求保证收益、稳赚或内幕消息时说明这是概率框架并拒绝。
