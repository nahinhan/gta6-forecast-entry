# GTA VI Trophy Rarity Forecast

[![Competition](https://make.fun/badge/gta6-trophy-rarity-forecast-01.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01)
[![Rank](https://make.fun/badge/gta6-trophy-rarity-forecast-01/nahinhan/gta6-forecast-entry/rank.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01)
[![Reward](https://make.fun/badge/gta6-trophy-rarity-forecast-01/nahinhan/gta6-forecast-entry/reward.svg)](https://make.fun/bounty/gta6-trophy-rarity-forecast-01)

## Algorithm: Trend-Decaying Log-Odds Model

This entry implements a deterministic forecasting model that improves upon the house baseline by estimating historical trends on the log-odds (logit) scale.

### Key Features:
- **Logit Transformation:** Rates are converted to log-odds to handle the bounded nature of percentages (0.01% to 99.99%).
- **Linear Trend Estimation:** For each trophy, a linear regression is performed on the historical logit values to determine its earn rate velocity.
- **Trend Decay & Capping:** Trends are decayed exponentially over the forecast horizon to prevent over-extrapolation, and the total logit move is capped to ensure stability.
- **Calibrated Quantile Spread:** A random-walk spread is applied on the logit scale, with a slightly widened tail for the 5% and 95% quantiles to account for unexpected volatility.
- **Deterministic & Efficient:** The model is strictly deterministic, uses only the Node.js standard library, and completes within the required 8-second runtime per case.

## Local Test Results
The model was tested against the practice cases `p00` and `p01` from the competition kit. 

| Case | Status | Runtime |
|------|--------|---------|
| p00  | Valid  | < 100ms |
| p01  | Valid  | < 100ms |

## Requirements
- Node.js 22+
- Standard library only

## Usage
```bash
MAKEFUN_INPUT_DIR=input MAKEFUN_OUTPUT_DIR=output node main.ts
```
