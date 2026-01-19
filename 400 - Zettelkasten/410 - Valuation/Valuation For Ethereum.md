Date: 2025-10-16
Tags: [[macro]] [[valuation]] [[ethereum]]

# Valuation For Ethereum

## defi
链上低风险 Defi 可以被更多大资金作为 saving account, 核心还是得解决安全问题，比如为协议引入保险金库。这比高风险的挖矿协议更有长期价值。稳定币及 RWA 规模也被预期会快速增长。

## zk
以太坊L1/L2生态已经从“昂贵/慢”，逐步转向“可证明的扩展”，Succinct、Zksync以及Brevis对以太坊在不牺牲去中心化（甚至利于朝更去中心化方向发展）下，对以太坊生态的整体扩展做出了贡献。
这为以太坊生态，尤其是L2真正转向消费级应用做好了重要的准备，未来的隐私DeFi、AI代理经济、RWA等场景都会收益。

是把ZK/STARK证明能力下沉到真正个人可参与的程度，并且同步排序器去中心化和历史数据可验证性问题。谁先把“在家用树莓派就能为一个TPS 10,000+、费用<0.001美元的链贡献出块和证明”这件事跑通，谁就拿到了下一轮L1的“最深的护城河”。其他方向（比如更好的BFT算法、更快的最终性）都有价值，但都已经不是数量级差异了，真正的10x~100x差距，只可能出现在“去中心化的可验证性”这个维度。
## post-quantum
比特币作为价值存储，目前最大的隐患就是抗量子计算。因为以太坊迭代得比比特币快的多，它大概率会比比特币更早解决抗量子计算的问题，一定程度上以太坊的 money premium 属性可能会回归。

## scaling
2年10倍、4年100倍、六年 1000倍。（这还真不是放卫星），2年内主要依靠 Gas 提升加并行，还有延迟执行等优化，4年以上靠 ZK。
gasLimit 是以太坊上面每个区块中所有交易可以消耗的 gas 上限。假设目前每个区块的 gasLimit 是 30M，一笔普通的转账大约消耗 21000 gas，那么一个区块最多 1428 比转账，因为区块时间为 12s，那么TPS 约为 119。因此提高 gasLimit 是直观可以提升 TPS 的方法。但是这样会对节点产生更大的负担，一定程度上削弱节点的去中心化。

据 Vitalik 说，ZK-EVM 和 PeerDAS 将解决不可能三角。
2026年，先不靠ZK-EVM，将gas限额（处理能力）大幅提高，还能试跑ZK节点； 2026-28年，调费用、改数据结构，让高负载更安全； 2027-30年，ZK-EVM成主流，处理能力再翻倍。

## upgrade
### Fusaka
EIP-7594，L2 成本大量降低，通过 Blob 扩容 + PeerDAS。以后 L2 的 Blob 不用完全检查了，（基于密码学）抽样检查即可。这样共识层的节点可以再不提升配置的前提下，处理更多 L2 Blob，社区分析认为这个让 L2 再便宜 8x。

EIP-7935，默认把 gas 上限上调到 60M，直接提升了 TPS，目前一笔转账已经降至 $0.01，uni上交易一笔 $0.03。

EIP-7918，引入最小Blob基础费用，意味着即使Blob需求低迷，L2也得交最低的过路费，逐渐让 ETH 进入通缩。
简单来理解blob，以太坊主网L1是大脑中枢，直接处理交易比较贵。由此，诞生了L2这些外挂的“福手大脑们”，它们处理交易便宜很多。但是为了安全，这些副手们处理完之后，需要把数据（交易记录）提交到L1，这些数据存在blobs上。Blob gas费呢，就是L2给L1的“数据可用性费用”，之前Dencun升级时，这个费用在使用时没有最低价的机制，导致费用卡在1wei，几乎免费。结果是，网络在补贴blob，节点亏本干活

EIP-7951，可以不用记种子短语即可创建钱包，加了 passkey 支持（用 secp256r1 曲线），可以用手机或电脑的硬件签名。然这个无短语钱包也并非没有其缺点，需要依赖第三方设备的安全（设备的硬件安全模块），需要依赖第三方提供商内置的恢复机制等等。

PeerDAS 降低验证者门槛85%，更加去中心化。

从 ultrasound 上看，Fusaka 升级并没有增加 blob fee 的燃烧，因为新的升级后 blob 的供应也大幅增加，需求反而没跟上，每天只能燃烧零点几 ETH。 

## adoption
以太坊在 Q4 稳定币转账接近 6 万亿，已经碾压 Visa（约3.5万亿）和 Mastercard（越2.5万亿）的极度支付量。USDT 的供应从 Tron 回流到以太坊。这是真实采用而非投机，机构资金在实打实的加速进场。

一些可以观察的 adoption 指标：
- L2 adoption
- DeFi TVL
- Stablecoin Market Cap
- TPS
- Tokenisation and RWA
- DAT
- Active Users
- Crypto Payment

> 离岸美元至少在10万亿以上，如果未来有50%跑在链上，其中以太坊占比约60%（按目前大概比例），届时以太坊大约会有3万亿美元跑在链上，这3万亿美元不会静静呆在链上，会参与到各种金融活动中，交易/借贷/合约/预测市场/期权/链上股票/链上基金...

以太坊上的稳定币市值：
https://defillama.com/stablecoins/Ethereum?referrer=grok.com
目前大约 1650 亿，达到3万亿还有约 15 倍，似乎短期内是过于乐观的预测。

## valuation

vitalik：
> Ethereum is not the world. Ethereum is an opinionated take on properties that we think should be available in the world for those who want or need them.

持有以太坊可能永远也不会像持有谷歌的股票一样，因为一旦进入这个范畴，它几乎注定失败。以太坊的独特性，最终会让它更像其他商品，比如金银铜，而所有商品都具有周期。人永远无法预言世界的发展，也有某个黑天鹅事件，会让世界对它产生巨大的需求。持有这种独特性，就像是持有一张无限期的看涨期权。

vitalik 希望以太坊通过启用测试，即使供应商失去维护兴趣，使用者不受影响。需要支持：
1. 抗量子
2. 整体架构可以支持足够高的 TPS
3. 账户抽象
4. 更好的 gas 机制
5. pos


- [ ] 研究以太坊的估值模型

# References
## zk
https://x.com/VitalikButerin/status/1978432581298204951
https://x.com/lanhubiji/status/1978721883316207788
https://x.com/darkforesttri/status/1978722898551665028
https://x.com/lanhubiji/status/1992450426588057817
https://x.com/lanhubiji/status/1994999784256803075
## post-quantum
https://x.com/lanhubiji/status/1992823572885360746
## scaling
https://x.com/NPC_Leo/status/1993569168785121787
https://x.com/lanhubiji/status/2007718657695330577
## UX
https://x.com/nake13/status/1995319745030295717
## upgrade
### fusaka
https://x.com/nake13/status/1995319745030295717
https://x.com/tmel0211/status/1996775309082087800
https://x.com/0x_Allending/status/1996540540796670123
https://x.com/0xTodd/status/1996516205709148249
https://x.com/lanhubiji/status/1996577110413181107
https://x.com/lanhubiji/status/1996103075766173861
https://x.com/nake13/status/1996241760155312566
## insight & valuation
https://x.com/Snapcrackle/status/1992924911325905256
https://ethval.com/
https://x.com/VitalikButerin/status/2008194024012705947
https://x.com/VitalikButerin/status/2010621884811845708
## adoption
https://x.com/dankrad/status/1998289130967691697
https://x.com/ready_co/status/2001610562111742325
https://x.com/cmdefi/status/2008523414332731796

