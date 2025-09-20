Date: 2025-09-20
Tags: [[crypto]] [[security]]

# ERC20's permit and Security related Issues

- [ ] learn how ERC20 permit works #active 

`permit` is an off-chain version of `approve`. You can generate a structual signature (EIP-712) off-chain which doesn't need gas and send it other service. That service will call the token's (EIP-2612) `permit` function and pay the gas. And your allowance for someone will be updated.

EIP-712 aims to make the signed message  could be displayed in a readable way instead of raw hex string.
EIP-2612 is an extension to ERC20 which adds the `permit` function.

# References
https://x.com/evilcos/status/1968631984739029206
https://www.cyfrin.io/blog/understanding-ethereum-signature-standards-eip-191-eip-712