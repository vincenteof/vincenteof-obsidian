Date: 2025-09-01
Tags: [[crypto]] [[eip]]

# EIP7702 and its danger

Basically EIP7702 upgrades your EOA account to contract account. The concrete operation is to make your address signed to an contract, and your address will have the functionality that contract owns. 
The risk comes in 2 direction: 
1. If your account is signed to a malicious contract, you are definitely fucked
2. If your account is signed to a good contract, but someone malicious phishes using the contract, you are fucked too (like smart contract vulnerabilities)

The key to EIP7702 is `setcode` tx. After that tx, your account's code points to ann


# References
https://x.com/galenyuan/status/1926659099170648344
https://eips.ethereum.org/EIPS/eip-7702
https://www.quicknode.com/guides/ethereum-development/smart-contracts/eip-7702-smart-accounts
https://www.youtube.com/watch?v=_k5fKlKBWV4&pp=ygUHRUlQNzcwMg%3D%3D
https://www.youtube.com/watch?v=ZFN2bYt9gNE&list=WL&index=2
https://youtu.be/zIlDMeatZ94
https://x.com/erc4337/status/1909244749183160394
https://x.com/gakonst/status/1908905871528353949
https://goplussecurity.medium.com/understanding-eip-7702-phishing-attacks-a-comprehensive-guide-to-protection-strategies-for-wallets-8e8372e3d5ea
https://slowmist.medium.com/in-depth-discussion-on-eip-7702-and-best-practices-968b6f57c0d5
