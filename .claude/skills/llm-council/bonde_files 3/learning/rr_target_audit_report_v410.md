# R:R Target Realism Audit — 2026-05-21

*v4.13.7 — V5.9 target regex fix on top of v4.13.6 baseline (regex disambiguation only; audit logic unchanged).*

*RR_TARGET_AUDIT_MONITORING_ONLY*

## 1. Purpose

This is a measurement-only report. It does not change trading rules, action labels, A2/B+ eligibility, or the maturity-gated rule-change logic. The audit tests whether planned R:R values from the V5.9.7 actionability skill are realistic in practice by comparing them against actual price action and structural resistance (200 SMA).

> This audit is partial monitoring only until enough forward bars exist. PENDING_INSUFFICIENT_DATA rows must not be interpreted as failures. Do not change rules from this audit alone.

## 2. Maturity Status

- Rows audited: **39**
- Pending insufficient data: **9** (23.1%)

## 3. Summary

- Rows in audit universe (final_trade_status TRADE/COUNCIL): **39**
- TRADE rows: 1
- COUNCIL rows: **38**
- A1 rows: 1
- A2 rows: **16**
- B+ rows (C1/C2/C3): **14**
- Rows eligible for triggered-only views: **21**

- Rows with V5.9 target parsed: **32**
- Rows with no V5.9 target tag (pre-V5.8.9 or other): 7
- Rows with invalid target parse (geometry guard): 0
- Rows with V5.9 R:R parsed: 31
- Rows with R:R not logged (target may be present): 8

- R:R arithmetic valid (computed within 0.10 of logged): 30
- R:R arithmetic mismatch: 1

- computed_planned_rr ≥ 2.0 but effective_rr < 2.0: **2**
- 200SMA reduces effective R:R below 2.0: **2**

- Hit +1R but not +2R (5d): 3
- Hit +2R but not planned target: 1
- Hit planned target: **0**

## 4. A2 Audit (all / triggered-only / not-triggered)

| action_label   | view           |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:---------------|:---------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| A2             | ALL            |       16 |               14 |                      2.51 |               2.33 |                   2.7 |           0.74 |           0.74 |           1.17 |              0.37 |                -0.43 |                            100 |                        100 |           22.22 |           11.11 |                   0 |                             0 |                  66.67 |                          0 |
| A2             | TRIGGERED_ONLY |       11 |                9 |                      2.7  |               2.44 |                   2.7 |           0.74 |           0.74 |           1.17 |              0.37 |                -0.43 |                            100 |                        100 |           22.22 |           11.11 |                   0 |                             0 |                  66.67 |                          0 |
| A2             | NOT_TRIGGERED  |        4 |                4 |                      2.08 |               2.08 |                 nan   |         nan    |         nan    |         nan    |            nan    |               nan    |                            nan |                        nan |          nan    |          nan    |                 nan |                           nan |                 nan    |                        nan |

> **View arithmetic note:** ALL ≥ TRIGGERED_ONLY + NOT_TRIGGERED. Rows where `triggered_flag` is unresolved (NaN — typically `PENDING_INSUFFICIENT_DATA` before the 5d window matures) appear in ALL but in neither subset. The difference equals the count of trigger-pending rows.

## 4b. B+ Audit (by blocker type)

| view               | group_col          | group_value   |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:-------------------|:-------------------|:--------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| BPLUS_BLOCKER_TYPE | bplus_blocker_type | C1            |       12 |                6 |                      1.36 |               1.36 |                  1.45 |           0.5  |           0.5  |           1.15 |              0.17 |                -0.65 |                            nan |                        nan |              25 |               0 |                   0 |                             0 |                     75 |                          0 |
| BPLUS_BLOCKER_TYPE | bplus_blocker_type | C3            |        2 |                2 |                      2.25 |               2.25 |                  2.25 |           0.33 |           0.33 |           1.6  |              0.33 |                -1.27 |                            nan |                        nan |               0 |               0 |                   0 |                             0 |                    100 |                          0 |

## 5. Setup-family Audit

