# 投资组合仪表板

## 组合汇总

```dataviewjs
const allFiles = app.vault.getMarkdownFiles();

const assets = allFiles
  .map(file => ({
    file,
    data: app.metadataCache.getFileCache(file)?.frontmatter ?? {},
  }))
  .filter(asset =>
    asset.data.type === "asset" ||
    asset.file.path.includes("972 - Assets")
  );

const money = (value) => Number(value || 0).toLocaleString("en-US", {
  minimumFractionDigits: 2,
  maximumFractionDigits: 2,
});

const percent = (value) => `${Number(value || 0).toFixed(2)}%`;
const field = (asset, name) => asset.data[name] ?? asset.data[name.replaceAll("_", "-")];
const num = (asset, name) => Number(field(asset, name) ?? 0);

const costBasis = assets
  .map(asset => num(asset, "quantity") * num(asset, "avg_cost"))
  .reduce((sum, value) => sum + value, 0);

const currentValue = assets
  .map(asset => num(asset, "quantity") * num(asset, "current_price"))
  .reduce((sum, value) => sum + value, 0);

const unrealizedGain = currentValue - costBasis;
const portfolioReturn = costBasis !== 0 ? (unrealizedGain / costBasis) * 100 : 0;

if (assets.length === 0) {
  dv.paragraph("No asset notes found under 970 - Investments/972 - Assets.");
  dv.table(
    ["Dataview can see these files"],
    allFiles.slice(0, 30).map(file => [file.path])
  );
}

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
const allFiles = app.vault.getMarkdownFiles();

const assets = allFiles
  .map(file => ({
    file,
    data: app.metadataCache.getFileCache(file)?.frontmatter ?? {},
  }))
  .filter(asset =>
    asset.data.type === "asset" ||
    asset.file.path.includes("972 - Assets")
  );

const snapshots = allFiles
  .map(file => ({
    file,
    data: app.metadataCache.getFileCache(file)?.frontmatter ?? {},
  }))
  .filter(snapshot =>
    snapshot.data.period_role === "ytd_start" ||
    snapshot.file.path.includes("974 - Snapshots")
  )
  .sort((a, b) => String(b.data.date).localeCompare(String(a.data.date)));

const start = snapshots[0];

const money = (value) => Number(value || 0).toLocaleString("en-US", {
  minimumFractionDigits: 2,
  maximumFractionDigits: 2,
});

const percent = (value) => `${Number(value || 0).toFixed(2)}%`;
const field = (asset, name) => asset.data[name] ?? asset.data[name.replaceAll("_", "-")];
const num = (asset, name) => Number(field(asset, name) ?? 0);

const currentValue = assets
  .map(asset => num(asset, "quantity") * num(asset, "current_price"))
  .reduce((sum, value) => sum + value, 0);

if (assets.length === 0) {
  dv.paragraph("No asset notes found under 970 - Investments/972 - Assets.");
  dv.table(
    ["Dataview can see these files"],
    allFiles.slice(0, 30).map(file => [file.path])
  );
}

if (!start) {
  dv.paragraph("No YTD start snapshot found.");
} else {
  const startDate = String(start.data.date);
  const startValue = Number(start.data.current_value || 0);
  const netContributions = Number(start.data.net_contributions_since_start || 0);
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

- [ ] 完成整体投资组合跟踪方案 #active
