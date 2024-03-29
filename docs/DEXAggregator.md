---
icon: arrow-switch
label: DEX Aggregator
---

The Conveyor aggregator is currently compatible with all DEXs that conform to the Uniswap v2/v3 standard, as well as their variants. This encompasses nearly every major DEX launched in the last few years, including Sushiswap, PancakeSwap, Camelot, Trader Joe, and several others. We plan to support several other DeFi protocols in the future including Curve, Balancer, Aave, etc.

## Why Use Conveyor's Aggregator?

Other DEX's and aggregators utilize a specific smart contract called a _Router_ that communicates between various liquidity pools for both single and multi LP interactions. While this does improve the likelyhood that a transaction will be successful, all of this processing is executed on-chain with multiple external contract calls and transfers in order to work.

With Conveyor, we construct all transaction calldata off-chain in a much more effective and cost-efficient manner, and pass the most favorable swap data back to the frontend for the trader to sign with their connected wallet.

This reduces unnecessary external calls or token transfers, which reduces the amount of on-chain processing needed to perform the swap, resulting in a much more gas efficient swap.

!!! Example: A trader wants to swap _X_ amount of _Token A_ for _Token C_
!!!

### <center>How other DEX's/Aggregators handle transactions</center>

```mermaid
graph LR
    A[User Wallet] --> |Send token A| B(DEX Router)
    B --> |Send token A| C{Token A/B Liquidity Pool}
    C --> |Receive token B| B
    B --> |Send token B| D{Token B/C Liquidity Pool}
    D --> |Receive token C| B
    B --> |Receive token C| A
```

### <center>How Conveyor handles transactions</center>

```mermaid
graph LR
    A[User Wallet] --> |Send token A| B{Liquidity Pool #1}
    B --> |Send token B| C{Liquidity Pool #2}
    C --> |Receive token C| A
```
