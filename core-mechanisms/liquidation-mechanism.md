---
description: Trigger Logic, Execution Flow & Security Guarantees
icon: money-bill-transfer
---

# Liquidation Mechanism

### Overview

Aril's liquidation mechanism is designed to safeguard the protocol's asset security and market stability. When the value of a user's collateralized LP assets (which will expand to other interest-bearing assets as the platform upgrades) is insufficient to cover their loan obligations, an automated liquidation process is triggered to protect creditors' interests and the overall health of the protocol.

### Core Design Objectives

1. Risk Isolation: Promptly address insolvent accounts to prevent risk from spreading to the entire protocol.
2. Fairness and Transparency: Liquidation rules are publicly verifiable, and asset distribution ratios are preset and immutable.
3. Efficient Execution: Automate the trigger and execution processes to minimize manual intervention and mitigate latency risks.
4. Asset Security: Implement strict account permission verification and transaction confirmation mechanisms to ensure compliance in asset handling.

### Liquidation Trigger Mechanism (Trigger Phase)

The liquidation trigger marks the start of the entire process. It involves real-time monitoring of user account statuses to accurately identify high-risk accounts that meet liquidation criteria.

**Trigger Condition Verification**

* Core Indicator: Liquidation is triggered when the value of the user's LP collateral (priced by Chainlink oracles) falls below their USDC loan obligation.
* Precondition: The user must simultaneously have "outstanding debts" and "hold valid LP collateral" (verified via on-chain account data).

**Automated Scanning Process**

1. User LP Position Identification: Scan users' LP collateral records via Program Derived Address (PDA) to filter accounts with valid debts and collateral.
2. Loan Record Matching: Link the user's loan details (including principal, remaining amount, interest rate, etc.) to ensure the authenticity and validity of debt information.
3. Liquidation Record Initialization: Generate a unique Liquidation Record to immutably store key data at the time of trigger (debt amount, LP value, health factor, etc.).

### Liquidation Execution Mechanism (Execution Phase)

The execution phase focuses on liquidating the collateralized LP assets and distributing funds according to preset rules. The entire process is powered by smart contracts and decentralized trading protocols.

**1. Liquidity Withdrawal**

* Interact with the Raydium SDK and Concentrated Liquidity Market Maker (CLMM) protocol to fully withdraw the user's collateralized LP tokens into underlying assets (e.g., SOL and USDC).
* Strictly verify the validity of LP positions to ensure the withdrawal complies with decentralized exchange rules.

**2. Asset Liquidation**

* If the withdrawn assets include SOL, automatically convert it to USDC via the Raydium CLMM pool (with 1% slippage protection to mitigate market volatility impacts).
* Consolidate all USDC assets to form a distributable fund pool.

**3. Fund Distribution Rules**

Funds are distributed in the following priority order (preset ratios are immutable):

1. Debt Repayment (100% Priority): Repay the user's USDC debt to the protocol first, with funds transferred directly to the protocol's USDC treasury.
2. Admin Fee (10%): Allocate 10% of the remaining funds as a protocol maintenance fee to the designated admin account.
3. Liquidator Reward (3%): Allocate 3% of the remaining funds as an incentive for liquidators to encourage timely risk resolution.
4. User's Remaining Funds (87%): Return the final remaining funds to the liquidated user to protect their legitimate rights and interests.

### Security and Reliability Guarantees

1. **Multi-Dimensional Verification:**
   * Real-time verification of on-chain account data (LP collateral, loan records, token balances).
   * Immutable storage of key parameters in the Liquidation Record to prevent disputes caused by price fluctuations.
   * Mandatory confirmation of account permissions and status before transaction execution to avoid invalid operations.
2. **Transparent Processes:**
   * All liquidation operations are executed via on-chain transactions, with real-time traceability on browsers like Solscan.
   * Fund distribution ratios are preset in the code logic, with no manual intervention throughout the process to ensure fairness.
3. **Automated Monitoring:**
   * A built-in liquidation listener (scans once per second) to promptly detect pending liquidation tasks.
   * Wait for blockchain confirmation (Finalized status) after transaction execution to prevent off-chain data inconsistencies.
