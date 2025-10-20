Date: 2025-10-19
Tags: [[perpetual]] [[trade]]

# Perp series

- [ ] read the perp overview

- [ ] read the oracles #active 
Binance use market price for USDe but with a relatively high LTV. Since itself is the primary market, cascading liquidation happens after someone control the spot market of USDe on it.
This kind of attack has a common pattern:
1. It's a leveraged system
2. Oracle price depend primarily on manipulatable spot market
3. Liquidation triggers are deterministic
4. Infra has capacity limits
5. Cost of manipulation < Extractable value through cascades
On 10/11, USDe happens $60M spot 

# References
https://x.com/yq_acc/status/1978800996689293674
https://x.com/mindaoyang/status/1976882462002405383