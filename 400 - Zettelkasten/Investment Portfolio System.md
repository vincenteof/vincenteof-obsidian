---
tags: [investment, portfolio, system, active]
created: 2026-04-21
---

# Investment Portfolio System

投资组合追踪系统的设计方案与使用规范。

---

## 目录结构

```
Investments/
  _Portfolio.md          ← 当前持仓总览快照
  _Accounts.md           ← 账户清单（交易所 / 券商 / 钱包）
  transactions/
    BTC.md               ← BTC 所有交易记录（表格追加）
    ETH.md
    NVDA.md
  assets/
    crypto/
      BTC.md             ← BTC 认知笔记（逻辑、观点演变）
      ETH.md
    stocks/
      NVDA.md
      AAPL.md
```

---

## 各文件用途

| 文件 | 用途 |
|------|------|
| `_Portfolio.md` | 当前持仓快照：持有什么、多少仓位、均价。"现状"。 |
| `_Accounts.md` | 账户清单，作为交易记录 `account` 字段的参考表，防止命名不一致 |
| `transactions/<Asset>.md` | 按资产分文件，每笔交易追加一行表格 |
| `assets/<category>/<Asset>.md` | 认知笔记：买入逻辑、观点演变、目标仓位、相关阅读 |

---

## 交易记录格式

每个 `transactions/<Asset>.md` 使用表格追加：

```markdown
| date | action | amount | price | account | fee | note |
|------|--------|--------|-------|---------|-----|------|
| 2026-04-21 | buy | 0.1 | 84000 | Binance | 12 | 定投 |
| 2026-03-15 | buy | 0.05 | 79000 | Binance | 6 | |
| 2026-02-01 | sell | 0.08 | 95000 | Binance | 10 | 减仓 |
```

字段说明：
- `amount`：数量（crypto 单位为币；股票单位为股）
- `price`：成交价（USD 或 CNY，保持一致）
- `fee`：手续费（同货币）
- `note`：交易理由或简短备注

---

## 设计原则

**按资产分文件，表格追加。**

原因：资产种类有限（10-20 个），但每个资产的交易次数持续增加。"我的 BTC 一共怎么操作的"是最自然的查询视角。跨时间查询用 Dataview 的 `date` 列处理。

**transactions 记流水，assets 记认知。**

`assets/` 里的笔记不记价格，记的是：
- 为什么买这个资产
- 目标仓位逻辑
- 观点什么时候变了，为什么
- 相关文章、数据来源

几年后这些文件会成为投资认知演变的轨迹记录。

---

## TODO

- [ ] 确认方案后，按结构建立 `Investments/` 目录并开始使用

---

*方案由 Alfred 设计，2026-04-21*
