---
title: Architecture
---
## System Overview
Averix comprises modular smart contracts and an off‑chain execution interface. Core layers:
- **Smart Contracts:** TFT token, staking tiers, risk engine, copy pools, governance.
- **Oracle Layer:** Price feeds (redundant providers with medianization + sanity checks).
- **Trading Interface:** Frontend/UI with TradingView for charting and local risk previews.
- **Indexers & Analytics:** Subgraph/GraphQL endpoints for historical and real‑time metrics.
- **Storage:** On‑chain state + off‑chain logs (IPFS/Arweave for docs and proofs).

## Component Diagram
```mermaid
flowchart LR
  U[Trader UI] -- tx --> SC[Smart Contracts]
  U -- read --> IDX[(Indexers / Subgraph)]
  ORA[Oracle Aggregator] --> SC
  SC <--> GOV[Governance / DAO]
  SC <--> POOLS[Copy Pools]
  SC <--> RISK[Risk Engine]
  SC <--> STAKE[Staking Tiers]
  TOK[TFT Token] --> STAKE
  SC --> TREAS[Treasury]
  IDX --> DAPP[Analytics / Leaderboards]
```

## Transaction Lifecycle (example)
1. Trader prepares order in UI; local pre‑check computes leverage, exposure, and predicted VF.  
2. Oracle price is fetched; UI displays slippage and risk flags.  
3. Trader submits tx to **Risk Engine** + **Copy Router**.  
4. Contracts validate limits; if valid, position is opened for trader and mirrored into eligible pools.  
5. PnL accrues; periodically rewards are computed and settled on‑chain.  
6. Reputation/NFTs update at checkpoint blocks.

## Data Flow
```mermaid
sequenceDiagram
  participant T as Trader
  participant UI as Frontend (TV + Prechecks)
  participant OR as Oracles
  participant RE as Risk Engine
  participant CP as Copy Pools
  participant ST as Staking
  T->>UI: Create/modify order
  UI->>OR: Fetch latest prices
  UI->>RE: Submit tx with params
  RE-->>CP: Validate + route copies
  RE-->>ST: Check tier limits
  RE-->>UI: Emit events (position opened)
  CP-->>UI: Pool mirrored pos
```

## Environments
- **Mainnet** (after audits)  
- **Testnet** for public beta and incentive programs  
- **Local forks** for integration testing

## Assumptions & Constraints
- Deterministic risk rules; no privileged backdoors.  
- Chain finality and oracle liveness are safety prerequisites.  
- Fees tuned for cost/benefit neutrality and sustainability.
