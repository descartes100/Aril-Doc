---
description: Stable Earn, Low Directional Risk
icon: chart-mixed-up-circle-dollar
---

# Neutral Strategy

Aril’s neutral vaults keep collateral productive while you borrow or trade—harvesting **basis, funding, and fee premia with delta-neutral** construction and tight risk limits. Results below are live track to 2025-09-30.

Why users choose Earn with Aril

* **Shallow drawdowns** and **low volatility** across sleeves
* **Short termination windows** (most <7 days; LP DN <3 days)
* **ZK transparency**: proofs of control, flow, neutrality, and return, anchored on-chain.&#x20;

### How It Works

1. **Source premia**: cross-venue basis, perp funding, LP fees/premia.
2. **Neutralize risk**: programmatic hedges; strict slippage & inventory limits.
3. **Route yield** to your cross-margin account—so **yield stays on** while you mint USDA or trade perps.

### Strategy Sleeves & Live Track

#### Cross-Exchange Arbitrage — Hyperliquid ↔ Binance / OKX

* Profile: Cross-venue dislocations with strict routing.
* Key stability: **Vol \~5.61% / 2.35%, Max DD \~1.74% / 0.37%, Sharpe \~9.30 / 7.61 (HYPE-BN / HYPE-OKX).**
* Returns: **66.28% (2024 (HYPE airdrop)); 7.91% (2025 YTD) (HYPE-BN). 5.00% (2025 YTD) (HYPE-OKX).**
* Why it fits Earn: High Sharpe, intraday monitoring, shallow historical DD.

#### Funding Rate Strategy — Hyperliquid & Bitget

* Profile: Market-neutral carry from funding with capped leverage.
* Stability: **Vol \~3.35% / 4.00%, Max DD \~1.13% / 2.45%, Sharpe \~5.61 / 4.75.**
* Returns (2025 YTD): **12.23% (HL), 10.98% (Bitget).**

#### Single-Exchange Arbitrage — Binance (BTC / ETH)

* Profile: In-venue basis/triangular edges; latency-aware fills.
* Stability: **Vol \~3.33% / 1.89%, Max DD \~0.47% / 0.74%, Sharpe \~6.19 / 4.97.**
* Returns (2025 YTD): **BTC 10.78%, ETH 4.74%.**
* Leverage guideline: 5×–10× (tight caps, single-venue controls).

#### LP Delta-Neutral — Jupiter DEX ↔ Binance (USDT)

* Profile: Provide DEX LP, hedge on CEX; monetize fees/premia.
* Stability: **Vol \~8.73%, Max DD \~3.21%, Sharpe \~2.55**.
* Returns: **9.21% (2024); 12.38% (2025 YTD)**.
* Ops: <3-day termination; dynamic premium management.

#### Mixed Arbitrage — KiloEx / Aster / Backpack ↔ Binance

* Profile: Basket of neutral opportunities + airdrops.
* Stability: **Vol \~5.69%, Max DD \~3.12%, Sharpe \~2.51.**
* Returns: **5.94% (2024); 7.60% (2025 YTD).**

**Sunset (for record)**: GMX v2 LP DN exited 2025-04-30 after parameter/liquidity changes; capital rotated to higher-Sharpe sleeves.

### Risk Controls&#x20;

* Neutral by construction: delta ≈ 0; returns come from funding/basis/fees.
* Venue diversification: DEX + CEX routes (Hyperliquid, Jupiter, KiloEx, Aster, Backpack; Binance/OKX/Bitget).
* Execution discipline: capped leverage, strict per-order slippage, inventory-aware unwinds.
* Operational cadence: up to hourly checks in stress; fast de-risk paths.
* [ZK proofs](../technology/zk-proof-module.md): control, flow, neutrality, and return rates—verifiable without revealing positions.&#x20;
* Performance 20%–30%

**Note**: “Neutral” ≠ “risk-free.” Past performance is not indicative of future results.
