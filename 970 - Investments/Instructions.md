# OpenClaw 投资组合操作规范

本文档是 OpenClaw 处理投资交易指令的行为规范。每次执行交易相关操作时，严格遵守以下规则。

---

## 目录结构

```
970 - Investments/
├── 971 - Portfolio/
│   ├── Dashboard.md          # 日常查看入口
│   └── Portfolio.base        # Bases 数据库定义
├── 972 - Assets/             # 每个持仓资产一个笔记
│   └── <SYMBOL>.md
├── 973 - Transactions/
│   └── Transaction-Log.md    # 交易流水日志
├── 974 - Snapshots/          # 组合快照，用于期间收益和 YTD 起点
│   └── YYYY-MM-DD.md
└── Instructions.md           # 本文件
```

---

## 一、收到交易指令时的执行流程

用户发出自然语言交易指令后，按以下顺序执行：

1. **解析指令**：提取关键字段（见下方字段定义）
2. **确认歧义**：如有字段缺失或不明确，先向用户确认，不要猜测
3. **更新资产笔记**：修改 `972 - Assets/<SYMBOL>.md` 的 YAML
4. **追加交易记录**：在 `973 - Transactions/Transaction-Log.md` 表格末尾追加一行
5. **维护快照/净入金口径**：如涉及期间表现起点或外部出入金，更新 `974 - Snapshots/` 中对应快照字段
6. **回复用户**：简短确认已完成，列出变更摘要

---

## 二、交易类型与字段

### 支持的操作类型

| 操作 | 说明 |
|------|------|
| Buy | 买入 |
| Sell | 卖出 |
| Dividend | 股息/分红到账 |
| Split | 股票拆分 |
| Fee | 独立手续费（非交易附带） |
| Deposit | 现金入金 |
| Withdraw | 现金出金 |
| Interest | 现金利息到账 |
| FX | 货币兑换 |
| Initial Position | 初始持仓快照，仅用于建立真实组合起点 |

### 必填字段

| 字段 | 说明 | 示例 |
|------|------|------|
| 日期 | 交易日期，YYYY-MM-DD | 2026-04-22 |
| 操作 | Buy / Sell / Dividend / Deposit / Withdraw 等 | Buy |
| 符号 | 资产 symbol，必须与笔记文件名一致 | AAPL |
| 数量 | 买入正数，卖出负数 | +50 / -30 |
| 价格 | 每股/每单位价格 | 228.50 |
| 货币 | USD / HKD / CNY / USDT 等 | USD |
| 平台 | 经纪商或交易所 | 雪盈证券 |

### 选填字段

| 字段 | 默认值 | 说明 |
|------|--------|------|
| 手续费 | 0.00 | 单独列出，不计入总金额 |
| 备注 | 空 | 交易理由或说明 |

---

## 三、avg_cost 计算规则

### Buy（买入）

使用加权平均成本法：

```
新 avg_cost = (旧 avg_cost × 旧 quantity + 买入价格 × 买入数量) / (旧 quantity + 买入数量)
新 quantity = 旧 quantity + 买入数量
```

### Sell（卖出）

卖出不改变 avg_cost，只减少持仓数量：

```
新 avg_cost = 旧 avg_cost（不变）
新 quantity = 旧 quantity - 卖出数量
```

如果卖出后 quantity = 0，保留笔记但 quantity 置为 0，avg_cost 保持不变（备查历史成本）。

### Dividend（分红）

不修改 quantity 和 avg_cost，只追加交易记录。

### Split（拆股）

用户需提供拆股比例（如 4:1）：

```
新 quantity = 旧 quantity × 拆股倍数
新 avg_cost = 旧 avg_cost / 拆股倍数
```

### Cash（现金）

现金也作为 `asset` 管理，category 为 `cash`。

现金资产规则：

```
symbol = <CURRENCY>-CASH，如 USD-CASH、HKD-CASH、CNY-CASH
quantity = 当前现金余额
avg_cost = 1
current_price = 1
currency = 对应货币
```

现金操作规则：

| 操作 | 对现金 quantity 的影响 | avg_cost | current_price | 说明 |
|------|------------------------|----------|---------------|------|
| Deposit | 增加 | 保持 1 | 保持 1 | 入金 |
| Withdraw | 减少 | 保持 1 | 保持 1 | 出金 |
| Interest | 增加 | 保持 1 | 保持 1 | 现金利息 |
| Fee | 减少 | 保持 1 | 保持 1 | 单独现金费用 |
| FX | 同时减少卖出币种现金、增加买入币种现金 | 保持 1 | 保持 1 | 需记录两个现金资产 |

现金不能产生浮盈，因此 `avg_cost` 和 `current_price` 固定为 1。Dashboard 中 `quantity * current_price` 即现金余额。

如果同一币种现金分布在多个平台，资产 YAML 只记录合计数量，正文 `平台分布` 表记录各平台金额。更新现金时必须同步维护平台分布。

---

## 四、资产笔记操作规范

### 文件命名

- 文件名 = symbol，全大写，如 `AAPL.md`、`BTC.md`
- 如果 symbol 包含 `/` 等不能用于文件名的字符，文件名使用安全替代写法，如 `BRK-B.md`，但 YAML `symbol` 和交易日志仍保留真实 symbol `BRK/B`
- 现金文件名 = `<CURRENCY>-CASH.md`，如 `USD-CASH.md`
- 路径：`972 - Assets/<SYMBOL>.md`

