# 恐惧猎手 · Fear Hunter — Sentiment Dislocation Alpha v2.0

> **"当所有人恐惧时，找到恐惧过度的那一刻。"**

基于情绪-费率背离的 AI 逆向交易策略，专为 OKX Agent Trade Kit 设计。

## 策略简介

| 维度 | 说明 |
|------|------|
| **核心逻辑** | Fear & Greed Index × Funding Rate 双重背离捕捉 |
| **Alpha 来源** | 情绪-费率背离（Sentiment-Funding Rate Dislocation） |
| **适用账户** | 100 – 1,000 USDT 小资金账户 |
| **执行周期** | 4H |
| **主要标的** | BTC-USDT-SWAP / ETH-USDT-SWAP |
| **杠杆上限** | BTC 3x / ETH 2x |

## 信号矩阵

|  | 费率 < -0.01%（空头拥挤） | 费率 > 0.05%（多头拥挤） |
|--|--------------------------|--------------------------|
| **F&G < 25（恐惧）** | ✅ **双重恐惧 → 做多** | ⚠️ 矛盾信号 → 观望 |
| **F&G > 75（贪婪）** | ⚠️ 矛盾信号 → 观望 | ✅ **双重贪婪 → 做空** |

## 快速开始

```bash
# 1. 安装 Agent Trade Kit
npm install -g @okx_ai/okx-trade-mcp @okx_ai/okx-trade-cli

# 2. 配置模拟盘
okx config init

# 3. 查看行情验证
okx market ticker BTC-USDT

# 4. 查看资金费率
okx market funding-rate BTC-USDT-SWAP
```

详细策略文档：[SKILL.md](./SKILL.md)

## 30 天回测表现

| # | 日期 | 方向 | 入场价 | 出场价 | 收益 |
|---|------|------|--------|--------|------|
| 1 | 3/27 | LONG | 66,984 | 67,050 | ±0%（追踪止损保本） |
| 2 | 4/5  | LONG | 69,923 | 73,900 | **+4.95%** |
| 3 | 4/15 | LONG | 74,063 | — | 持仓中 |

累计收益 ≈ +5%，最大回撤 < 1%，83% 时间在等待。

## 演示网站

📖 **[在线教程 & 实操演示](https://fear-hunter.github.io/fear-hunter-skill/)**

## 文件说明

| 文件 | 说明 |
|------|------|
| `SKILL.md` | 完整策略文档（OKX Skill 广场提交格式） |
| `index.html` | 实操教程 — 深色主题交互式长文 |
| `tweet-draft.md` | 推文线程草稿（#OKXAI交易大赛） |

## 相关资源

- 🔗 [OKX Agent Trade Kit](https://github.com/okx/agent-trade-kit)
- 📦 npm: `@okx_ai/okx-trade-mcp` / `@okx_ai/okx-trade-cli`
- 📚 [官方文档](https://www.okx.com/docs-v5/agent_zh/)
- 🎓 [AI 101 课程](https://www.okx.com/zh-hans/ai-101)
- 💬 [Telegram 社群](https://t.me/OKX_AgentKit)

## License

MIT

---

**#OKXAI交易大赛** | @okxchinese
