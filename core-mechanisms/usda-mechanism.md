---
description: >-
  A Yield-Bearing stablecoin Backed by Over-Collateralization and Delta-Neutral
  Strategies
icon: coin-blank
---

# USDA Mechanism

The goal of USDA is to create a stablecoin that offers price stability, yield sharing, absolute transparency, and ultra-low risk. Its core mechanism is built around three pillars:

### Pillar 1: Tiered Over-Collateralization and Net Value Anchoring <a href="#pillar-1-tiered-over-collateralization-and-net-value-anchoring" id="pillar-1-tiered-over-collateralization-and-net-value-anchoring"></a>

**Over-Collateralized Minting**

To mint 1 USDA, users must deposit collateral assets worth more than $1. This creates a natural safety buffer.

**Tiered Collateral Management**

Collateral assets with different risk profiles correspond to different collateral ratios. Higher-risk assets require higher collateral ratios to control systemic risk.

**Net Value Anchoring and Redemption**

The ultimate value anchor of USDA stems from the net value of its underlying collateral. The protocol calculates the net collateral value per USDA in real time.

**Two-Way Conversion Channels**

* **Minting**: Deposit collateral → Mint USDA based on the collateral ratio.
* **Redemption**: Burn USDA → Retrieve corresponding collateral value based on net worth (after debt settlement). This is the ultimate safeguard against USDA depegging.

### Pillar 2: Delta-Neutral Hedging and Yield Engine <a href="#pillar-2-delta-neutral-hedging-and-yield-engine" id="pillar-2-delta-neutral-hedging-and-yield-engine"></a>

This is what sets USDA apart from traditional over-collateralized stablecoins (e.g., DAI) and centralized stablecoins (e.g., USDC).

**Delta-Neutral Strategy**

To prevent collateral price fluctuations from devaluing USDA, the protocol does not leave collateral "idle." Instead, it automatically deploys collateral (e.g., SOL) into delta-neutral strategies—for example, holding SOL while opening short positions in the perpetual futures market.The goal of this strategy is to hedge against the price risk (Delta risk) of the collateral itself. This stabilizes the USD value of the collateral, making it less vulnerable to sharp market swings.

**Yield Sources and Distribution**

Hedged collateral participates in [yield strategies](neutral-strategy.md) to generate stable, low-risk yields.**Yield Distribution**

* **Yield Sharing**: These yields do not belong to the protocol but are distributed to USDA holders. Holding USDA is like owning an interest-bearing USD savings account.
* **Enhanced Security**: Yields are continuously injected into the collateral pool, gradually increasing the collateral ratio. This means the collateral value behind each USDA grows over time, making the system increasingly secure.

### Pillar 3: Multi-Layered Market Adjustments and Windowless Minting/Redemption <a href="#pillar-3-multi-layered-market-adjustments-and-windowless-minting-redemption" id="pillar-3-multi-layered-market-adjustments-and-windowless-minting-redemption"></a>

**Three-Tiered Anchoring Maintenance Mechanisms**

1. **Arbitrage Anchoring (Market Behavior)**: If USDA trades below $1 on secondary markets (e.g., DEXs), arbitrageurs can buy discounted USDA and redeem it via the protocol for full net-value collateral, profiting from the spread and pushing the price back to $1. Conversely, if the price exceeds $1, arbitrageurs will mint new USDA to sell.
2. **Net Value Anchoring (Ultimate Guarantee)**: As noted, redeemability ensures a price floor.
3. **Windowless Minting and Redemption**: Users can mint or redeem USDA at any time (24/7). This eliminates time barriers to arbitrage, ensuring real-time anchoring effects and significantly curbing price deviations.

**Controlled Supply**

Initially, the number of USDA that can be minted will be limited. This is a prudent risk management measure to ensure hedging strategies operate stably at a controllable scale. The supply cap will gradually increase as strategies mature and gain market recognition, ensuring long-term system robustness.

### Summary: Core Advantages of USDA <a href="#summary-core-advantages-of-usda" id="summary-core-advantages-of-usda"></a>

| Feature                 | USDA                                                                                 | DAI                                                                        | USDC                                                        |
| ----------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------- | ----------------------------------------------------------- |
| **Anchoring Mechanism** | Net value redemption + market arbitrage                                              | Relies mainly on market arbitrage; low collateral utilization              | Centralized 1:1 USD redemption promises                     |
| **Capital Efficiency**  | High: Collateral generates continuous yields via hedging strategies                  | Low: Collateral is mostly idle, serving only as security                   | N/A                                                         |
| **Yield Ownership**     | Accrues to holders: Yields flow back to USDA itself via strategies                   | Accrues to the protocol: Yields are primarily captured via deposit spreads | Accrues to issuers: Interest on reserves belongs to issuers |
| **Transparency**        | Extremely high: All collateral, debts, and hedging positions are on-chain verifiable | Relatively high                                                            | Relies on periodic audits by centralized institutions       |