### YAML 标准格式

```yaml
---
type: asset
category: stock        # stock / crypto / fund / bond / etf / cash
symbol: AAPL
quantity: 150
avg_cost: 180.50
current_price: 225.30  # 手动更新，或用户要求时拉取行情
currency: USD
last_updated: 2026-04-22
---
```

- 修改 YAML 后必须更新 `last_updated` 为当天日期
- 不要修改笔记正文内容（YAML 以下部分）
- 现金资产例外：允许维护正文中的 `平台分布` 表，用于记录不同平台的现金余额

### 现金 YAML 标准格式

```yaml
---
type: asset
category: cash
symbol: USD-CASH
quantity: 1444
avg_cost: 1
current_price: 1
currency: USD
last_updated: 2026-04-22
---
```

### 新资产处理

如果 `972 - Assets/` 下不存在对应 symbol 的笔记：
1. 告知用户该资产笔记不存在
2. 询问是否自动创建
3. 确认后按标准格式创建，category 由用户指定或根据 symbol 合理推断

---

## 五、Transaction-Log.md 追加规范

- 在表格**最后一行下方**追加新行，不改动任何已有内容
- 总金额 = 数量（绝对值）× 价格，卖出时为负数
- 现金记录中，价格固定为 1，总金额等于现金变动金额
- 现金出金、费用等减少现金的操作，数量和总金额都记录为负数
- 保持 Markdown 表格格式对齐（列之间用 `|` 分隔）
- 示例行格式：

```
| 2026-04-22 | Buy | AAPL | +50 | 228.50 | USD | 11425.00 | 雪盈证券 | 5.00 | 看好AI进展 |
```

现金示例：

```
| 2026-04-22 | Deposit | USD-CASH | +1000 | 1.00 | USD | 1000.00 | IBKR | 0.00 | 入金 |
| 2026-04-22 | Withdraw | USD-CASH | -500 | 1.00 | USD | -500.00 | IBKR | 0.00 | 出金 |
| 2026-04-22 | Interest | USD-CASH | +3.25 | 1.00 | USD | 3.25 | IBKR | 0.00 | 现金利息 |
```

---

## 六、Dashboard 汇总维护规范

`971 - Portfolio/Dashboard.md` 中的 `组合汇总` 由 DataviewJS 自动计算，读取 `972 - Assets/` 下所有 `type: asset` 的 YAML。

Dashboard 自动计算：

- Cost Basis
- Current Value
- Unrealized Gain
- Portfolio Return
- Period Performance

汇总计算规则：

```
Cost Basis = Σ(quantity × avg_cost)
Current Value = Σ(quantity × current_price)
Unrealized Gain = Σ((current_price - avg_cost) × quantity)
Portfolio Return = Unrealized Gain / Cost Basis
```

注意：Bases 可以对单列做 Sum 汇总，但不要对各资产的 `Return %` 做求和或平均。组合总收益率必须使用 `Unrealized Gain / Cost Basis`。

### Period Performance

Dashboard 中的 `Period Performance` 使用 `974 - Snapshots/` 中标记为 `period_role: ytd_start` 的快照作为起点。

2026 年规则：

- 使用 `974 - Snapshots/2026-04-22.md` 作为 2026 起点
- Dashboard 显示为从 2026-04-22 起算的期间表现

之后年份规则：

- 每年年末保存当年最后一个组合快照
- 下一年使用上一年年末快照作为 YTD 起点

期间收益计算规则：

```
Net Contributions = 起点之后 Deposit - Withdraw（如有 FX，只计算外部净入金，不把内部换汇计为入金）
Period P/L = Current Value - Start Value - Net Contributions
Period Return = Period P/L / Start Value
```

每次新增、删除或修改资产 YAML 后，Dashboard 会由 DataviewJS 自动刷新。如果 Obsidian 未自动刷新，重新打开 Dashboard 或触发 Dataview 刷新。

涉及外部入金/出金时，必须更新起点快照中的 `net_contributions_since_start`，否则 `Period Performance` 会失真。内部交易、内部换汇、买卖资产不计入外部净入金。

---

## 七、边界情况处理

| 情况 | 处理方式 |
|------|----------|
| 卖出数量超过当前持仓 | 停止执行，告知用户当前持仓数量，请用户确认 |
| symbol 不存在对应笔记 | 停止执行，询问是否创建新资产笔记 |
| 字段信息不完整 | 停止执行，列出缺少的字段，请用户补充 |
| 货币与笔记中 currency 不一致 | 提示用户确认，不自动转换汇率 |
| 用户要求更新当前价格 | 仅更新 `current_price` 和 `last_updated`，不追加交易记录 |
| 现金出金、费用超过当前现金余额 | 停止执行，告知用户当前现金余额，请用户确认 |
| FX 缺少卖出币种、买入币种、金额、汇率或平台 | 停止执行，列出缺少字段，请用户补充 |
| 同一币种现金分布在多个平台 | 更新合计 YAML，同时更新正文平台分布 |

---

## 八、回复格式

执行完成后，回复格式如下（简洁）：

```
已完成：
- Transaction-Log：追加 1 行（Buy AAPL +50 @ 228.50 USD）
- AAPL.md：quantity 100 → 150，avg_cost 175.20 → 179.45
```

如有计算过程需要验证，附上 avg_cost 的计算步骤。
