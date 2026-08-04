Date: 2026-08-03
Tags: [[ai]] [[harness]]

# DeepSeek With Pi Agent

这个方案（oh-my-pi + DeepSeek V4 Flash）据说很快，而且可以高性价比解决大多数日常问题
https://x.com/geekbb/status/2068545154659860640

pi + deepseek 的具体配置方案
https://x.com/LinearUncle/status/2065295690671305059


pi 默认的 core 很小（no built-in plan mode, no sub-agents, no MCP, and no permission popups），很多功能需要安装 extension 实现。

安装完成后用 /login 注入 deepseek 的 key

因为 pi 的内核足够简介足够小，其他 agent 做的一些功能在模型升级迭代后反而成了累赘，而 pi 可以最大发挥模型本身的智能
https://x.com/justone_he/status/2084185953799946323
https://x.com/Eternalfate__/status/2084282759439417640



# Todos

- [ ] 完成 pi agent 和 deepseek 的搭建 #active 

# References
https://x.com/geekbb/status/2068545154659860640
https://x.com/LinearUncle/status/2065295690671305059
https://x.com/justone_he/status/2084185953799946323
https://x.com/Eternalfate__/status/2084282759439417640