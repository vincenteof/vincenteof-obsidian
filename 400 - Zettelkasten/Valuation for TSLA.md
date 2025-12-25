Date: 2025-10-08
Tags: [[macro]] [[valuation]]

# Valuation for TSLA

TSLA use synthesis to simulate edge cases, a world model for vison based fsd.

- [x] read the roadmap #active ✅ 2025-11-12

## Basic

The goal: **sustianable abundnace**
Basically they want to eliminate the scarity through technology revolution. The scarity could be energy, labor force, time. In order to make all things scalable, the cost must be low enough and the production efficiency must be high.
Optimus -> Infinite labor force supply with intelligence
FSD -> free time with more safety, Car becomes asset creating cash flow, the cost of transportation reuducing to near zero
Energy storage -> sun as the infinite energy supply


Elon is trying to put 100GW/year of AI in space. Basically they are gonna deploy GPUs into orbit.

基础设施第一次进入算法时代。自动驾驶，是人类历史上第一次尝试以软件的速度扩张现实世界的基础设施。软件的迭代速度是远远低于物理世界的，但是自动驾驶模型直接把“道路使用效率”变成可计算对象，速度的定义就从物理层切换到了算法层。终局就是利用 Optimus 把所有整个物理世界都变成可编程对象。这样城市拥堵、物流效率、交通事故率，长期被认为是“无法突破的物理约束”，这些限制会像早期移动互联网的带宽瓶颈一样——突然被突破。自动驾驶不是产品，而是城市层级的计算平台。 当算法能影响道路的运行节奏，它就从功能升级变成了基础设施升级。

- [ ] 2025 Q3 report
- [ ] watch the annual shareholder meeting
- [ ] read muskonomy2.0

- [x] watch the interview #active ✅ 2025-11-21

Hand is very complex and its the core of robot which intends to do a surgery or build a house. This kind of demand cannot be solved by money because these kind of resources(good surgeon) is limited.

The sentience will grow when new Grok is trainned. The question is how far it can go? Elon thinks almost incomprehensibly far. Elon sees a path putting 100 gw per year of solar powered AI satellite into orbit as a solution to scale AI.

Elon doesn't have problem taking risks.


## Energy

- [x] read the post about  megapack #active ✅ 2025-11-20

因为 AI 数据中心的能耗波动极大，有可能从 10％ 飙升到 100％。这种“尖峰+高频震荡”会严重冲击当地电网，可能导致电压骤降、频率失稳，甚至大面积停电。Megapack 可以充当缓冲期，只需要数据中心成本的 1％ 就可以完全平滑这种波动。


截止 2025 年 Q3，TSLA Energy 业务占应收 12％ 左右，整体毛利率比汽车业务高。这看这块业务，已经达到了 “大型独立能源／储能供应商”级别，不是简单边缘业务，而是具有明显盈利能力和增长潜力的核心业务。

## Space Data Center

马斯克似乎在认真思考把算力部署到太空。本质上是由于太空有无限的能源资源（太阳能）且效率更高，而且可以绕开国家电网及各种中心化监管。因为处于真空，理论上可以使用辐射散热到太空背景（2.7K），无需水冷。这会让 SpaceX + X + Tesla + Starlink 形成**完整的 AI 帝国闭环**。
但挑战同样巨大：散热成本，计算芯片在太空可能不能运作，维护成本等等。
https://chatgpt.com/g/g-p-67a5639b3cec8191b6084622f64bed7d-trade/c/691fa2a0-7b68-8320-a435-b41e50b228bf

“配备了本地化AI计算能力的卫星，只需将结果从低延迟、太阳同步轨道传回地面，将是三年内生成AI比特流的最低成本方式。 并且在四年内，这将是迄今为止最快的扩展方式，因为在地球上已经很难找到易于获取的电力来源。每年1兆吨的卫星，每颗卫星具有100kW功率，每年可增加100GW的AI计算能力，而且没有运营或维护成本，通过高带宽激光连接到Starlink星座。 超越这一水平的下一步是在月球上建造卫星工厂，并使用质量驱动器(电磁轨道炮)将AI卫星加速到月球逃逸速度，而无需使用火箭。这种方式每年可将 AI 计算能力扩展到100TW以上，并能为迈向卡尔达舍夫II型文明取得实质性进展。”

