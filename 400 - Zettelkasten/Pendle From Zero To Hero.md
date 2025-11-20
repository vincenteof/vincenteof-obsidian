Date: 2025-11-01
Tags: [[trade]] [[farming]]

# Pendle From Zero To Hero

- [x] 1. Why PT users exist make IY higher 2. Why PT moves oppsite way from  YT #active ✅ 2025-11-09
Sine `PT + YT = SY`， it means that the price of PT and YT moves in a oppsite way. Although YT moves to 0 and PT moves to SY when maturity is coming, it's still possible that YT goes high while PT goes down at some point based on trader's expectation.

Pendle has an AMM for PT and SY, and YT is derived. So PT and SY is the real liquidity. When some one is trading PT, the point move on the AMM curve. Buy PT means put SY and get PT. And sell PT means the oppsite direction.

Trading YT is indirect. Buy YT means first minting PT and YT using SY, then send PT to the pool getting more SY, and the PT reserve goes up and SY reserve goes dowm resulting PT price down and YT price up. When selling YT, the router mints PT first, combines with YT to reconstruct SY and buy back PT from AMM and rebalances. The pool will have more SY and less PT and PT price up.

- [ ] try to monitor IY and send alert
Since most of the time we just use the maker order to buy YT, so we tend to split a big order into small orders at different IY, so the real time IY is not that important.
Grok has given some advice.

- [x] what happens when yield become negative #active ✅ 2025-11-20

Pende 中有个 Watermark，表示 SY 资产能兑换的资产的最大值。一旦出现负收益，兑换率就回小于这个曾经最高的水位。因为 YT 始终会归零，因为之前拿出的利息是无法收回的，所以 PT 的持有者在兑换回底层资产的时候会减少。
一旦重新上升到水位以上，YT 重新开始收到利息，PT 又可以足额兑换回 SY。


# References
### projects
https://x.com/imqianyi88/status/1984488715776114893
https://x.com/imqianyi88/status/1984218704133923153
https://x.com/imqianyi88/status/1984843098141421957
## tools
https://pendle-yield-calculator.vercel.app/
## insight
https://x.com/an_le23998/status/1985948554452770972
https://x.com/LumaoDoggie/status/1974455195414499414