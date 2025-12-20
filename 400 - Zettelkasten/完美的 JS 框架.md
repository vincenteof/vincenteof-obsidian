Date: 2025-12-10
Tags: [[full-stack]]

# 完美的 JS 框架

NextJS 太过依赖 Vercel，而且可能会有很多的潜在漏洞。我希望找到一个心智负担较小的全栈方案，并且便于部署到 Coludflare 或者 AWS。

- [ ] tanstack start + orpc
- [ ] react stack pattern

关于 TS 的 node 后端（2025）
1. tsc/esbuild/swc 转译到 JS + 外部 node_modules + docker
2. 直接 bun + docker
 bundling 只适合对冷启动速度要求很高时，但可能会遇到很多如路径等潜在问题。
 Node.js 23+ 原生支持直接跑 .ts，但仍有局限，托管平台也常不支持实验 flag。所以还是老老实实 build 到 JS。


# References
https://x.com/Manjusaka_Lee/status/1998030917961666632
https://x.com/meathill1/status/1992806954545406432
https://www.patterns.dev/react/react-2026/
https://x.com/changwei1006/status/2000919020762226918