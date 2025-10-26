---
title: Developer Resources
---
## Smart Contracts (planned)
- `TFTToken`: ERC‑20 compliant with extensions
- `StakingTiers`: tier proofs + cooldowns
- `RiskEngine`: exposure, violations, rewards
- `CopyRouter`: mirroring logic and caps
- `Governance`: proposals and execution
- `Treasury`: fee routing and buy‑back

> ABI & addresses will be published at launch.

## API / Indexer
- GraphQL/Subgraph endpoints for positions, PnL, seasons, NFTs.
- Webhooks for events (optional).

## Integration Example (pseudo)
```solidity
// Pseudo-interface
interface IRiskEngine {
  function openPosition(address trader, bytes calldata params) external returns (uint id);
}
```

## Tooling
- Hardhat/Foundry for testing
- Slither/Manticore for analysis
- OpenZeppelin libs
