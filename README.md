
RentLock: The Yield-Protected RWA Escrow Engine
===============================================

💡 The Vision
-------------

**RentLock** transforms the stagnant £10B rental deposit market into a high-utility, yield-generating RWA protocol. By leveraging **Uniswap v4's Hook infrastructure**, we move deposits from idle custodial accounts into active, gas-optimized liquidity, while providing institutional-grade security for both tenants and landlords.

This is a global solution with massive potential---the impact of such automated escrow and yield generation is particularly transformative for the high-margin rental markets emerging across Africa and Asia.

🚀 Key Innovations
------------------

-   **Dynamic LVR Capture (`beforeSwap`):** Algorithmically adjusts swap fees based on oracle price deviations. This captures 80% of toxic MEV and "Loss-Versus-Rebalancing" (LVR) value, converting it into passive yield for deposit holders.

-   **Reactive Automation (RSC):** Utilizes the **Reactive Network** to provide Inversion-of-Control. Our protocol monitors lease expiry events on-chain and autonomously degrades security gates to 1-of-2 if a landlord fails to raise a dispute within 14 days. No centralized cron-jobs or manual intervention required.

-   **De-Peg Safety Fuse:** Integrated circuit breaker that atomicaly pauses pool swaps if stablecoin assets drop below a 0.98 threshold, protecting underlying tenant collateral.

-   **Singleton Architecture:** Built on the Uniswap v4 Singleton, enabling atomic execution and massively reduced gas costs compared to traditional v3 factory deployments.

🛠️ Architecture Overview
-------------------------

### The Tech Stack

-   **Framework:** Foundry (for atomic testing and deployment)

-   **Core:** Uniswap v4 (Singleton pool management)

-   **Automation:** Reactive Smart Contracts (ReactVM)

-   **Oracles:** Chainlink (price feed triggers)

📂 Monorepo Structure
---------------------

```text
/packages/contracts
├── src/core/LeaseManager.sol       # Logic for lease status & deposit escrow
├── src/hooks/RentLockSentryHook.sol # Dynamic fee & LVR capture logic
├── src/hooks/RentLockHook.sol       # Base hook security & de-peg fuse
└── src/core/RentLockReactiveOrchestrator.sol # Reactive listener engine

```

🏗️ Quick Start
---------------

```bash
# Clone the repository
git clone https://github.com/benpaymaster/rentlock-protocol.git
cd rentlock-protocol

# Enter the contracts directory where Foundry is configured
cd packages/contracts

# Install dependencies
forge install

# Run the test suite
forge test

```

📜 License
----------

MIT