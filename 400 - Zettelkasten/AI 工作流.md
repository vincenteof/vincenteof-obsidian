Date: 2026-02-25
Tags: [[ai]]

# AI 工作流

## prerequisite
- [x] setup an claude account #active ✅ 2026-03-05
- [x] setup openclaw #active ✅ 2026-03-09

## insight

好的实践
1. 长期维护个人taste的上下文，并且按照职责分类。因为大模型的上下文窗口是有限的，把一切都塞进去不仅浪费注意力而且损害性能。

OpenClaw 做了什么
1. 自托管，因此可以完成一些更复杂的 agent 工作，如打开 Mac 上的浏览器
2. 自主执行复杂任务（通过定时触发）
3. 长期记忆系统
它的核心价值在于用 AI 解决非标准化的需求

关于多 agents 系统，一种实际的用途是解决自己生活中流程化的部分，最重要的是你自己要对怎么做有一套看法和审美，多 agents 只是杠杆或者加速器。
https://x.com/jimprosser/status/2029699731539255640
我觉得使用 Agent 一个最真实的需求是用 AI 搭建一个自动化的自己，比如 [这篇文章](https://x.com/xingpt/status/2025219080421277813)。

[这篇文章](https://x.com/AYi_AInotes/status/2026224275192193465)介绍了一种 Code Agent Swarm，[但是目前我不太理解为什么需要一个 7✖️24 不断运行的 Code Agent Team](https://x.com/vincenteof/status/2029163178341646847)。

使用 Code Agent 的时候将需求（spec）和实现（分离）也许会更好，可以参考 [这类经验](https://x.com/defi88888888/status/2036262502464626713)

- [ ] read [Claude Code overview](https://code.claude.com/docs) and [How I Use Claude Code](https://boristane.com/blog/how-i-use-claude-code/)

## experience

### openclaw
新版本的 openclaw 默认给 tool 的权限只有 message，需要更改配置：
openclaw config set tools.profile full
https://x.com/akokoi1/status/2030086511660789965

[提升 openclaw 的效率 10 倍](https://x.com/Louis_Chenxf/status/2028271391376888120)
一些 insight：
- 合理利用记忆系统，MEMORY.md 只保留 P0 级别的硬约束，日常事务全部写进 daily notes，需要回忆时用 `memory_search` 检索，不是全文加载
- 重执行任务交给子代理隔离，主绘画只做决策和审核
- openclaw 可以自主化管理记忆，甚至用 git 做版本控制，claude 这点做不到
配置要点：
1. MEMORY.md 精简原则：只保留 P0 级别的硬约束，其他全部移到 daily notes
2. Compaction 配置：`memoryFlush` + `contextPruning(cache-ttl=15m, keepLastAssistants=3)`
3. Heartbeat 策略：默认空文件，只在需要时写入任务
4. 子代理隔离：重执行任务用短命子代理（`cleanup: delete`）
5. Prompt Cache：稳定指令区前置，波动输入区后置
6. 安全审计：安装 skill 前跑 `scripts/skill-audit.sh`
7. 成本监控：每周检查 token 消耗，识别异常高的任务

- [ ] 尝试用 openclaw 操作 obsidian #active 
obsidian 的 vault 与 openclaw 的 workspace 如何存放
有了 obsidian 如何产生记忆，是否会上下文太大


- [ ] 尝试用 openclaw 如何建立多 agents 系统 #active 
[guoyu 针对开发者的多 agents 系统](https://x.com/turingou/status/2030180402766434780)
[tualatrix 的 agent 编排系统](https://x.com/tualatrix/status/2038506764854075699)



### harness engineering
[openai blog 上 关于harness engineering 的文章](https://x.com/fredchuuu/status/2038476548874145995)
[一个关于 harness engineering 实践的仓库](https://x.com/0xdeusyu/status/2036120884940058893)
- [ ] 在 vincenteofcom 中实践 harness engineering #active 



## usage
一人软件开发的 Agent 化

审计职能合约

### UI 设计
[宝藏小众设计 Prompts 网站](https://www.designprompts.dev/)
https://variant.com/

- [ ] 尝试使用 [impeccable](https://impeccable.style/) 或其他 [Design Skills](https://x.com/Jackywine/status/2033791236960846249) 来优化 vincenteofcom #active 



# References
## insight
https://x.com/koylanai/status/2025286163641118915
https://x.com/brucexu_eth/status/2028226211118481430
https://x.com/taresky/status/2028506302071325059
## memory
https://x.com/runes_leo/status/2027030391643570258

https://x.com/fredchuuu/status/2038476548874145995
## usage
https://x.com/Jackywine/status/2033791236960846249
https://variant.com/