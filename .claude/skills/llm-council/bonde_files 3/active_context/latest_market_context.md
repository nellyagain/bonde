# Active Market Context — Nasdaq Extension

Source: Nasdaq Extension Report — ^IXIC
Generated: 2026-05-15 17:28:19
Analyzer: v1.11
Period: 1985-01-02 to 2026-05-15
Close: 26,403.07 on 2026-05-15
Current regime: Bull, based on close above SMA200

## Council interpretation

Use this as optional market context for Bonde council runs. This is not a hard actionability gate.

Current read: **risk-on but tactically extended**.

Practical implications:

- Market backdrop is supportive because Nasdaq remains in a Bull regime.
- Nasdaq is extended enough that the council should avoid chase entries.
- Prefer limit/pullback entries over buy-stops when candidate R:R is marginal.
- Be stricter on portfolio heat when multiple growth/cyclical names trigger together.
- Treat weekend/holiday exposure carefully if the review date is Friday.
- Do not cancel all trades solely because the Nasdaq is extended.

## Multi-MA snapshot

| MA | Value | Extension | Zone | Historical n in zone |
|---|---:|---:|---|---:|
| SMA10 | 26,008.91 | +1.52% | Extended | 2,010 |
| EMA21 | 25,305.36 | +4.34% | Extended | 2,054 |
| SMA50 | 23,569.21 | +12.02% | Extremely Extended | 499 |

## Current bull-regime reversion probabilities

| MA | P(revert <= 5d) | P(revert <= 10d) | P(revert <= 20d) | Median fwd ext 5d | Median fwd ext 10d | Median fwd ext 20d |
|---|---:|---:|---:|---:|---:|---:|
| SMA10 | 35.5% | 66.0% | 90.5% | +0.88% | +0.46% | +0.50% |
| EMA21 | 14.3% | 35.1% | 65.1% | +2.23% | +1.78% | +1.20% |
| SMA50 | 1.4% | 4.8% | 15.2% | +9.67% | +8.80% | +7.84% |

Interpretation: short-term compression to SMA10/EMA21 is plausible, but the SMA50 extension usually does not fully mean-revert quickly in a bull regime. This is an execution caution, not a broad bearish signal.

## Current bull-regime forward drawdown context

| MA zone basis | Median dd 5d | P25 dd 5d | P10 dd 5d | Median dd 10d | P25 dd 10d | P10 dd 10d | Median dd 20d | P25 dd 20d | P10 dd 20d |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| SMA10 extended | -0.48% | -1.57% | -3.03% | -0.91% | -2.55% | -4.49% | -1.55% | -3.71% | -6.89% |
| EMA21 extended | -0.39% | -1.44% | -2.72% | -0.80% | -2.36% | -4.10% | -1.41% | -3.43% | -6.55% |
| SMA50 extremely extended | -0.84% | -2.84% | -4.26% | -1.55% | -3.68% | -6.59% | -1.82% | -4.16% | -8.39% |

Interpretation: normal pullbacks can happen even within a bullish/extended tape. Candidate stops and position sizing should account for a possible 3-6% Nasdaq drawdown over 5-10 trading days when the tape is this extended.

## Time to next +/-3% move in current bull-regime zone

| MA zone basis | P(up first) | P(down first) | P(neither) | Median days |
|---|---:|---:|---:|---:|
| SMA10 extended | 62.8% | 36.4% | 0.8% | 12 |
| EMA21 extended | 65.3% | 33.3% | 1.4% | 12 |
| SMA50 extremely extended | 67.5% | 32.5% | 0.0% | 6 |

Interpretation: extension is not bearish by itself. Historically, in the current bull-regime extension zone, the first +/-3% move has still more often been upward than downward. Use this as a sizing/execution caution, not a cancellation rule.

## Nearby structural levels

Current price: 26,403.07.

Nearest resistance:

- 26,500.00: +0.37%, round-number resistance.
- 26,707.14: +1.15%, all-time high / 3-month high / 4-week high / 52-week high cluster.
- 27,000.00: +2.26%, round-number resistance.

Nearest support:

- 26,008.91: -1.49%, SMA10 + round-number area.
- 25,500.00: -3.42%, round-number support with confluence.
- 25,305.36: -4.16%, EMA21.
- 25,000.00: -5.31%, round-number support.
- 24,198.99 / 24,184.41: about -8.4%, 4-week low / AVWAP confluence.

## Council use rules

1. Do not treat this file as a hard buy/sell regime filter.
2. If candidate-specific actionability says `final_trade_status=COUNCIL`, this market context helps size and choose order type; it does not replace candidate review.
3. In this environment, prefer:
   - limit entries over chase buy-stops;
   - tighter portfolio heat controls;
   - explicit Friday/weekend order-duration instructions;
   - reduced size if multiple correlated growth/cyclical candidates trigger at once.
4. If the council promotes more than one candidate, the Portfolio Heat section should mention that the Nasdaq is extended and discuss whether entries should be conditional or mutually exclusive.
