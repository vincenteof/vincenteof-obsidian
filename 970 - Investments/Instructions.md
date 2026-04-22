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
└── Instructions.md           # 本文件
```

---

## 一、收到交易指令时的执行流程

用户发出自然语言交易指令后，按以下顺序执行：

1. **解析指令**：提取关键字段（见下方字段定义）
2. **确认歧义**：如有字段缺失或不明确，先向用户确认，不要猜测
3. **更新资产笔记**：修改 `972 - Assets/<SYMBOL>.md` 的 YAML
4. **追加交易记录**：在 `973 - Transactions/Transaction-Log.md` 表格末尾追加一行
5. **回复用户**：简短确认已完成，列出变更摘要

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

### 必填字段

| 字段 | 说明 | 示例 |
|------|------|------|
| 日期 | 交易日期，YYYY-MM-DD | 2026-04-22 |
| 操作 | Buy / Sell / Dividend 等 | Buy |
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

---

## 四、资产笔记操作规范

### 文件命名

- 文件名 = symbol，全大写，如 `AAPL.md`、`BTC.md`
- 路径：`972 - Assets/<SYMBOL>.md`

### YAML 标准格式

```yaml
---
type: asset
category: stock        # stock / crypto / fund / bond / etf
symbol: AAPL
name: Apple Inc.
quantity: 150
avg_cost: 180.50
current_price: 225.30  # 手动更新，或用户要求时拉取行情
currency: USD
last_updated: 2026-04-22
---
```

- 修改 YAML 后必须更新 `last_updated` 为当天日期
- 不要修改笔记正文内容（YAML 以下部分）

### 新资产处理

如果 `972 - Assets/` 下不存在对应 symbol 的笔记：
1. 告知用户该资产笔记不存在
2. 询问是否自动创建
3. 确认后按标准格式创建，category 由用户指定或根据 symbol 合理推断

---

## 五、Transaction-Log.md 追加规范

- 在表格**最后一行下方**追加新行，不改动任何已有内容
- 总金额 = 数量（绝对值）× 价格，卖出时为负数
- 保持 Markdown 表格格式对齐（列之间用 `|` 分隔）
- 示例行格式：

```
| 2026-04-22 | Buy | AAPL | +50 | 228.50 | USD | 11425.00 | 雪盈证券 | 5.00 | 看好AI进展 |
```

---

## 六、边界情况处理

| 情况 | 处理方式 |
|------|----------|
| 卖出数量超过当前持仓 | 停止执行，告知用户当前持仓数量，请用户确认 |
| symbol 不存在对应笔记 | 停止执行，询问是否创建新资产笔记 |
| 字段信息不完整 | 停止执行，列出缺少的字段，请用户补充 |
| 货币与笔记中 currency 不一致 | 提示用户确认，不自动转换汇率 |
| 用户要求更新当前价格 | 仅更新 `current_price` 和 `last_updated`，不追加交易记录 |

---

## 七、回复格式

执行完成后，回复格式如下（简洁）：

```
已完成：
- Transaction-Log：追加 1 行（Buy AAPL +50 @ 228.50 USD）
- AAPL.md：quantity 100 → 150，avg_cost 175.20 → 179.45
```

如有计算过程需要验证，附上 avg_cost 的计算步骤。
