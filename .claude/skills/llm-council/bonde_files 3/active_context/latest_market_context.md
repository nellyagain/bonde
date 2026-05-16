# ACTIVE MARKET CONTEXT — Nasdaq Extension

Generated: 2026-05-16
Source: Nasdaq Extension Report — ^IXIC, Analyzer v1.12
Status: CURRENT
Instruction: Treat this as current market context. Advisory only; do not override candidate-level `final_trade_status` or hard rejects.

## Summary

Current read: **Risk-on but tactically extended**.

- Nasdaq current regime: Bull, based on close above SMA200.
- Close: 26,225.14 on 2026-05-15.
- SMA10: +0.90%, Normal.
- EMA21: +3.70%, Extended.
- SMA50: +11.29%, Extremely Extended.

## Council interpretation

Use this file to adjust execution posture, not to cancel all trades.

Practical implications:

- The broader tape is supportive, but not early-cycle fresh.
- Avoid chase entries, especially wide Day-1 breakouts.
- Prefer limit/pullback entries over buy-stops when R:R is marginal.
- Be stricter with portfolio heat if multiple growth/cyclical names trigger together.
- If the review occurs before a weekend/holiday gap, avoid casual GTC language unless intentionally justified.

## Current bull-regime reversion probabilities

| MA | Current zone | P(revert <= 5d) | P(revert <= 10d) | P(revert <= 20d) | Median fwd ext 5d | Median fwd ext 10d | Median fwd ext 20d |
|---|---|---:|---:|---:|---:|---:|---:|
| SMA10 | Normal | 59.6% | 80.2% | 95.2% | +0.47% | +0.45% | +0.40% |
| EMA21 | Extended | 14.3% | 35.1% | 65.1% | +2.23% | +1.78% | +1.20% |
| SMA50 | Extremely Extended | 1.4% | 4.8% | 15.2% | +9.67% | +8.80% | +7.84% |

Interpretation: SMA10/EMA21 compression risk is real, but full SMA50 mean reversion is uncommon over short windows in bull regimes. This supports execution caution, not a bearish hard gate.

## Current bull-regime forward drawdown context

| Basis | Median dd 5d | P25 dd 5d | P10 dd 5d | Median dd 10d | P25 dd 10d | P10 dd 10d | Median dd 20d | P25 dd 20d | P10 dd 20d |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| SMA10 normal | -0.49% | -1.71% | -3.04% | -0.96% | -2.49% | -4.48% | -1.53% | -3.91% | -6.66% |
| EMA21 extended | -0.39% | -1.44% | -2.72% | -0.80% | -2.36% | -4.10% | -1.41% | -3.43% | -6.55% |
| SMA50 extremely extended | -0.84% | -2.84% | -4.26% | -1.55% | -3.68% | -6.59% | -1.82% | -4.16% | -8.39% |

Interpretation: candidate sizing/stops should account for a possible 3-6% Nasdaq drawdown over 5-10 trading days when the tape is this stretched.

## Time to next +/-3% move in current bull-regime zone

| Basis | P(up first) | P(down first) | P(neither) | Median days |
|---|---:|---:|---:|---:|
| SMA10 normal | 60.7% | 38.5% | 0.9% | 12 |
| EMA21 extended | 65.3% | 33.3% | 1.4% | 12 |
| SMA50 extremely extended | 67.5% | 32.5% | 0.0% | 6 |

Interpretation: extension is not bearish by itself. In the current bull-regime zone, the first +/-3% move has historically still more often been upward than downward.

## Nearby structural levels

Current price: 26,225.14.

Nearest resistance:

- 26,500.00: +1.05%, round-number resistance.
- 26,707.14: +1.84%, all-time high / 3-month high / 4-week high / 52-week high cluster.
- 27,000.00: +2.95%, round-number resistance.

Nearest support:

- 25,991.12: -0.89%, SMA10 + round-number area.
- 25,500.00: -2.77%, round-number support with confluence.
- 25,289.19: -3.57%, EMA21.
- 25,000.00: -4.67%, round-number support.
- 24,206.03: -7.70%, AVWAP / 4-week-low confluence.

## Council use rules

1. Do not treat this file as a hard buy/sell regime filter.
2. If candidate-specific actionability says `final_trade_status=COUNCIL`, this market context helps size and choose order type; it does not replace candidate review.
3. Prefer limit entries, controlled pullbacks, and portfolio-heat discipline when candidate R:R is marginal.
4. If the council promotes more than one candidate, the Portfolio Heat section should mention that Nasdaq is extended and discuss whether entries should be conditional or mutually exclusive.
