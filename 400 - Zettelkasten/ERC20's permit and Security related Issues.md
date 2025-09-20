Date: 2025-09-20
Tags: [[crypto]] [[security]]

# ERC20's permit and Security related Issues

- [ ] learn how ERC20 permit works #active 

`permit` is an off-chain version of `approve`. You can generate a structual signature (EIP-712) off-chain which doesn't need gas and send it other service. That service will call the token's() `permit` function and pay the gas. 

# References
https://x.com/evilcos/status/1968631984739029206