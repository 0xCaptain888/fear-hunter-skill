# OKX AI 交易大赛 — 内容创作推文线程

> 话题标签: #OKXAI交易大赛
> 提及: @okxchinese
> 主题: 恐惧猎手 — 用 AI + Agent Trade Kit 搭建逆向交易策略

---

【Tweet 1】Hook

我用 AI 搭建了一套名叫"恐惧猎手"的逆向交易策略。

核心逻辑：当市场极度恐惧 + 空头拥挤时做多，当市场极度贪婪 + 多头拥挤时做空。

不是 PPT 概念，是在 OKX 模拟盘上真枪实弹跑出来的。

从安装到第一笔策略交易，全程实操记录 👇

#OKXAI交易大赛

---

【Tweet 2】安装 Agent Trade Kit（60 秒搞定）

```
npm install -g @okx_ai/okx-trade-mcp @okx_ai/okx-trade-cli
```

安装后查行情，连 API Key 都不需要：

> $ okx market ticker BTC-USDT
> last: 74,789 (+5.31%)

再看资金费率：

> $ okx market funding-rate BTC-USDT-SWAP
> fundingRate: -0.006%（空头付费）

一分钟内拿到策略需要的所有数据。

#OKXAI交易大赛

---

【Tweet 3】策略核心：双重恐惧矩阵

恐惧猎手的信号不是 EMA 交叉那种人人都会的东西。

它看两个东西：
1. Fear & Greed Index（情绪有多恐惧？）
2. 资金费率（空头有多拥挤？）

当两者同时极端 = "双重恐惧" → 做多
当两者同时极端 = "双重贪婪" → 做空

当前市场：F&G = 23，连续 30 天极度恐惧，费率为负。

正好触发做多信号。

#OKXAI交易大赛

---

【Tweet 4】AI 推理 vs 规则引擎

这策略不是简单的 if-else。

市场同时告诉你：
- 情绪：极度恐惧
- 价格：在涨（70,500 → 74,000）
- 费率：空头还在拥挤

矛盾吗？人类会纠结。

但 AI 能推理出：价格在恐惧中上涨 + 空头没投降 = 轧空燃料还在堆积 → 继续做多。

这就是为什么这策略必须用 AI 跑，不能用规则引擎。

#OKXAI交易大赛

---

【Tweet 5】模拟盘实战：开仓

在 OKX Demo 模式下执行策略交易：

```
$ okx --demo swap place --instId BTC-USDT-SWAP \
    --side buy --ordType market --sz 1 \
    --posSide long --tdMode isolated
Order placed: OK ✅
```

入场价 74,063，止损 72,500，止盈 76,000。

同一时间 ETH 和 SOL 被过滤器拦截 — 费率不够极端，跳过。

3 个标的只做 1 个，80% 时间不交易，这才是策略纪律。

#OKXAI交易大赛

---

【Tweet 6】回测：过去 30 天的表现

用真实 F&G 数据 + BTC 日线做了回测：

交易 #1（3/27）：66,984 入场 → 保本出场（追踪止损保护）
交易 #2（4/5）：69,923 入场 → 73,900 止盈（+4.95%）⭐
交易 #3（4/15）：74,063 入场 → 持仓中

30 天 3 笔交易，83% 时间在等待。
累计收益约 +5%，最大回撤 <1%。

不追求交易频率，只在极端时刻出手。

#OKXAI交易大赛

---

【Tweet 7】安全机制 + 风控体系

策略安全：
- API Key 本地保存，AI 无法访问密钥
- 模拟盘模式零风险测试
- MIT 开源，代码可审计

策略风控：
- 单笔最大亏损 2%
- 日回撤 4% 暂停 8 小时
- 周回撤 8% 暂停至下周
- 连亏 3 笔自动缩仓

100 USDT 的账户也能跑，最多亏 2U 一笔。

#OKXAI交易大赛

---

【Tweet 8】完整教程 + SKILL.md

我的完整教程和策略文件：
- 实操教程（HTML 长文）
- SKILL.md — 恐惧猎手策略 v2.0
- 30 天历史回测数据
- 模拟盘 Live Demo 交易记录

Agent Trade Kit 资源：
🔗 github.com/okx/agent-trade-kit
📦 npm: @okx_ai/okx-trade-mcp
📚 okx.com/docs-v5/agent_zh/
💬 t.me/OKX_AgentKit

欢迎 @okxchinese 社区一起交流 AI 交易策略！

#OKXAI交易大赛

---

## 配图建议

| 推文 | 配图内容 |
|------|---------|
| Tweet 1 | 教程 Hero 区域截图 + "恐惧猎手" 标题 |
| Tweet 2 | 终端安装命令 + BTC 行情 + 资金费率查询 |
| Tweet 3 | 2×2 情绪-费率矩阵图（从 SKILL.md 截取） |
| Tweet 4 | AI 推理报告截图（ASCII 框图） |
| Tweet 5 | 模拟盘开仓命令 + 持仓确认截图 |
| Tweet 6 | 回测 3 笔交易记录 + 收益汇总表 |
| Tweet 7 | 风控参数表格 + 安全架构要点 |
| Tweet 8 | GitHub 仓库 + Skill 广场页面拼图 |

- 尺寸: 1200x675px（16:9）
- 风格: 深色终端截图 + OKX 黄色(#FCD535)高亮
- 终端美化: carbon.now.sh，One Dark 主题
