# Stage 4 压力测试摘要

> 数据来源：归档 `审计过程/.cangjie/test-prompts/`（8 套用例）、`审计过程/.cangjie/test-results/`（逐项评分报告与回归复测）、`审计过程/PIPELINE_STATE.md`（阶段 4 记录）。
> 结构检查为 2026-10-29 在本仓库实测；触发盲测与执行测试的结论引自上述归档报告，**本次未复跑**。

## 测试范围

本包是《炒股的智慧：在华尔街炒股为生的体验》（陈江挺，2016 第四版）单本书的蒸馏产物，1 个 bundle、14 项能力单元，两种输出形态：

- `single/`：1 个入口（`stock-trading-wisdom-skill`），14 张能力卡内嵌在 `references/capabilities/`。
- `pack/`：8 个可发现入口 = 1 个来源路由入口（`stock-trading-wisdom-skill-router`）+ 7 个晋级独立 skill；其余 7 项能力作为路由卡放在 router 的 `references/capabilities/` 内。

触发用例随 skill 目录分发，仓库内共 **9 份 `test-prompts.json`**（`pack/` 8 个入口目录各 1 份 + `single/` 入口 1 份），**合计 61 条**用例：

| 用例集 | 归属入口 | 条数 | should_trigger | should_not_trigger | edge_case |
|---|---|---|---|---|---|
| `motion-normality` | `pack/motion-normality-skill` | 7 | 3 | 2 | 2 |
| `critical-point-buy` | `pack/critical-point-buy-skill` | 6 | 3 | 2 | 1 |
| `sell-trailing-stop` | `pack/sell-trailing-stop-skill` | 6 | 3 | 2 | 1 |
| `money-management` | `pack/money-management-skill` | 6 | 3 | 2 | 1 |
| `stock-picking` | `pack/stock-picking-skill` | 6 | 3 | 2 | 1 |
| `market-regime` | `pack/market-regime-skill` | 6 | 3 | 2 | 1 |
| `bubble-mania` | `pack/bubble-mania-skill` | 6 | 3 | 2 | 1 |
| `stock-trading-wisdom-skill-router` | `pack/stock-trading-wisdom-skill-router` | 9 | 7 | 2 | 0 |
| `stock-trading-wisdom-skill` | `single/stock-trading-wisdom-skill` | 9 | 7 | 2 | 0 |
| **合计** | **9 份文件** | **61** | **35** | **18** | **8** |

- 覆盖类型：`should_trigger`（该触发时要触发）、`should_not_trigger`（诱饵题，不该触发时要沉默或转交相邻卡）、`edge_case`（边界/缺输入场景）。
- `output_case`：**0 条，未以 JSON 形式提供**。执行类测试（13 个任务场景，含 4 个边界场景）以叙述形式记录在根目录 `test-results.md` 第二部分，不随 `test-prompts.json` 分发。
- `single/stock-trading-wisdom-skill/test-prompts.json` 与 `pack/stock-trading-wisdom-skill-router/test-prompts.json` 逐字节相同（同一份入口级用例的两个副本）；按内容去重后实际不同用例为 **52 条**（`should_trigger` 28 / `should_not_trigger` 16 / `edge_case` 8）。

## 结构检查

2026-10-29 在本仓库实测，结果如下：

| 检查项 | 范围 | 结果 |
|---|---|---|
| JSON 可解析性 | 12 个 JSON 文件（9 份 `test-prompts.json` + `pack/BUILD_MANIFEST.json` + `pack/capability-destinations.json` + `single/stock-trading-wisdom-skill/BUILD_MANIFEST.json`） | 12/12 可解析，0 失败 |
| YAML frontmatter | 9 个 `SKILL.md` | 9/9 有 frontmatter 且含 `name` 字段，`name` 与所在目录同名 |
| 六段完整性（R/I/A1/A2/E/B） | 42 张能力卡（`bundle/cards` 14 + `single/.../capabilities` 14 + `pack/.../router/references/capabilities` 14） | 42/42 六段齐全，0 缺段 |
| 用例字段 | 61 条用例 | 每条含 `id`/`type`/`prompt`/`expected_behavior`/`notes` |
| 候选材料 | `candidates/` 5 个文件（frameworks / principles / cases / counter-examples / glossary） | 与归档一致，纯文本 |

未做的检查（如实记录）：未逐条把能力卡正文与原文重新比对，未复算卡内数字（归档阶段 1.5 做过数字抽查，64/65 一致，不一致的 1 处见下）。

## 结果

- skills: 8（`pack/` 可发现入口）；`single/` 入口 1 个；能力单元共 14 项
- test_json: 9 份 `test-prompts.json` 共 61 条用例（按内容去重后 52 条）；另有 3 份构建清单 JSON（`pack/BUILD_MANIFEST.json`、`pack/capability-destinations.json`、`single/stock-trading-wisdom-skill/BUILD_MANIFEST.json`）
- 通过情况（引自归档报告，本次未复跑）：
  - 触发盲测：首轮 45 例中 **42 例符合预期，3 例触发歧义**（T2-12 融资杠杆无人承接、T3-18 蓄劲期误投选股卡、T1-13 复合场景归属可辩护）。3 例均按"修 skill 不修测试"处理（补 description/keywords、补相邻区分条目），回归复测后 **45/45 全部符合预期**，诱饵容错 0。
  - 执行测试：**13/13 通过**，含 4 个边界/缺输入场景，全部先询问补齐、未静默猜值。
  - 未通过项：无。
  - 遗留注记："资金行为 + 技术问题"的复合场景由路由入口分发、再由资金管理卡兜底拒绝，属设计行为。
  - 回归最小集：R1→router/money-management-skill、R2→router/cycle-phase、R3→router/stock-picking-skill（原始复测记录 `trigger_retest.json` 未随仓库发布，结论见根目录 `test-results.md`）。

## 可接入 darwin-skill 的后续动作

1. **回归样本**：61 条用例（按内容去重后 52 条）可直接作为回归集。`should_not_trigger` 的 18 条（去重后 16 条）是本书内部的"跨卡诱饵"，适合检验路由分发是否抢触发；建议连同归档的 3 条回归复测用例一起作为每次改 description 后的最小回归门。
2. **判定标签映射**：用例的 `type` 字段可直接映射为 darwin 的判定标签（`should_trigger` → 命中、`should_not_trigger` → 静默或转交、`edge_case` → 询问/拒绝），无需改结构；`expected_behavior` 已是可核对的自然语言断言，可作为评分 rubric 的初稿。
3. **补 `output_case`**：现有用例只覆盖"是否触发/是否转交"，执行质量靠叙述报告。若接入 darwin 自动评分，建议把根目录 `test-results.md` 第二部分的 13 个执行场景（输入、期望交付物、核对要点）结构化为 `output_case` 用例，尤其是 4 个缺输入场景——它们最容易在回归中退化。
4. **需先复跑**：本仓库当前只有归档报告，没有本次复跑记录。接入 darwin 前应先在目标宿主/模型上跑一遍，用新结果替换报告口径，避免把旧结论当作当前基线。
5. **结构门可脚本化**：本次的 JSON 可解析、frontmatter 存在、六段齐全三项检查可直接固化为提交前脚本，防新增卡/改卡时漏段。
