# Ajna contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Resources

- [Twitter](https://mobile.twitter.com/ajnafi)
- [Website](https://www.ajna.finance/)
- [Business Logic recording](https://www.youtube.com/watch?v=LoknmCG-0kw)
- [Whitepaper](https://docsend.com/view/brw647iyuvwh9wj5)
- [Ajna Technical Spec](https://docsend.com/view/ai74yqgzjp3yydyt)
- [ELI5](https://docsend.com/view/dqf64s8gfi2p9aqh)
- [Technical Diagrams](https://docsend.com/view/api44fg49ts2y3ae)

# On-chain context

```
DEPLOYMENT: Ethereum mainnet, Arbitrum, Optimism, Binance Smart Chain, Polygon, Fantom, Tron, Avalanche
ERC20:  any - ERC20's are used in fungible, collection and subset pool types
ERC721: any - ERC721's are used in collection and subset pool types
ERC777: none
FEE-ON-TRANSFER: none
REBASING TOKENS: none
ADMIN: N/A
```

In case of restricted, by default Sherlock does not consider direct protocol rug pulls as a valid issue unless the protocol clearly describes in detail the conditions for these restrictions. 
For contracts, owners, admins clearly distinguish the ones controlled by protocol vs user controlled. This helps watsons distinguish the risk factor. 
Example: 
* `ContractA.sol` is owned by the protocol. 
* `admin` in `ContractB` is restricted to changing properties in `functionA` and should not be able to liquidate assets or affect user withdrawals in any way. 
* `admin` in `ContractC` is user admin and is restricted to only `functionB`

# Audit scope
* ./contracts/src files and any files they import
* ./ecosystem-coordination/src files and any files they import

# About Ajna
The Ajna protocol is a non-custodial, peer-to-peer, permissionless lending, borrowing and trading system that requires no governance or external price feeds to function. The protocol consists of pools: pairings of quote tokens provided by lenders and collateral tokens provided by borrowers. Ajna is capable of accepting fungible tokens as quote tokens and both fungible and non-fungible tokens as collateral tokens.

# Known attacks or issues
## Defined Upper and lower boundaries of deposit size
- When depositing large amounts at high prices (low indexes), balances can overflow a uint256 causing a revert. For buckets with quote token deposited, interest accumulation makes this problematic.

