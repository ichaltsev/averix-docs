---
title: Risk Management
---
## Philosophy
Capital protection and **predictable risk** are paramount. Averix encodes limits in contracts to prevent discretionary overrides.

## Engine Structure
- **Exposure Limits:** per asset, per account, and per tier.  
- **Drawdown Checks:** intraday and rolling.  
- **Position Rules:** max leverage, size, and time‑in‑market constraints.  
- **Violation Registry:** on‑chain log driving reward penalties.

## Reward Formula
```
Reward = Base × Weight × SeasonMultiplier × (1 − ViolationFactor) + AchievementBonus
```
- **Base:** baseline epoch reward for activity cohort.  
- **Weight:** risk‑adjusted performance weight.  
- **SeasonMultiplier:** seasonal scaling (events, campaigns).  
- **ViolationFactor (VF):** from 0.0 to 0.9+ based on rule breaches.  
- **AchievementBonus:** NFTs, streaks, and milestone rewards.

## Violation Examples
- Breach of max leverage or position size.  
- Holding through restricted events (e.g., flagged volatility).  
- Oracle divergence beyond tolerance.

## Dynamic Leverage Model
Leverage decreases as volatility ↑ or as exposure concentration ↑. Governance can tune curves per asset class.

## Reputation
A cumulative score derived from: Sharpe‑like metrics, adherence to limits, and season performance, minted as **Reputation NFTs** per season.
