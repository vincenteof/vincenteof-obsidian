Date: 2025-10-19
Tags: [[perpetual]] [[trade]]

# Perp series

- [ ] read the perp overview

- [x] read the oracles #active ✅ 2025-10-21
Binance use market price for USDe but with a relatively high LTV. Since itself is the primary market, cascading liquidation happens after someone control the spot market of USDe on it.
This kind of attack has a common pattern:
1. It's a leveraged system
2. Oracle price depend primarily on manipulatable spot market
3. Liquidation triggers are deterministic
4. Infra has capacity limits
5. Cost of manipulation < Extractable value through cascades
On 10/11, $60M spot dump happened on USDe while $19.B destroyed.
There are mainly 2 categories for non usd collateral. If we want high LTV, we can fix its price to 1 USD (for USDC, USDT). Or we can view it as risk asset and use the market price but with a low LTV. For USDe in Binance, it uses market price with a high LTV.
But using fixed rate has its own problem. UST was used to be te treated like that, and the result is the platform beared all the bad debts.
I think the only ways works is to use hybrid oracle design, combining multiple price sources with sanity checks that actually work:
- CEX prices (with volume weighting across venues)
- DEX prices (from high-liquidity pool only)
- On-chain proof of reserves
- Cross-exchange

# References
https://x.com/yq_acc/status/1978800996689293674
https://x.com/mindaoyang/status/1976882462002405383