| view         | group_col    | group_value    |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:-------------|:-------------|:---------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| SETUP_FAMILY | setup_family | ACTIVE_BURST   |       13 |               12 |                      2.09 |               2.09 |                  2.23 |           0.81 |           0.81 |           1    |              0.37 |                -0.19 |                            nan |                        nan |           22.22 |           11.11 |                   0 |                             0 |                  66.67 |                          0 |
| SETUP_FAMILY | setup_family | DELAYED_EP     |        7 |                3 |                      2.25 |               2.25 |                  2.27 |           0.7  |           0.7  |           1.41 |              0.7  |                -0.71 |                            nan |                        nan |           50    |            0    |                   0 |                             0 |                  50    |                          0 |
| SETUP_FAMILY | setup_family | EP_ACTIVE      |       12 |               12 |                      1.83 |               1.6  |                  2.05 |           0.33 |           0.33 |           1.29 |              0.36 |                -0.96 |                             50 |                         50 |            0    |            0    |                   0 |                             0 |                 100    |                          0 |
| SETUP_FAMILY | setup_family | MOMENTUM_BURST |        1 |                0 |                    nan    |             nan    |                nan    |         nan    |         nan    |         nan    |            nan    |               nan    |                            nan |                        nan |          nan    |          nan    |                 nan |                           nan |                 nan    |                        nan |
| SETUP_FAMILY | setup_family | SLINGSHOT      |        5 |                2 |                      1.56 |               1.56 |                  2.17 |           0.92 |           0.92 |           1.72 |              0.92 |                -0.8  |                            nan |                        nan |           50    |            0    |                   0 |                             0 |                  50    |                          0 |
| SETUP_FAMILY | setup_family | UNKNOWN        |        1 |                1 |                      3.3  |               1.64 |                nan    |         nan    |         nan    |         nan    |            nan    |               nan    |                            100 |                        100 |          nan    |          nan    |                 nan |                           nan |                 nan    |                        nan |

## 6. Resistance Audit (by nearest_resistance_type)

| view                    | group_col               | group_value   |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:------------------------|:------------------------|:--------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| NEAREST_RESISTANCE_TYPE | nearest_resistance_type | NONE          |       36 |               27 |                      1.93 |               1.93 |                  2.14 |           0.65 |           0.65 |           1.25 |              0.37 |                -0.6  |                         nan    |                     nan    |           21.05 |            5.26 |                   0 |                             0 |                  73.68 |                          0 |
| NEAREST_RESISTANCE_TYPE | nearest_resistance_type | SMA200        |        3 |                3 |                      2.76 |               1.43 |                  2.5  |           0.39 |           0.39 |           0.86 |              0.39 |                -0.48 |                          66.67 |                      66.67 |            0    |            0    |                   0 |                             0 |                 100    |                          0 |

## 7. Top Warning Rows (computed_planned_rr ≥ 2.0 but effective or actual < 2.0)

| ticker   | signal_date   | action_label   | final_trade_status   | setup_family   |   computed_planned_rr |   effective_rr |   actual_entry_rr | nearest_resistance_type   |   nearest_resistance_price | target_realism_flag     |
|:---------|:--------------|:---------------|:---------------------|:---------------|----------------------:|---------------:|------------------:|:--------------------------|---------------------------:|:------------------------|
| IMSR     | 2026-05-06    | B              | COUNCIL              | UNKNOWN        |                  3.3  |           1.64 |            nan    | SMA200                    |                      10.61 | NOT_TRIGGERED           |
| BILL     | 2026-05-08    | A2             | COUNCIL              | EP_ACTIVE      |                  3.05 |           0.72 |              3.05 | SMA200                    |                      46.37 | RR_OVERSTATED_BY_200SMA |

## 8. Missing-field Diagnostics

- v59_target_tag_missing: 7 rows lacked the [V5.9 R:R floor] tag (likely pre-V5.8.9 rows). Target/R:R fields are NaN for these.
- v59_rr_tag_missing: 8 rows lacked a parseable R:R value. Reported as RR_NOT_LOGGED in target_realism_flag where target was parseable.

Notes on schema gaps in v4.13.7:
- `prior_high` is not pre-computed; nearest_resistance considers 200SMA only. The RR_OVERSTATED_BY_NEAREST_RESISTANCE flag is retained for forward compatibility but currently duplicates the SMA200 flag. A future patch can add prior-high derivation.
- `gap_fill_destroyed_rr`: NaN universally in v4.13.7. This metric requires trigger-day open/fill data, which is not preserved in current enriched outputs. Reserved for a future patch when intraday fill data is added.
- `actual_entry_rr` uses `trigger_price` as the fill proxy when triggered (not gap-aware). Mathematically equal to `computed_planned_rr` for triggered rows in v4.13.7 — a true gap-fill comparison requires intraday data.
- `target_hit_before_stop_5d` is set to UNKNOWN universally; daily bars do not resolve intraday order.
- Non-triggered rows have NaN R-multiples and hit flags by design. Signal-level fields (max_high_Nd, min_low_Nd, computed_planned_rr, effective_rr, target_realism_flag) remain populated for monitoring.

## 9. Interpretation Guidance

- Do not change rules from this report alone.
- Use this audit to diagnose whether A2 problems come from **target realism** rather than from selection alone.
- Rule changes require repeated mature evidence in the weekly cohort report, not partial monitoring.
- Triggered-only views are the primary read for trade quality. A2 rows that never triggered should not be counted as failed trades.
- Partial rows are monitoring-only; PENDING_INSUFFICIENT_DATA rows are not failures.

*No trading-rule recommendation is emitted from this audit.*
