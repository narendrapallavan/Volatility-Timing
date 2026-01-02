# Volatility-Timing
Volatility targeting / volatility timing applied to the U.S. Profitability (RMW) factor (Ken French data): managed long-short factor, managed long-only portfolios, and MVO blend; includes performance stats, drawdowns, and turnover.

# Volatility Timing for the U.S. Profitability (RMW) Factor

## Overview
This project tests whether **volatility targeting** (volatility timing) improves risk-adjusted performance for factor investing strategies.
Mandate: U.S. Profitability (RMW) factor using data sourced from the Kenneth French database (provided in the coursework dataset).

**Deliverables**
- Executive memo (results + recommendation): `report/USA_Profitability_Memo.pdf`
- Assignment brief / questions: `report/Volatility-targeting_USA-Profitability.pdf`
- Replication model (forecasts, weights, returns, stats): `model/USA_Profitability_Factor_Volatility_Timing.xlsx`

## Strategy (volatility targeting)
Each month, the risky-asset weight is scaled by:
- weight_t = target_vol / forecast_vol_t

Forecast vol is produced from daily returns and mapped into a monthly forecast (rolling/EWMA-style approach per assignment framework).

## What was analyzed
### Part 1 — Long–short RMW factor premium
- Built a managed (vol-targeted) version of the RMW long–short factor.
- Set target volatility equal to the full-sample annualized volatility of the unmanaged factor.
- Compared unmanaged vs managed performance (return, vol, Sharpe, skew, kurtosis, max drawdown, turnover).

### Part 2 — Long-only profitability portfolios
- Repeated the same vol-targeting process for each provided long-only portfolio.
- Set each portfolio’s target vol to its own in-sample annualized vol.
- Evaluated where vol timing “works best” (long–short vs long-only) and why.

### Part 3 — Optimal combination (MVO)
- Treated (i) unmanaged long–short RMW and (ii) managed long–short RMW as two assets.
- Used mean–variance optimization to find the best combination and compared it to 100% unmanaged / 100% managed.

### Part 4 — Recommendation & implementation constraints
- Provided a recommendation and discussed practical frictions (turnover/trading costs, leverage limits, forecast error).

## Key results (from the memo)
### Long–short RMW (unmanaged vs managed)
- Unmanaged: mean annual return 3.25%, annual vol 7.71%, Sharpe 0.421, max drawdown 41.8%.
- Vol-targeted: mean annual return 3.55%, annual vol 7.71% (by construction), Sharpe 0.461, max drawdown 37.1%.
- Cost: annualized turnover ~1.21 (≈121% notional traded per year).

### Long-only portfolios
Volatility timing generally did **not** improve risk-adjusted performance for the long-only profitability portfolios; returns and Sharpe ratios typically fell even when drawdown sometimes improved.

### MVO blend (unmanaged + managed LS RMW)
The mean–variance optimization favored a mix tilted toward the managed strategy (≈18% unmanaged / 82% managed), delivering a slightly higher Sharpe than either strategy alone.

## How to review quickly
1. Read `report/USA_Profitability_Memo.pdf` for the investment-committee style narrative and tables.
2. Open `model/USA_Profitability_Factor_Volatility_Timing.xlsx` to audit the volatility forecast, monthly weights, managed returns, turnover, and performance statistics.

