# Trader Sentiment Analysis

Analysis of 211,224 Hyperliquid perpetual-futures trades (32 accounts, 246 assets, May 2023 – May 2025) against the daily Bitcoin Fear & Greed Index, testing whether crowd sentiment predicts trader performance — and stress-testing the resulting strategy against per-account data and independently reconstructed BTC prices.

## Key Finding

Trader profitability is **U-shaped across sentiment**, not linear: performance is strongest at the emotional extremes (Extreme Fear, Extreme Greed) and weakest during plain Greed. A backtest against real BTC prices shows this holds up **only on the Extreme Fear side** — the "short the greed" leg of the naive strategy loses money once tested independently.

## Contents

| Path | Description |
|---|---|
| `report.docx` | Full report — Part 1 (sentiment vs. performance analysis) and Part 2 (per-account segmentation + strategy backtest), merged into a single document |
| `data/` | Raw trade-level and Fear & Greed Index data used in the analysis (zipped) |

## Report Structure

- **Part 1 — Trader Performance vs. Bitcoin Market Sentiment**: methodology, the U-shaped profitability pattern, volume/sizing behavior by regime, long vs. short positioning, coin-level sensitivity, and preliminary strategy recommendations.
- **Part 2 — Per-Account Segmentation & Strategy Backtest**: checks whether the pattern holds across individual accounts (rather than being driven by a few large traders) and backtests the proposed contrarian rule against reconstructed BTC prices. Ends with revised, final recommendations that supersede Part 1's preliminary ones.

## Methodology Summary

- Trades joined to daily Fear & Greed classification (99.997% match rate).
- Significance tested via Kruskal-Wallis (daily PnL across sentiment groups) and chi-square (win/loss vs. sentiment).
- Independent BTC price series reconstructed from volume-weighted execution prices to validate the strategy out-of-sample, rather than relying on the trades' own reported PnL.

## Headline Numbers

- Overall win rate: 83.2% of closed trades profitable; $10.25M net PnL on $1.19B volume.
- Win rate by sentiment: 76.2% (Extreme Fear) to 89.2% (Extreme Greed), χ² = 1,976, p < 0.0001.
- Top 5 accounts (15.6% of accounts) generated 62.0% of total PnL.
- Long Extreme Fear signal validated against BTC forward returns (p = 0.019); short Extreme Greed signal not significant (p = 0.43).

## Limitations

- Sample limited to 32 accounts; may reflect sophisticated-trader behavior rather than the broader market.
- Extreme Fear regime covers only 14 trading days (12 usable for the backtest) — directional, not definitive.
- Findings are observational, not causal.
