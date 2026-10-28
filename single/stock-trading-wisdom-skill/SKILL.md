---
name: stock-trading-wisdom-skill
description: |
  《炒股的智慧》（陈江挺，2016第四版）全书蒸馏：一套以人性与概率为核心的股票交易决策体系。覆盖：股票运动正常性判定（危险信号）、临界点买卖决策、卖点与移动止损、资金管理与仓位、选股三步过滤、大市判定、泡沫识别、周期阶段定位、心理纪律自检、学股阶段自测、合理回报与资产配置、250天线极简系统、基本面快速审视、大户操纵痕迹识别共 14 项能力。适用于辅助 A 股/美股个股与大市的投资分析决策；不用于荐股、预测具体点位或代客下单。Trigger: 炒股的智慧、陈江挺、临界点、止损、截短亏损让利润奔跑、败而不倒、久赌必赢、股疯/泡沫、大市。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: single
  cangjie.bundle-id: bundle.stock-trading-wisdom-skill
  cangjie.capability-count: 14
  cangjie.entrypoint-count: 1
---
# 炒股的智慧：在华尔街炒股为生的体验（第四版） — 全书能力入口

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 预测具体点位、荐股、代客下单或任何实盘执行
- 无行情数据（价格/量能/均线）时的纯基本面估值建模
- 期货、期权等衍生品的策略设计（书中仅以期货经验佐证股票方法）
- 人生理财哲学咨询（见附录《金钱的反思》，属背景参考）

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 败而不倒：保本第一，本金没了游戏结束（快速止损+别一次下注太多）
2. 炒股是艺术不是科学：只能提高获胜概率（>50%），不能消除不确定性
3. 截短亏损，让利润奔跑：一见不对即刻止损，有利润让利润从小跑成大
4. 买卖全在临界点：入场触发价与止损价同时确定，跌回临界点之下即离场
5. 大市不好时，别买任何股票：用指数当一只股票看它的运动阶段
6. 市场从来不会错：出错的只有你自己，一有不对即刻认错
7. 善战者无赫赫之功：分仓对个股风险、轻仓对大市风险，集小胜为大胜

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 判断当前持仓个股走势是否健康、该不该继续持有；区分正常回调与出货危险信号（洗盘还是出货）；持仓异动（放量长上影、暴升回落、跌破支撑/均线）后的离场判定；危险信号离场后的重入观察 | references/capabilities/motion-normality-skill.md | references/capabilities/sell-trailing-stop-skill.md、references/capabilities/cycle-phase-skill.md、references/capabilities/market-regime-skill.md、references/capabilities/manipulation-signs-skill.md |
| 判断某个图形突破/回调能否买入（升势破前峰、放量破阻力线、回踩支撑、倒头肩破颈线、假跌破弹回）；买入前同步确定止损价与失败判据（跌破何价即离场）；拦截"跌了很多就买""有好消息/专家推荐就买"类入场冲动；升势A/B点两段建仓的路径安排（A点试探、B点补足） | references/capabilities/critical-point-buy-skill.md | references/capabilities/motion-normality-skill.md、references/capabilities/sell-trailing-stop-skill.md、references/capabilities/money-management-skill.md、references/capabilities/stock-picking-skill.md、references/capabilities/ma250-system-skill.md |
| 判断持仓个股的卖出时机与卖出价位；设置并逐级上移移动止损/跟踪止损；处理浮盈回吐与利润保护（别让利润变亏损）；识别短期暴升与量增价滞后的兑现时机；决定卖出后的重新买入条件 | references/capabilities/sell-trailing-stop-skill.md | references/capabilities/motion-normality-skill.md、references/capabilities/money-management-skill.md、references/capabilities/psych-discipline-skill.md |
| 计算单笔交易应投入的资金规模与股数；规划分批建仓与逐级加码序列；评估风险报酬比是否值得开仓；决定持股集中度与仓位动态调节（睡眠测试）；判断能否补仓/摊平 | references/capabilities/money-management-skill.md | references/capabilities/critical-point-buy-skill.md、references/capabilities/return-allocation-skill.md、references/capabilities/sell-trailing-stop-skill.md |
| 决定现在该买什么股票（对象筛选）；比较哪些板块/类别更强势更值得买；同板块多只候选股排序或二选一；判断"跌了很多的便宜股"能不能买；识别板块内的龙头股 | references/capabilities/stock-picking-skill.md | references/capabilities/market-regime-skill.md、references/capabilities/critical-point-buy-skill.md、references/capabilities/fundamental-check-skill.md |
| 判定当前是牛市还是熊市；决定大盘能不能入场、该不该清仓；判断大市是否见顶/见底；解释指数与个股表现背离（怀疑指数失真）；为选股/买入决策提供大市否决开关 | references/capabilities/market-regime-skill.md | references/capabilities/stock-picking-skill.md、references/capabilities/bubble-mania-skill.md、references/capabilities/motion-normality-skill.md |
| 判断热点标的或板块是不是泡沫（疯）；决定是否参与泡沫行情及用多大仓位参与；判断泡沫所处阶段与退出时机（公众识破前离场）；识别疯狂晚期信号（几天暴涨一倍、盲目抢购、骗案层出不穷）；复盘历史泡沫案例并映射当下行情 | references/capabilities/bubble-mania-skill.md | references/capabilities/market-regime-skill.md、references/capabilities/motion-normality-skill.md |
| 判断个股当前处于蓄劲/爬坡/疲劳/下坡哪个时期；确认蓄劲期向爬坡期的真升势起点（放量突破阻力线）；获取各阶段的操作许可（买/持/卖/观望/不碰）；定位长期持股的离场触发（跌穿均线及支撑线） | references/capabilities/cycle-phase-skill.md | references/capabilities/motion-normality-skill.md、references/capabilities/critical-point-buy-skill.md、references/capabilities/market-regime-skill.md |
| 交易前自查这单该不该下（买入理由、书面计划、内心声音甄别）；持仓中核对执行纪律（止损执行、到价当机立断、别摊平、别频繁交易、别让利润变亏损）；识别恐惧/贪婪/希望三障碍的当下症状（该进反出、情绪加码、拒绝止损合理化）；亏损或违规后的归因复盘（违反了哪条规则、不找替罪羊） | references/capabilities/psych-discipline-skill.md | references/capabilities/sell-trailing-stop-skill.md、references/capabilities/money-management-skill.md |
| 自评处于学股哪个阶段、什么水平、还要学多久；问该阶段先练什么、典型错误怎么纠正；大亏或大赚后大亏之后，想知道这在学习路径中意味着什么；在几套方法间来回切换、怀疑是方法问题还是自己问题 | references/capabilities/stage-selftest-skill.md | references/capabilities/psych-discipline-skill.md、references/capabilities/money-management-skill.md |
| 判断个股异动是不是庄家/主力做盘（假跌破、假突破、砸盘吸筹、诱多）；判断放量滞涨、无消息暴升是不是在出货、该不该跑；判断股评推荐该不该跟（找最后傻瓜还是联手推升初期）；低位温和放量缓涨是不是有人在悄悄吸筹 | references/capabilities/manipulation-signs-skill.md | references/capabilities/motion-normality-skill.md、references/capabilities/critical-point-buy-skill.md、references/capabilities/bubble-mania-skill.md |
| 设定合理的年化回报预期（多少算正常、能不能指望翻倍）；决定投入股市的资金总盘子与仓位哲学（满仓还是轻仓）；在"赌一把/走专业道路/稳妥投资"之间做战略分流；规划分散度（集中一只还是分散多只、单票占比）；挑选基金/投资管理人；校准"专职炒股/财务自由"的职业预期 | references/capabilities/return-allocation-skill.md | references/capabilities/money-management-skill.md、references/capabilities/market-regime-skill.md |
| 用250天线规则给出极简买卖动作（买/持有/卖/不参与）；判断某股当前在年线上方还是下方、可否按系统参与；为新手配置一套四要素齐备、可照做的最小操作系统；核查自己是否按既定均线规则执行（没找不做的理由） | references/capabilities/ma250-system-skill.md | references/capabilities/critical-point-buy-skill.md、references/capabilities/sell-trailing-stop-skill.md、references/capabilities/money-management-skill.md |
| 快速核对某公司基本面（干什么的、干得怎么样）；评估营收与盈利增长的质量（真假增速、背离调查）；检查一家公司有无股价上涨的三因素（盈利增长/新产品/回购）；识别财报水分红旗（收入确认、折旧、会计游戏）；买点决策前做底层校验 | references/capabilities/fundamental-check-skill.md | references/capabilities/stock-picking-skill.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 用户提供的数据不足以支撑判定（如无任何价格/量能信息）时，先询问补齐，不得静默猜值
- 用户要求保证收益、稳赚或内幕消息时，说明本体系为概率框架并拒绝
- 分析结论与用户持仓立场冲突时如实输出，不得迎合
