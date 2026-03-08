# AegisPay 🛡️

**The Settlement Ledger for Web3 Commerce**
_Bringing Visa-style "Auth & Capture" to Smart Contracts via Chainlink CRE._

[![Website](https://img.shields.io/badge/Live_Demo-aegispay.xyz-blue)](https://aegispay.xyz)
[![Video Pitch](https://img.shields.io/badge/Pitch-Watch_Video-red)](INSERT_YOUTUBE_LINK_HERE)

## ⚠️ Repositories 

AegisPay is a multi-layered decentralized payment protocol. We have two main repositories:
 - [aegispay-contracts](#1-the-singleton-ledger-smart-contracts)
- [aegis-cre](#2-the-ai-risk-engine-chainlink-cre)

And a frontend demo:
- [aegisweb](#3-the-interactive-demo-frontend)

Please explore the protocol through these links:

### 1. The Singleton Ledger (Smart Contracts)

🔗 **[Go to aegispay-contracts repo](https://github.com/AegisPayments/aegispay-contracts)**

- **What it is:** The on-chain settlement layer built with Foundry.
- Has a 3-tier balance system (`userFreeBalances`, `authorizedHolds`, `merchantSettledBalances`).
- **Security:** Core functions are strictly modifier-gated to the Chainlink CRE Forwarder. No one bypasses the AI guard.

### 2. The AI Risk Engine (Chainlink CRE)

🔗 **[Go to aegis-cre repo](https://github.com/AegisPayments/aegis-cre)**

- **What it is:** The off-chain intelligence and orchestration layer powered by Chainlink CRE and AI.
- **Innovation** - Visa style auth & capture. Evaluates dynamic pricing adjustments and User Authorizations (e.g., Uber route changes, EV charging variance) against historical user data in Firestore.
- **Security:** Provides real-time fraud detection and maintains an end to end off-chain audit trail via EVM Log Triggers.

### 3. The Interactive Demo (Frontend)

🔗 **[Go to aegisweb repo](https://github.com/AegisPayments/aegisweb)**

- **What it is:** A Next.js 16 application demonstrating the "Auth & Capture" flow.
- Features a split-screen "Simulation Mode" showing the clean Web2 mobile UX alongside the simulated Chainlink CRE terminal execution.

---

## The Problem AegisPay Solves

Web3 payments fail real-world commerce due to three limitations:

1.  **Infinite Approvals Risk:** Users risk wallet drains for a simple transaction.
2.  **Over-collateralization Burden:** Dynamic pricing (DePIN, AI Agents, Ride-sharing) requires locking excessive upfront capital.
3.  **Strict Approval UX Nightmare:** Standard ERC20 approvals revert if the final price changes by a single cent.

## The Aegis Solution

We translated TradFi's proven "Auth & Capture" architecture to Web3. Users deposit once into a secure ledger. This acts as an completely liquid Web3 checking account where funds can be withdrawn at any time. The merchant only gets access to the temporary `authorizedHolds`. 

Merchants request specific, time-limited authorizations. When prices dynamically change, merchants request a `secureIncrement`. This request routes through our **Chainlink CRE AI Risk Engine**, which evaluates the merchant's risk profile and the user's history before approving the on-chain increment.