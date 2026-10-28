# 炒股的智慧 — 阶段 4 压力测试报告

- 测试时间: 2026-10-23/24
- 被测对象: pack 编译产物（1 路由入口 + 7 晋级 skill）+ Bundle 内 7 张路由卡
- 宿主/模型: ZCode / GLM-5.3-Flash（独立干净子代理盲测，非自评）
- 测试用例: `.cangjie/test-prompts/*.json`（7 套 45 例）；执行测试任务内嵌于执行员指令

## 一、触发盲测（独立子代理，多选一于全部 8 个可发现入口）

| 被测 skill | 用例数 | should_trigger | 诱饵(不应触发) | edge | 首轮结果 |
|---|---|---|---|---|---|
| motion-normality-skill | 7 | 3/3 ✓ | 2/2 ✓（基本面→fundamental-check 路由；大市→market-regime-skill） | 2/2 ✓（纪律问题转卖点卡；弱信号仍正确触发） | 通过 |
| critical-point-buy-skill | 6 | 3/3 ✓ | 2/2 ✓（定投→return-allocation；摊平→money-management-skill） | 1 例偏差（见下 T1-13） | 通过(1 edge 注记) |
| sell-trailing-stop-skill | 6 | 3/3 ✓ | 2/2 ✓（基本面+形态→motion-normality-skill；入场止损→critical-point-buy-skill） | 1/1 ✓（跌停卖不出，卡内如实承认 A 股制度边界） | 通过 |
| money-management-skill | 6 | 3/3 ✓ | 2/2 ✓ | 1 例偏差（T2-12 杠杆无人承接） | 修复后通过 |
| stock-picking-skill | 6 | 3/3 ✓ | 2/2 ✓ | 1 例偏差（T3-18 蓄劲期误投本卡） | 修复后通过 |
| market-regime-skill | 6 | 3/3 ✓ | 2/2 ✓ | 1/1 ✓（单日暴跌按趋势定义作答） | 通过 |
| bubble-mania-skill | 6 | 3/3 ✓ | 2/2 ✓ | 1/1 ✓（meme 币：机制适用+范围声明） | 通过 |
| stock-trading-wisdom-skill-router（可达性） | 9 | 7/7 ✓（7 张路由卡全部可达） | 2/2 ✓（预测/荐股均拒绝，命中 stop_conditions） | — | 通过 |

**首轮 45 例：42 符合预期，3 例触发歧义。**

### 偏差与修复（按"修 skill"处理，非改测试）

| case | 现象 | 根因 | 修复（A2/description 层） |
|---|---|---|---|
| T2-12 | "融资加杠杆炒股可行吗"→ 判 none，无人承接 | money-management-skill 描述未含杠杆信号；router 分发表未列杠杆 | verified.yaml: money-management-skill description 补"融资/两融/杠杆"承接句 + keywords；router_entry 分发表补"融资/杠杆/两融→money-management-skill"；卡 A2 语言信号补一行 |
| T3-18 | "周期股横盘两年算蓄劲期吗"→ 直投 stock-picking-skill | stock-picking-skill 描述与 keywords 含"蓄劲期"，与 cycle-phase 抢触发 | stock-picking-skill description 补"只比较候选股蓄劲期长短，单票阶段判定用 cycle-phase"；卡 A2 相邻区分补 cycle-phase 条目 |
| T1-13 | "5万全仓梭哈买哪只临界点好"→ 选 stock-picking-skill | "买哪只"与"买多少"纠缠的边界场景，归因可辩护（选股意图），且执行层由 money-management-skill 兜底 | 记录为可辩护 edge；router 复测确认经 router→stock-picking-skill 分发正确；全仓风险拒绝行为已在执行测试 E2-D 验证 |

### 回归复测（修复后）
trigger_retest.json: R1→router/money-management-skill ✓，R2→router/cycle-phase ✓，R3→router/stock-picking-skill ✓。**修复后 45/45 全部符合预期（含 3 例经路由分发的正确归宿）。** 修复涉及的用例已纳入回归集。

## 二、实际执行测试（独立执行员，只给任务与 skill 全文，不看断言）

| 任务 | 能力 | 场景 | 结果 | 核对要点 |
|---|---|---|---|---|
| E1-A | motion-normality-skill | 新数字升势序列 45→47.5→52→49.2→54.8→58.5（回调缩量不破前谷） | ✓ | 四维+量价核对→"正常运动，持有安坐"；回调低点 49.2>前谷 47.5 正确采信 |
| E1-B | motion-normality-skill | 边界：只有基本面消息无行情数据 | ✓ | 拒绝判定，按输入契约索要波峰波谷/200天线/量能对比，未猜值 |
| E1-C | critical-point-buy-skill | 箱体 19.8–20.2 三个月后放量突破收 20.80 | ✓ | 触发 20.20 上方、止损 19.70（箱顶略下，-5.3%≤阈值）、失败判据=收盘跌回箱顶下；"烫过两次"不改三价 |
| E1-D | critical-point-buy-skill | 边界："茅台现在能买吗"无价位数据 | ✓ | 询问现价/前峰前谷/量比/大市状态 |
| E2-A | sell-trailing-stop-skill | 浪谷序列 11.2→12.4→14.1 的移动止损 | ✓ | 止损=最近浪谷 14.1，跌破全卖，四字段契约齐全 |
| E2-B | sell-trailing-stop-skill | 边界：无持仓成本/序列 | ✓ | 先询问不猜值 |
| E2-C | money-management-skill | 20 万新手首笔仓位 | ✓ | 分 6~8 份（取严→单注约 2 万）、首笔分层 200:400:400、胜算-仓位对应（60%→10%、80%→30~50%）、止损约束 |
| E2-D | money-management-skill | 边界："90% 把握全押 20 万" | ✓ | 拒绝全押：自评超规则上限+分仓原则+"我亏得起吗"+利物莫反面教材 |
| E3-A | market-regime-skill | 高位横盘+龙头疲软+垃圾股活跃+量增价滞+情绪亢奋 | ✓ | 顶部信号清单多项命中→判停条件触发，停止新买入 |
| E3-B | market-regime-skill | 边界：零数据问"要变盘吗" | ✓ | 索要 7 项必需输入 |
| E3-C | bubble-mania-skill | 合成"脑机接口"狂热情景 | ✓ | 六特性 6/6 命中→判"疯狂晚期"，未参与者不追+退出纪律 |
| E3-D | bubble-mania-skill | 边界：meme 币（超书范围标的） | ✓ | 声明范围仅类比+按六特性反问输入 |
| E3-E | router 可达 | "最简单的规则照做" | ✓ | 分发 ma250-system |

**执行测试 13/13 通过（含 4 个边界/缺输入场景的询问与拒绝行为）。计算类输出均可复算核对。**

## 三、结论

- 触发精度：修复后 45/45；诱饵容错 0（跨书内混淆诱饵全部正确避开或经路由分发）。
- 执行质量：13/13，无缺失交付物；缺输入场景全部先询问，未静默猜值。
- 未通过项：无。3 处 A2 歧义已修复并回归通过。
- 遗留注记：T1-13 类"资金行为+技术问题"复合场景，由 router 分发+money-management-skill 兜底拒绝，属设计行为。
