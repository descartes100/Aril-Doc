---
icon: hand-wave
---

# Welcome

Aril is a next-generation DeFi lending protocol dedicated to redefining the on-chain lending experience through innovative mechanisms. We support a variety of interest-bearing assets as collateral—including Liquidity Providing (LP) Tokens, Liquid Staking Tokens (LSTs), and Real-World Assets (RWAs)—and on this basis, offer the world’s first zero-interest-rate stablecoin loan. The stablecoin in question is [USDA](core-mechanisms/usda-mechanism.md), natively issued by the Aril platform; users can mint for free upon collateralizing their assets, with no interest or additional fees incurred.

The core of Aril’s zero-interest-rate model lies in the fact that users’ collateralized assets are not left idle in a pool. Instead, they are automatically directed to [a strategy-optimized yield vault (neutral strategy vault)](core-mechanisms/neutral-strategy.md), which consistently generates stable returns. This portion of returns is sufficient to cover lending costs, thereby enabling efficient capital utilization. Meanwhile, as the collateral itself has the inherent property of generating continuous interest, it also provides an additional safety buffer for loan positions, significantly reducing the risk of users being liquidated.

Currently, in the [Minimum Viable Product (Devnet)](https://aril.so/) version during the hackathon phase, we have implemented core functions: supporting SOL-USDC LP as collateral and providing interest-bearing lending services based on USDC. This forms the foundational infrastructure of the Aril protocol. In the subsequent roadmap, we will successively launch the USDA stablecoin and its function as collateral, gradually building a more complete and robust [DeFi ecosystem](basics/roadmap.md).
