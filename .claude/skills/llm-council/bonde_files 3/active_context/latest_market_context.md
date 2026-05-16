# Nasdaq Extension Report — ^IXIC

_Generated: 2026-05-16 01:56:15 · Analyzer v1.12_  
_Period: 1985-01-02 → 2026-05-15 (10,423 trading days)_  
_Close: **26,225.14** (2026-05-15)_  
_Current regime: **Bull** (close vs SMA200)_

⚠ = cell has fewer than 30 historical observations; treat as anecdotal.

## Contents

- [Multi-MA Snapshot](#multi-ma-snapshot)
- [Support & Resistance Levels](#support--resistance-levels)
- [Forward Drawdown — Current Zone](#forward-drawdown--current-zone)
- [Flat-Price Projection](#flat-price-projection)
- [Time to Next Move](#time-to-next-move)
- [SMA10 Detail](#sma10-detail)
- [EMA21 Detail](#ema21-detail)
- [SMA50 Detail](#sma50-detail)
- [Methodology](#methodology)

## Multi-MA Snapshot

| MA | Value | Extension | Zone | n in zone |
|---|---|---|---|---|
| **SMA10** | 25,991.12 | **+0.90%** | ⚪ Normal | 5,190 |
| **EMA21** | 25,289.19 | **+3.70%** | 🟡 Extended | 2,054 |
| **SMA50** | 23,565.65 | **+11.29%** | 🔴 Extremely Extended | 499 |

### Reversion & forward extension — blended (current zone)

| MA | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Median fwd ext 5d | Median fwd ext 10d | Median fwd ext 20d |
|---|---|---|---|---|---|---|
| **SMA10** | 60.1% | 80.6% | 94.9% | +0.46% | +0.41% | +0.41% |
| **EMA21** | 15.0% | 35.3% | 64.6% | +2.25% | +1.82% | +1.20% |
| **SMA50** | 1.4% | 5.0% | 18.2% | +9.80% | +8.82% | +7.41% |

### Reversion in current regime (Bull)

| MA | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Median fwd ext 5d | Median fwd ext 10d | Median fwd ext 20d |
|---|---|---|---|---|---|---|
| **SMA10** (n=4,166) | 59.6% | 80.2% | 95.2% | +0.47% | +0.45% | +0.40% |
| **EMA21** (n=1,747) | 14.3% | 35.1% | 65.1% | +2.23% | +1.78% | +1.20% |
| **SMA50** (n=415) | 1.4% | 4.8% | 15.2% | +9.67% | +8.80% | +7.84% |

## Support & Resistance Levels

Current price: **26,225.14** (2026-05-15). Structural price-level analysis from 5-bar pivots, recent N-bar highs/lows, all-time high, moving averages, round numbers, and **AVWAP from significant highs/lows**. Levels within 0.2% of each other are collapsed to the more important type (AVWAP pairs use a tighter 0.05% threshold). **Touches** = distinct historical approaches (±0.3% band) over last 252 bars; MA touches are computed against the MA series (dynamic), other levels against current price (static). **Conf** = number of nearby levels within ±1.0% (including self); Conf ≥ 2 = confluence zone. Absorbed-type annotations (`+ X`) show what got merged into this row during dedupe.

**These levels mark where historical structure sits — not predictions of which will hold.** Use as price-target context, cross-reference with the statistical zone analysis below.

### Nearest Resistance — above 26,225.14

| Distance | Price | Type | Touches | Conf | Last touch |
|---|---|---|---|---|---|
| **+1.05%** | 26,500.00 | Round (500) | 1 | **2** | 2026-05-15 |
| **+1.84%** | 26,707.14 | All-time high + 3-month high + 4-week high + 52-week high | 1 | **2** | 2026-05-14 |
| **+2.95%** | 27,000.00 | Round (500) | 0 | 1 | — |
| **+4.86%** | 27,500.00 | Round (500) | 0 | 1 | — |
| **+6.77%** | 28,000.00 | Round (500) | 0 | 1 | — |
| **+8.67%** | 28,500.00 | Round (500) | 0 | 1 | — |

### Nearest Support — below 26,225.14

| Distance | Price | Type | Touches | Conf | Last touch |
|---|---|---|---|---|---|
| **-0.89%** | 25,991.12 | SMA10 + Round (500) | 16 | 1 | 2026-04-30 |
| **-2.77%** | 25,500.00 | Round (500) | 1 | **2** | 2026-05-06 |
| **-3.57%** | 25,289.19 | EMA21 | 15 | **2** | 2026-04-07 |
| **-4.67%** | 25,000.00 | Round (500) | 1 | 1 | 2026-05-04 |
| **-6.58%** | 24,500.00 | Round (500) | 1 | 1 | 2026-04-30 |
| **-7.70%** | 24,206.03 | AVWAP from 3-month low + 4-week low + AVWAP from pivot low | 1 | **2** | 2026-04-23 |
| **-8.53%** | 23,988.27 | Long-term pivot high (broken) + Round (500) + Long-term pivot high (broken) | 3 | **3** | 2026-04-16 |
| **-9.20%** | 23,813.30 | Long-term pivot high (broken) | 4 | **5** | 2026-04-15 |
| **-9.76%** | 23,665.15 | Long-term pivot high (broken) + Long-term pivot high (broken) | 6 | **6** | 2026-04-15 |
| **-10.00%** | 23,603.90 | AVWAP from pivot high (broken) | 6 | **6** | 2026-04-15 |

## Forward Drawdown — Current Zone

Distribution of forward maximum drawdown (deepest peak-to-trough drop from current close) over each window. Computed across all historical days in the current zone, blended regime.

| MA | n | Median dd 5d | P25 dd 5d | P10 dd 5d | Median dd 10d | P25 dd 10d | P10 dd 10d | Median dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| **SMA10** | 5,190 | -0.51% | -1.77% | -3.24% | -1.00% | -2.63% | -4.87% | -1.58% | -4.15% | -7.11% |
| **EMA21** | 2,054 | -0.42% | -1.50% | -2.86% | -0.84% | -2.39% | -4.21% | -1.43% | -3.55% | -6.99% |
| **SMA50** | 499 | -0.97% | -3.04% | -4.64% | -1.80% | -3.95% | -6.92% | -2.14% | -4.58% | -9.45% |

- **Median dd**: half of historical periods saw a deeper drawdown.
- **P25 dd**: 75% of periods saw a less deep drawdown; this is the "worse than typical" pullback.
- **P10 dd**: 90% of periods saw a less deep drawdown; this is the "severe but not extreme" pullback. Useful for stop placement.

### Forward drawdown in current regime (Bull)

| MA | n | Median dd 5d | P25 dd 5d | P10 dd 5d | Median dd 10d | P25 dd 10d | P10 dd 10d | Median dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| **SMA10** | 4,166 | -0.49% | -1.71% | -3.04% | -0.96% | -2.49% | -4.48% | -1.53% | -3.91% | -6.66% |
| **EMA21** | 1,747 | -0.39% | -1.44% | -2.72% | -0.80% | -2.36% | -4.10% | -1.41% | -3.43% | -6.55% |
| **SMA50** | 415 | -0.84% | -2.84% | -4.26% | -1.55% | -3.68% | -6.59% | -1.82% | -4.16% | -8.39% |

## Flat-Price Projection

If close holds at **26,225.14** through each horizon, the MA itself will move (oldest bars roll off, replaced by current price). The projection shows what extension would mechanically be at each horizon given no price change.

Comparing the projection to historical median forward extension reveals the typical compression mechanism:
- If **projection ≈ historical median** → compression historically comes from SMA catching up.
- If **projection > historical median** → compression typically involves some price drop too.
- If **projection < historical median** → in this zone, price has historically continued to rise even as extension compressed.

| MA | Current ext | Proj 5d (flat) | Hist median 5d | Proj 10d (flat) | Hist median 10d | Proj 20d (flat) | Hist median 20d |
|---|---|---|---|---|---|---|---|
| **SMA10** | +0.90% | -0.19% | +0.46% | +0.00% | +0.41% | +0.00% | +0.41% |
| **EMA21** | +3.70% | +2.27% | +2.25% | +1.40% | +1.82% | +0.53% | +1.20% |
| **SMA50** | +11.29% | +9.58% | +9.80% | +7.79% | +8.82% | +3.82% | +7.41% |

## Time to Next Move (±3.0% within 60d)

From historical days in the current zone, how often was the first ±3.0% move up vs. down, and how many trading days did it take?

| MA | Current Zone | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|---|
| **SMA10** | ⚪ Normal | 5,190 | 60.4% | 38.9% | 0.8% | 6 | 11 | 20 |
| **EMA21** | 🟡 Extended | 2,054 | 65.4% | 33.3% | 1.3% | 6 | 12 | 19 |
| **SMA50** | 🔴 Extremely Extended | 499 | 64.3% | 35.7% | 0.0% | 3 | 5 | 9 |

- **P(up first)** / **P(down first)**: probability the first ±3.0% move was in that direction.
- **P(neither)**: probability no ±3.0% move occurred within 60 trading days.
- **Median days**: median trading days to first ±3.0% move, conditional on it occurring within the window.

### Time to Next Move in Current Regime (Bull)

| MA | Current Zone | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|---|
| **SMA10** | ⚪ Normal | 4,166 | 60.7% | 38.5% | 0.9% | 7 | 12 | 21 |
| **EMA21** | 🟡 Extended | 1,747 | 65.3% | 33.3% | 1.4% | 7 | 12 | 19 |
| **SMA50** | 🔴 Extremely Extended | 415 | 67.5% | 32.5% | 0.0% | 3 | 6 | 10 |

---

## SMA10 Detail

**Current:** extension **+0.90%** · zone ⚪ **Normal**

![SMA10 extension distribution](./SMA10_distribution.png)

### Zone scale

| Zone | From | To |
|---|---|---|
| 🟦 Extremely Compressed | −∞ | -3.6% |
| 🟢 Compressed | -3.6% | -0.8% |
| ⚪ Normal ← **current** | -0.8% | +1.5% |
| 🟡 Extended | +1.5% | +3.4% |
| 🔴 Extremely Extended | +3.4% | +∞ |

### Reversion probability & median forward extension by zone (blended)

| Zone | n | Median ext | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Med fwd ext 5d | Med fwd ext 10d | Med fwd ext 20d |
|---|---|---|---|---|---|---|---|---|
| Extremely Compressed | 519 | -4.94% | 48.0% | 82.5% | 99.4% | -0.90% | +0.01% | +0.64% |
| Compressed | 2,121 | -1.72% | 59.2% | 86.4% | 99.6% | -0.21% | +0.49% | +0.42% |
| Normal ← **current** | 5,190 | +0.46% | 60.1% | 80.6% | 94.9% | +0.46% | +0.41% | +0.41% |
| Extended | 2,010 | +2.09% | 37.9% | 67.2% | 91.0% | +0.88% | +0.47% | +0.47% |
| Extremely Extended | 514 | +4.29% | 34.2% | 63.0% | 91.2% | +1.70% | +0.88% | +0.53% |

### Forward drawdown by zone (blended)

| Zone | n | Med dd 5d | P25 dd 5d | P10 dd 5d | Med dd 10d | P25 dd 10d | P10 dd 10d | Med dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| Extremely Compressed | 519 | -1.68% | -4.27% | -7.93% | -2.97% | -6.81% | -11.90% | -4.78% | -11.12% | -17.54% |
| Compressed | 2,121 | -1.06% | -2.76% | -4.79% | -1.74% | -3.96% | -6.99% | -2.61% | -5.69% | -10.38% |
| Normal ← **current** | 5,190 | -0.51% | -1.77% | -3.24% | -1.00% | -2.63% | -4.87% | -1.58% | -4.15% | -7.11% |
| Extended | 2,010 | -0.55% | -1.74% | -3.43% | -1.00% | -2.79% | -5.31% | -1.62% | -3.95% | -7.83% |
| Extremely Extended | 514 | -1.05% | -3.03% | -5.35% | -1.85% | -4.24% | -8.17% | -2.47% | -6.25% | -11.78% |

### Current zone — split by regime

| Regime | n | Median ext | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Med fwd ext 5d | Med fwd ext 10d | Med fwd ext 20d |
|---|---|---|---|---|---|---|---|---|
| Bull ← **current** | 4,166 | +0.51% | 59.6% | 80.2% | 95.2% | +0.47% | +0.45% | +0.40% |
| Bear | 905 | +0.30% | 62.8% | 82.5% | 93.7% | +0.47% | +0.31% | +0.54% |

### Drawdown in current zone — split by regime

| Regime | n | Med dd 5d | P25 dd 5d | P10 dd 5d | Med dd 10d | P25 dd 10d | P10 dd 10d | Med dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| Bull ← **current** | 4,166 | -0.49% | -1.71% | -3.04% | -0.96% | -2.49% | -4.48% | -1.53% | -3.91% | -6.66% |
| Bear | 905 | -0.64% | -2.40% | -4.82% | -1.20% | -3.55% | -7.24% | -2.04% | -5.72% | -10.09% |

### Time to next ±3.0% move by zone (blended)

| Zone | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|
| Extremely Compressed | 519 | 58.4% | 41.6% | 0.0% | 1 | 2 | 5 |
| Compressed | 2,121 | 53.9% | 45.8% | 0.2% | 3 | 6 | 12 |
| Normal ← **current** | 5,190 | 60.4% | 38.9% | 0.8% | 6 | 11 | 20 |
| Extended | 2,010 | 62.4% | 36.7% | 0.9% | 6 | 11 | 18 |
| Extremely Extended | 514 | 62.1% | 37.9% | 0.0% | 3 | 5 | 9 |

### Time to next move in current zone — split by regime

| Regime | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|
| Bull ← **current** | 4,166 | 60.7% | 38.5% | 0.9% | 7 | 12 | 21 |
| Bear | 905 | 59.0% | 40.8% | 0.2% | 3 | 7 | 13 |

---

## EMA21 Detail

**Current:** extension **+3.70%** · zone 🟡 **Extended**

![EMA21 extension distribution](./EMA21_distribution.png)

### Zone scale

| Zone | From | To |
|---|---|---|
| 🟦 Extremely Compressed | −∞ | -4.7% |
| 🟢 Compressed | -4.7% | -0.9% |
| ⚪ Normal | -0.9% | +2.2% |
| 🟡 Extended ← **current** | +2.2% | +4.4% |
| 🔴 Extremely Extended | +4.4% | +∞ |

### Reversion probability & median forward extension by zone (blended)

| Zone | n | Median ext | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Med fwd ext 5d | Med fwd ext 10d | Med fwd ext 20d |
|---|---|---|---|---|---|---|---|---|
| Extremely Compressed | 522 | -6.56% | 17.8% | 44.3% | 77.2% | -3.96% | -2.81% | -0.51% |
| Compressed | 2,048 | -2.18% | 41.3% | 65.6% | 88.4% | -1.18% | -0.33% | +0.41% |
| Normal | 5,219 | +0.85% | 48.9% | 64.9% | 82.3% | +0.87% | +0.78% | +0.84% |
| Extended ← **current** | 2,054 | +2.86% | 15.0% | 35.3% | 64.6% | +2.25% | +1.82% | +1.20% |
| Extremely Extended | 520 | +5.51% | 11.5% | 29.4% | 53.5% | +3.96% | +3.36% | +2.31% |

### Forward drawdown by zone (blended)

| Zone | n | Med dd 5d | P25 dd 5d | P10 dd 5d | Med dd 10d | P25 dd 10d | P10 dd 10d | Med dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| Extremely Compressed | 522 | -1.99% | -5.11% | -9.29% | -3.72% | -8.03% | -12.88% | -5.86% | -11.87% | -18.33% |
| Compressed | 2,048 | -1.19% | -2.94% | -5.25% | -1.95% | -4.24% | -7.46% | -2.87% | -6.06% | -11.28% |
| Normal | 5,219 | -0.51% | -1.80% | -3.34% | -1.01% | -2.66% | -5.00% | -1.62% | -4.20% | -7.15% |
| Extended ← **current** | 2,054 | -0.42% | -1.50% | -2.86% | -0.84% | -2.39% | -4.21% | -1.43% | -3.55% | -6.99% |
| Extremely Extended | 520 | -1.03% | -2.93% | -4.63% | -1.77% | -3.88% | -6.94% | -2.29% | -4.76% | -9.70% |

### Current zone — split by regime

| Regime | n | Median ext | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Med fwd ext 5d | Med fwd ext 10d | Med fwd ext 20d |
|---|---|---|---|---|---|---|---|---|
| Bull ← **current** | 1,747 | +2.85% | 14.3% | 35.1% | 65.1% | +2.23% | +1.78% | +1.20% |
| Bear | 286 | +2.95% | 20.3% | 36.7% | 60.1% | +2.59% | +2.37% | +1.61% |

### Drawdown in current zone — split by regime

| Regime | n | Med dd 5d | P25 dd 5d | P10 dd 5d | Med dd 10d | P25 dd 10d | P10 dd 10d | Med dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| Bull ← **current** | 1,747 | -0.39% | -1.44% | -2.72% | -0.80% | -2.36% | -4.10% | -1.41% | -3.43% | -6.55% |
| Bear | 286 | -0.71% | -1.91% | -4.19% | -1.15% | -2.87% | -6.56% | -1.36% | -4.10% | -10.68% |

### Time to next ±3.0% move by zone (blended)

| Zone | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|
| Extremely Compressed | 522 | 56.9% | 43.1% | 0.0% | 1 | 2 | 4 |
| Compressed | 2,048 | 53.7% | 45.9% | 0.4% | 3 | 6 | 11 |
| Normal | 5,219 | 59.3% | 40.2% | 0.5% | 6 | 11 | 20 |
| Extended ← **current** | 2,054 | 65.4% | 33.3% | 1.3% | 6 | 12 | 19 |
| Extremely Extended | 520 | 63.3% | 36.2% | 0.6% | 3 | 5 | 9 |

### Time to next move in current zone — split by regime

| Regime | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|
| Bull ← **current** | 1,747 | 65.3% | 33.3% | 1.4% | 7 | 12 | 19 |
| Bear | 286 | 68.5% | 30.4% | 1.0% | 3 | 6 | 14 |

---

## SMA50 Detail

**Current:** extension **+11.29%** · zone 🔴 **Extremely Extended**

![SMA50 extension distribution](./SMA50_distribution.png)

### Zone scale

| Zone | From | To |
|---|---|---|
| 🟦 Extremely Compressed | −∞ | -8.6% |
| 🟢 Compressed | -8.6% | -1.5% |
| ⚪ Normal | -1.5% | +4.4% |
| 🟡 Extended | +4.4% | +8.7% |
| 🔴 Extremely Extended ← **current** | +8.7% | +∞ |

### Reversion probability & median forward extension by zone (blended)

| Zone | n | Median ext | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Med fwd ext 5d | Med fwd ext 10d | Med fwd ext 20d |
|---|---|---|---|---|---|---|---|---|
| Extremely Compressed | 525 | -12.44% | 2.3% | 13.1% | 36.8% | -11.10% | -9.43% | -5.01% |
| Compressed | 2,031 | -3.61% | 19.1% | 37.1% | 60.1% | -3.03% | -2.22% | -0.76% |
| Normal | 5,204 | +1.80% | 31.6% | 43.9% | 58.0% | +1.85% | +1.87% | +1.86% |
| Extended | 2,055 | +5.81% | 2.6% | 10.2% | 28.1% | +5.46% | +4.94% | +3.64% |
| Extremely Extended ← **current** | 499 | +10.76% | 1.4% | 5.0% | 18.2% | +9.80% | +8.82% | +7.41% |

### Forward drawdown by zone (blended)

| Zone | n | Med dd 5d | P25 dd 5d | P10 dd 5d | Med dd 10d | P25 dd 10d | P10 dd 10d | Med dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| Extremely Compressed | 525 | -2.26% | -6.09% | -10.03% | -4.03% | -8.70% | -13.17% | -7.00% | -12.57% | -17.10% |
| Compressed | 2,031 | -1.15% | -3.00% | -5.21% | -1.84% | -4.35% | -7.65% | -2.82% | -6.17% | -11.57% |
| Normal | 5,204 | -0.51% | -1.76% | -3.24% | -1.00% | -2.66% | -4.85% | -1.58% | -4.07% | -7.06% |
| Extended | 2,055 | -0.45% | -1.58% | -2.86% | -0.91% | -2.47% | -4.40% | -1.62% | -3.77% | -7.04% |
| Extremely Extended ← **current** | 499 | -0.97% | -3.04% | -4.64% | -1.80% | -3.95% | -6.92% | -2.14% | -4.58% | -9.45% |

### Current zone — split by regime

| Regime | n | Median ext | P(revert ≤ 5d) | P(revert ≤ 10d) | P(revert ≤ 20d) | Med fwd ext 5d | Med fwd ext 10d | Med fwd ext 20d |
|---|---|---|---|---|---|---|---|---|
| Bull ← **current** | 415 | +10.71% | 1.4% | 4.8% | 15.2% | +9.67% | +8.80% | +7.84% |
| Bear | 84 | +10.93% | 1.2% | 6.0% | 33.3% | +10.26% | +9.04% | +5.36% |

### Drawdown in current zone — split by regime

| Regime | n | Med dd 5d | P25 dd 5d | P10 dd 5d | Med dd 10d | P25 dd 10d | P10 dd 10d | Med dd 20d | P25 dd 20d | P10 dd 20d |
|---|---|---|---|---|---|---|---|---|---|---|
| Bull ← **current** | 415 | -0.84% | -2.84% | -4.26% | -1.55% | -3.68% | -6.59% | -1.82% | -4.16% | -8.39% |
| Bear | 84 | -2.50% | -4.22% | -5.67% | -3.11% | -5.62% | -8.39% | -3.72% | -7.75% | -11.47% |

### Time to next ±3.0% move by zone (blended)

| Zone | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|
| Extremely Compressed | 525 | 52.0% | 48.0% | 0.0% | 1 | 2 | 4 |
| Compressed | 2,031 | 54.8% | 45.0% | 0.2% | 3 | 6 | 11 |
| Normal | 5,204 | 60.0% | 39.5% | 0.5% | 6 | 11 | 20 |
| Extended | 2,055 | 63.5% | 35.1% | 1.4% | 6 | 11 | 18 |
| Extremely Extended ← **current** | 499 | 64.3% | 35.7% | 0.0% | 3 | 5 | 9 |

### Time to next move in current zone — split by regime

| Regime | n | P(up first) | P(down first) | P(neither) | P25 days | Median days | P75 days |
|---|---|---|---|---|---|---|---|
| Bull ← **current** | 415 | 67.5% | 32.5% | 0.0% | 3 | 6 | 10 |
| Bear | 84 | 48.8% | 51.2% | 0.0% | 2 | 4 | 6 |

---

## Methodology

- **Data:** yfinance `^IXIC`, auto-adjusted close, 1985-01-02 → 2026-05-15.
- **Extension:** (close − MA) / MA × 100, computed per MA.
- **EMA convention:** pandas `ewm(span=N, adjust=False)`, matches TradingView.
- **Regime:** Bull if close > SMA200, Bear if close < SMA200. No 'Sideways' subclass.
- **Reversion event:** extension crosses through 0 within the forward window.
- **Median forward extension:** where extension typically sits at horizon t+w, by starting zone.
- **Forward drawdown:** for each historical day, the deepest signed % drop in close over the window. Aggregated by zone as median / P25 / P10.
- **Flat-price projection:** closed-form. For SMA, the projected MA replaces the rolled-off bars with the current close. For EMA, uses `EMA(t+w) = C − (1−α)^w · (C − EMA(t))` where α = 2/(period+1).
- **Time to next move:** for each historical day, days until close moves by ±3.0% from start, within 60 trading days. `P(up/down/neither first)` are mutually exclusive and sum to 1. `Median days` is conditional on the move happening within the window — read alongside P(neither) to see the conditioning.
- **Support & Resistance:** mechanical level identification. Pivots = symmetric 5-bar swing. Pivots older than 252 bars (~1 year) dropped. Levels within 0.2% of each other deduplicated; the more important type wins (ATH > major MAs > 52w > pivots > shorter N-bar > round numbers). Round-number levels at 500 interval within ±10% of current price. Levels beyond ±15.0% of current price are filtered out. Pivot highs below current price (and pivot lows above) are labeled `(broken)` to indicate role reversal. S/R is structural and does NOT modify any statistical zone calculations.
- **Touch counting:** for each level, count of distinct historical approaches over last 252 bars. A bar counts as touching if its high-low range overlaps ±0.3% band around the level. Consecutive touching bars within 3 bars collapse to one event. For moving averages (SMA10, EMA21, SMA50, SMA200), the level is dynamic — each bar's touch is evaluated against `MA(t)` not `MA(current)`. Last-touch date shows the most recent bar that touched.
- **AVWAP from anchors:** anchored VWAP from significant high/low anchors (52w high/low, ATH, 3-month high/low, top 2 recent pivot highs/lows) to current bar. AVWAP(t) = Σ((H+L+C)/3 × Vol) / Σ(Vol) from anchor to t. Anchors ≥ 20 bars old (younger ≈ simple mean) and ≤ 504 bars old. AVWAP pairs use a tighter dedupe threshold (0.05% vs 0.2% for others) so AVWAPs survive more often when sitting near but not on top of static levels.
- **Confluence count:** for each level, count of other S/R levels within ±1.0% (including self). Computed AFTER dedupe on the unique-type set, so confluence reflects how many DIFFERENT level types coincide. Conf ≥ 2 indicates a cluster zone — usually more historically respected than isolated levels.
- **Dedupe annotations:** when a level absorbs another during dedupe, the absorbed type is appended to the Type column as `+ X` (e.g., `Round (500) + 4-week low`). Reveals what's structurally clustered behind the displayed level.
- **Zones:** snapped from full-history P5 / P25 / P75 / P95 per MA. Each MA has its own zones.
- **Sample correlation:** forward windows overlap; probabilities are well-calibrated base rates but adjacent-day samples are not independent.
- **Low-n flag:** cells with n < 30 marked ⚠.
- **No composite score, no stack state classifier:** the three MA extensions are highly correlated; combining them with weights would invent parameters without out-of-sample justification. The v1.2 stack state classifier was cut after real-data validation showed forward returns were statistically indistinguishable across states.
