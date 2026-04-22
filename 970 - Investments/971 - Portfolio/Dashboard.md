# 投资组合仪表板

## 组合汇总

```dataviewjs
const assets = dv.pages('"970 - Investments/972 - Assets"')
  .where(p => p.type === "asset");

const money = (value) => Number(value || 0).toLocaleString("en-US", {
  minimumFractionDigits: 2,
  maximumFractionDigits: 2,
});

const percent = (value) => `${Number(value || 0).toFixed(2)}%`;

const costBasis = assets
  .map(p => Number(p.quantity || 0) * Number(p.avg_cost || 0))
  .array()
  .reduce((sum, value) => sum + value, 0);

const currentValue = assets
  .map(p => Number(p.quantity || 0) * Number(p.current_price || 0))
  .array()
  .reduce((sum, value) => sum + value, 0);

const unrealizedGain = currentValue - costBasis;
const portfolioReturn = costBasis !== 0 ? (unrealizedGain / costBasis) * 100 : 0;

dv.table(
  ["指标", "数值"],
  [
    ["Cost Basis", `${money(costBasis)} USD`],
    ["Current Value", `${money(currentValue)} USD`],
    ["Unrealized Gain", `${money(unrealizedGain)} USD`],
    ["Portfolio Return", percent(portfolioReturn)],
  ]
);
```

## Period Performance

```dataviewjs
const assets = dv.pages('"970 - Investments/972 - Assets"')
  .where(p => p.type === "asset");

const snapshots = dv.pages('"970 - Investments/974 - Snapshots"')
  .where(p => p.type === "portfolio_snapshot" && p.period_role === "ytd_start")
  .sort(p => p.date, "desc");

const start = snapshots.first();

const money = (value) => Number(value || 0).toLocaleString("en-US", {
  minimumFractionDigits: 2,
  maximumFractionDigits: 2,
});

const percent = (value) => `${Number(value || 0).toFixed(2)}%`;

const currentValue = assets
  .map(p => Number(p.quantity || 0) * Number(p.current_price || 0))
  .array()
  .reduce((sum, value) => sum + value, 0);

if (!start) {
  dv.paragraph("No YTD start snapshot found.");
} else {
  const startDate = start.date?.toFormat ? start.date.toFormat("yyyy-MM-dd") : String(start.date);
  const startValue = Number(start.current_value || 0);
  const netContributions = Number(start.net_contributions_since_start || 0);
  const periodPl = currentValue - startValue - netContributions;
  const periodReturn = startValue !== 0 ? (periodPl / startValue) * 100 : 0;

  dv.table(
    ["指标", "数值"],
    [
      ["Start Date", startDate],
      ["Start Value", `${money(startValue)} USD`],
      ["Current Value", `${money(currentValue)} USD`],
      ["Net Contributions", `${money(netContributions)} USD`],
      ["Period P/L", `${money(periodPl)} USD`],
      ["Period Return", percent(periodReturn)],
    ]
  );
}
```

> 2026 年从 2026-04-22 快照起算；之后年份使用上一年年末快照作为 YTD 起点。

## 总览表格（实时计算）
![[Portfolio.base#Portfolio Overview]]

---

**提示**：
- 改完后，**关闭 Dashboard.md 再重新打开**，或点击 Bases 表格右上角的刷新按钮。

- [ ] 完成整体投资组合跟踪方案 #active
