---
icon: money-bill-transfer
---

# Liquidation Mechanism

### **1. Overview​​**

The Aril liquidation system is a critical, automated smart contract module designed to maintain the solvency of the protocol. It is activated when the value of a user's collateral—initially LP positions, with planned expansion to other yield-bearing assets—falls below the required threshold to cover their outstanding loan obligations. This mechanism ensures the protection of the lending pool's assets and overall protocol health by systematically closing undercollateralized positions.

### **​​2. Core Design Principles​​**

The system is architected around four key objectives:

1. ​**​Risk Containment:​**​ Isolate and neutralize insolvent positions in real-time to prevent systemic risk contagion.
2. ​**​Deterministic Execution:​**​ Ensure liquidation logic is transparent, verifiable, and operates with predefined, immutable parameters.
3. ​**​Maximized Efficiency:​**​ Automate the entire lifecycle from trigger to settlement, minimizing latency and maximizing capital efficiency.
4. ​**​Secure Asset Handling:​**​ Enforce strict permission checks and on-chain verification at every step to guarantee the integrity of asset movement.

### **​​3. System Architecture & Data Flow​​**

The liquidation process is a two-phase mechanism: a continuous monitoring phase that identifies at-risk positions, and an execution phase that settles them. The following sequence diagram illustrates the core workflow and system interactions:

<div data-with-frame="true"><figure><img src="../.gitbook/assets/Untitled 33.png" alt=""><figcaption><p>Aril Liquidation Process</p></figcaption></figure></div>

### **4. Liquidation Trigger Mechanism​​**

The trigger is a condition monitored on-chain that initiates the liquidation process.​**​**

**4.1. Trigger Condition​**​

The primary condition is the deterioration of a position's Health Factor (HF). Liquidation is triggered when:

```markup
HF = (Total Collateral Value in USDC) / (Total Borrowed Value in USDC) < Liquidation Threshold (e.g., 1.1)
```

* ​**​Collateral Valuation:​**​ The value of LP tokens is calculated in real-time using price feeds from decentralized oracles (e.g., Chainlink), combined with the LP's ratios from the underlying AMM.
* ​**​Debt Valuation:​**​ The total debt includes the principal plus any accrued interest up to the current block. ( With the launch of the USDA module, loans will carry a 0% interest rate. Consequently, the principal debt amount will equal the value of the collateral provided. )

​**​4.2. State Verification & Record Initialization​**​

Before execution, the system verifies the on-chain state:

* ​**​Account Validation:​**​ Confirms the existence of an outstanding debt and valid, non-zero collateral in the user's account via the protocol's `Program Derived Address (PDA)`.
* ​**​Liquidation Record:​**​ A unique, immutable on-chain struct is initialized, logging critical pre-liquidation snapshots (e.g., debt amount, collateral value, block timestamp, HF) to prevent disputes arising from price volatility during execution.

### **​​5. Liquidation Execution Mechanism​​**

The execution phase is an atomic series of operations handled by the liquidation smart contract.​**​**

**5.1. Collateral Unwinding & Settlement​**​

1. ​**​LP Position Withdrawal:​**​ The contract interacts with the integrated AMM protocol (e.g., Raydium CLMM) to withdraw the user's LP tokens, converting them into the underlying asset pair (e.g., SOL/USDC).
2. ​**​Asset Swap (if necessary):​**​ If the withdrawn assets include volatile tokens (e.g., SOL), they are immediately swapped for USDC via the on-chain DEX pool. A maximum slippage parameter (e.g., 1%) is enforced to mitigate market volatility impact.
3. ​**​Fund Consolidation:​**​ All assets are consolidated into a single USDC amount within the liquidation contract.

​**​5.2. Fund Distribution Algorithm​**​

The consolidated USDC is distributed according to a fixed, pre-programmed priority order:

1. ​**​Debt Repayment (First-Lien):​**​ 100% of the user's outstanding debt (principal + interest) is repaid to the protocol's USDC pool.
2. ​**​Protocol Fee:​**​ 10% of the ​**​remaining USDC balance​**​ is allocated to the protocol treasury as a maintenance fee.
3. ​**​Liquidator Incentive:​**​ 3% of the ​**​remaining USDC balance​**​ is sent to the address that triggers the liquidation function as a reward.
4. ​**​User Residual:​**​ The final 87% of the remaining funds are returned to the user's wallet, protecting their equity above the liquidation threshold.

**​​6. Security & Reliability Guarantees​​**

* ​**​On-Chain Verifiability:​**​ Every transaction, from trigger to distribution, is recorded on the blockchain, enabling full auditability via explorers like Solscan.
* ​**​Pre-Execution State Checks:​**​ The contract verifies account permissions and the validity of the liquidation state immediately before execution to prevent invalid transactions.
* ​**​Automated Monitoring:​**​ A dedicated off-chain "liquidation keeper" bot scans the blockchain state to identify and submit eligible positions for liquidation, ensuring prompt risk mitigation.
* ​**​Transaction Finality:​**​ The system awaits blockchain confirmation before considering a liquidation complete, preventing inconsistencies from chain reorganizations.