短期路径：太空同步轨道卫星，太阳能阵列供电，抗辐射 AI 芯片，通过激光链路传输到 Starlink 网络
长期远景：月球工厂，在月球建立工厂，利用原位资源利用（ISRU）制造卫星组件，通过电磁质量驱动器从月球低重力表面“发射”卫星，无需火箭燃料，实现指数级扩展
核心指标：1 megaton/year of satellites with 100kW per satellite yields 100GW of AI added per year with no operating or maintenance cost
2024年向太空输送了 `1.9*10^6` kg，其中大部分是 SpaceX，目标是 `1*10^9`kg，大约还要四年内增加 500倍。
这里隐含假设 1,000,000 颗卫星，1 吨/颗，可以提供 100kW。
这在今天属于**极端乐观**：
- 轨道太阳能板：在日地距离，太阳常数约 1360 W/m²，假设光电效率 30%，系统效率再打个折，实际到 DC 端大约几百 W/m²。#要凑出 **100 kW**，你大概要 **两三百 m²** 量级的太阳能板面积。
- 散热：在真空中只能靠辐射。按黑体辐射估算，要散掉 100 kW 热量，即便允许工作在 400K 左右，也需要 **几十平方米量级的散热板**，质量不低。
- 再加上结构件、姿态控制、推进剂、通信、GPU/TPU 模块、防辐射屏蔽等等，一颗卫星要压到 **1 吨以内还提供 100 kW 连续电力**，在 2030 年左右也还是非常拼命的指标。
https://chatgpt.com/share/69397d0c-0b4c-8008-a1da-961f42a4b18c

1吨/100 kW是“moonshot”指标，这不妨碍方案核心——太空计算避地球能源墙——只需上调数量/质量（e.g., 2吨/50 kW），总部署仍<10 megaton，经济性高（Starlink已证明LCOE<0.01美元/kWh）。Musk的xAI若投资专用芯片（辐射容忍+低热），可加速。
## FSD
- [x] read post the magic of telsa fsd ✅ 2025-11-26
从 FSD V12 版本开始，特斯拉完全抛弃 rule-based 方案，采用端到端 AI，用 8 个摄像头输入光子信号，输出控制信号。因为特斯拉自身也是骑车制造商，因此有巨大的数据优势，异常数据自动回传，模型永不停止迭代。V14 引入 Mixture of Experts (MoE) 架构，因为驾驶不是单一任务，需要根据环境切换专家模式。MoE 允许全球部署——用中国数据微调后，即可适配本地交通规则。整个 FSD 的架构，Optimus 也可以共享。
整个模型计算量巨大，Austin 的 Cortex 集群（10 万 GPU）并行处理，RL 耗时超模仿数倍。这种数据训练能力，也只有 AI 头部玩家才能做到。
V14 也引入了更多推理能力，直观感受就是 FSD 近似有意识，判用户需求、个性化服务，人类逐渐从驾驶中解放。

V14.2 已经展现了完全解决自动驾驶的能力，许多人都汇报长距离自动驾驶 0 接管。Elon 说 V14.3 是自动驾驶的最后一块拼图。
 
## Milestone

FSD:
1. size scale (2000 robotaxi)
2. when remove the security officer (by the end of 2025)
3. when will FSD allow driver to use the phone (by the end of 2025)

## Leadership

Elon的身价表示人们在押注世界将被颠覆。底层机制将被改写，不确定性大到可能导致裂变。这种时代纸面的财富如果不能捕获新的范式转移，那么只会一点点被洗牌走。巴菲特在上一轮抓住了 APPL。
Buffett的世界观假设世界稳定、激励趋同、时间会平滑波动；Musk的世界观假设世界剧变、激励分化、时间放大差异。资本已选择相信后一种更“真实”的视角，这解释了为什么Musk的财富相对暴增，而Buffett相对落后。当机构失去合法性（无法有效解决问题）但仍握有权力时，系统会寻找替代者——那些能承受混乱、外部化风险、先行一步的人。


# References
## roadmap
https://x.com/Tesla/status/1962591324022153607
https://x.com/Tesla/status/1977443755256111109
https://www.youtube.com/watch?v=VGPlvmMjPtE
https://youtu.be/GwfLkEOW37Q?si=XZZ9Oaut8nbGh7EG
## insight
https://rabbit-hole.notion.site/2650616711418094bb74e38b58052acf
https://x.com/jason1730/status/1982293830436311041
https://x.com/battleangelviv/status/1982309205441724906
https://x.com/jason1730/status/1982443011633295666
https://x.com/pirrer/status/1982379299039834433
https://x.com/TeslaLarry/status/1990060509979119670
https://x.com/Maggie191919/status/1994982499110224095
### energy
https://x.com/iamai_eth/status/1989457402203386066
https://x.com/Tesla_Megapack/status/1989073638273012133
https://x.com/tradergokux/status/1991341114452832757
https://x.com/BlueJay87476298/status/1991435063859487022
https://x.com/elonmusk/status/1997706687155720229
## fsd
https://x.com/pbeisel/status/1831315999037210900
https://grok.com/share/bGVnYWN5LWNvcHk_a4e5bb9a-0a35-4212-b32c-4f024e07d3de
https://x.com/Louistesla93/status/1992022320958107887
https://x.com/XieJackie/status/1991902747688579074
## leadership
https://x.com/RakukageMSC/status/2001274700690010341