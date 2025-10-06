Date: 2025-08-29
Tags: [[defi]] [[trade]]

# Pendle Boros

YU is Boros is very like YT, If you long YU you are longing the funding rate, and vice versa.
YU only has a maturity date, the price of YU will become zero at maturity date.

What's different here is: 
1. when you long YU, you pay fixed but receive underlying
2. when you short YU, you pay underlying but received fixed
It means that whether we are longing or shorting, we all receive some interests and pay some interests.

For someone running delta netural funding rate strategy, since the funding rate may not be stable, he could add an YU short postion to lock the expected funding rate.

some strategy:
1. directly trading YU based on Implied APY
2. long spot and short perp, short YU to fix funding rate receivement (It's very like long spot and short future to eat basis)
3. long perp and long YU to hedge funding rate payment in very bullish market
4. triangular funding arbitrage between different exchanges



# References
https://x.com/ViNc2453/status/1953398036748812713
https://x.com/0xanonnnn/status/1960015380388409356
https://x.com/quant_sheep/status/1953490472116396395
https://x.com/JiamigouCn/status/1959184062721229043
https://x.com/quant_sheep/status/1953667222779703622
https://x.com/wili_eth/status/1955205439949599153
https://pendle.gitbook.io/boros/boros-docs
https://pendle.gitbook.io/boros
https://youtu.be/7qCLL1oMyCo
https://www.youtube.com/watch?v=Min3DxVpjzQ