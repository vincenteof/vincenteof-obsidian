Date: 2025-08-22
Tags: [[trade]]

# 关于 SBET 与 ETHA 的套利策略

核心思路时基于每股含 ETH 数，可以得出约 7SBET = 4ETHA，基于这个可以扩展出很多套利策略。

作者使用这样的策略：因为当前 mNav 已经在接近与 1 的低位，可以卖出 7 份 SBET 的 put 并买入 4 份 ETHA 的 put。因为 SBET 的波动率高于 ETHA，因此卖出获得权利金会多于买入消耗的权利金。如果 mNav 升高，可以收取权利金。如果mNav 继续下跌，就会亏损。

我更倾向使用现货策略，整体更简单但是杠杆比较低，大跌且 mNav 大于 1 的时候从 ETH 现货切换到 SBET，这样可以吃到价格和 mNav 的反弹。



# References
https://x.com/cs_wow/status/1957056955274678687