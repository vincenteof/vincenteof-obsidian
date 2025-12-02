Date: 2025-10-16
Tags: [[macro]] [[valuation]] [[ethereum]]

# Valuation For Etherum

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

## UX
Fusaka EIP-7951


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
## UX
https://x.com/nake13/status/1995319745030295717
## insight
https://x.com/Snapcrackle/status/1992924911325905256