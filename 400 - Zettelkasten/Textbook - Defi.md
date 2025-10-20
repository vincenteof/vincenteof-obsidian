Date: 2025-09-13
Tags: [[crypto]]

# Defi Book

I generate a defi book using chatgpt, and I store it on notion. I will read it and do some labs on it.

- [x] Defi Book Chapter2 #active ✅ 2025-09-16
Exercises:
2. Since blockchain is a distributed network, nodes should agree on the network state. 
3. In POW, a new node is created by minners, they compete with the minning puzzle to get the right to crate a new block. While in POS, the node creating the new block is random picked from stakers.
4. The one who created a new block will get reward, which is newly minted token. So they must back up with some scarity. In POW, the sacrity is hashing power, or energy. While in POS, the scarity is the staked token.
5. For POW, the attacker must hold over 51% hashing power. While the attacker must hold over 2/3 token in a POS system.
6. One angle is environment friendness. POW will waste a lot of energy because of the minning puzzle while POS is not. And POS is more friendly for long-term security budget. Minners will get less and less reward because of the halving, and so minner may shut down at some point when they are not profitable. But for POS, as long as the price of the token is still healthy, the amount of the stakers will remaining almost the same. But this also brings some good, because in POS, there is no limit for the total supply.
7. Sketch the contents of a simple block
8. The parent hash is the pointer for the chain. If someone alters a transaction in prev block, the block hash changes. And there will be mismatch for that block's hash and parent hash storing in the current block. 
9. Alice must hold at less 12 tokens, and the order doesn't matter.
10. Maybe based on the oder?
11. Minning puzzle is trying to find a nonce making the hash meet some requirements.
12. Kind of lab.
13. Kind of lab.
14. Because the hash result is not predictable.
15. Since directly altering the chain will be caught by the algorithm, the only way is to fork the chain at some point and make it the main. But finishing the minning puzzle is so difficult that you cannot save time, forking and becoming main is almost impossible. 
16. For racing to do some task, since other RPC is not controllable and maybe down when transactions are crowded. Ethereum tps is about 20 currently.
Labs:
I used to implement some toy pow blockchain, these labs are very similar to it.


- [x] Defi Book Chapter3 #active ✅ 2025-09-21
Ways to prevent Front-Running:
1. use commit-reveal pattern if your contract involves actions could be exploited when seen
2. send transactions to minners via private relays instead of mempool, e.g. Flashbots

The will be gas auction when multiple bots compete to exploit something by spamming higher and higher gas prices. The whole class of things is called MEV.

Exercises:
1. The private key is used to generate and the public key is used to verify. When someone forge your digital signature without your private key, when being verified with the public, it will fail.
2. Because it sends rewards before mutating the state, which introduces reentrancy attack. We can fix it using checks-effects-iteractions pattern.

- [ ] Defi Book Chapter4 #active 
Exercises:
1. **collateral risk** DAI is over-collateralization, so there is a buffer for collateral value crashes. But if the vault becomes undercollateralized, liquidations happen. For usde, since it's fully hedged, it won't be affected too much. **peg mechanism risk** for DAI, if its value is under 1, PSM will start and  arbitrageur will buy it to swap to USDC. For USDE, people can redeem USDE to get the value backed by it. **operational risk** They both has the risk of being hacked. And USDE has extra risk since it relies on centeralized exhcange or custodian. Both for DAI and USDE, this kind of risk is fatal. Someone has to undertake the loss. **regulatory risk** DAI relies on USDC, so if USC blacklists its address, it will have trouble. USDE has KYC gating. And it yield-bearing version could be considered a security.
   https://chatgpt.com/share/68f17f2b-1fd4-8008-8bf9-c32d54d20457
2. a. 150% b. 120% c. 12500 (according to 125% liquidation ratio) 
3. Since heged, total value doesn't change
4. If the stable coin has the real assets backed and has redeem, we can always arbitrage from depeg.




# References
