# R:R Target Realism Audit — 2026-05-25

*v4.13.7 — V5.9 target regex fix on top of v4.13.6 baseline (regex disambiguation only; audit logic unchanged).*

*RR_TARGET_AUDIT_MONITORING_ONLY*

## 1. Purpose

This is a measurement-only report. It does not change trading rules, action labels, A2/B+ eligibility, or the maturity-gated rule-change logic. The audit tests whether planned R:R values from the V5.9.7 actionability skill are realistic in practice by comparing them against actual price action and structural resistance (200 SMA).

> This audit is partial monitoring only until enough forward bars exist. PENDING_INSUFFICIENT_DATA rows must not be interpreted as failures. Do not change rules from this audit alone.

## 2. Maturity Status

- Rows audited: **31**
- Pending insufficient data: **0** (0.0%)

## 3. Summary

- Rows in audit universe (final_trade_status TRADE/COUNCIL): **31**
- TRADE rows: 1
- COUNCIL rows: **30**
- A1 rows: 1
- A2 rows: **14**
- B+ rows (C1/C2/C3): **8**
- Rows eligible for triggered-only views: **22**

- Rows with V5.9 target parsed: **27**
- Rows with no V5.9 target tag (pre-V5.8.9 or other): 4
- Rows with invalid target parse (geometry guard): 0
- Rows with V5.9 R:R parsed: 26
- Rows with R:R not logged (target may be present): 5

- R:R arithmetic valid (computed within 0.10 of logged): 25
- R:R arithmetic mismatch: 1

- computed_planned_rr ≥ 2.0 but effective_rr < 2.0: **0**
- 200SMA reduces effective R:R below 2.0: **0**

- Hit +1R but not +2R (5d): 3
- Hit +2R but not planned target: 1
- Hit planned target: **0**

## 4. A2 Audit (all / triggered-only / not-triggered)

| action_label   | view           |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:---------------|:---------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| A2             | ALL            |       14 |               14 |                      2.42 |               2.42 |                   2.6 |           2.19 |           2.19 |           -0.1 |              0.42 |                 2.29 |                            nan |                        nan |              30 |              20 |                   0 |                             0 |                     60 |                          0 |
| A2             | TRIGGERED_ONLY |       10 |               10 |                      2.6  |               2.6  |                   2.6 |           2.19 |           2.19 |           -0.1 |              0.42 |                 2.29 |                            nan |                        nan |              30 |              20 |                   0 |                             0 |                     60 |                          0 |
| A2             | NOT_TRIGGERED  |        4 |                4 |                      2.08 |               2.08 |                 nan   |         nan    |         nan    |          nan   |            nan    |               nan    |                            nan |                        nan |             nan |             nan |                 nan |                           nan |                    nan |                        nan |

> **View arithmetic note:** ALL ≥ TRIGGERED_ONLY + NOT_TRIGGERED. Rows where `triggered_flag` is unresolved (NaN — typically `PENDING_INSUFFICIENT_DATA` before the 5d window matures) appear in ALL but in neither subset. The difference equals the count of trigger-pending rows.

## 4b. B+ Audit (by blocker type)

| view               | group_col          | group_value   |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:-------------------|:-------------------|:--------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| BPLUS_BLOCKER_TYPE | bplus_blocker_type | C1            |        6 |                6 |                      1.53 |               1.53 |                  1.56 |           0.5  |           0.5  |           1.15 |              0.17 |                -0.65 |                            nan |                        nan |              25 |               0 |                   0 |                             0 |                     75 |                          0 |
| BPLUS_BLOCKER_TYPE | bplus_blocker_type | C3            |        2 |                2 |                      2.25 |               2.25 |                  2.25 |           0.33 |           0.33 |           1.6  |              0.33 |                -1.27 |                            nan |                        nan |               0 |               0 |                   0 |                             0 |                    100 |                          0 |

## 5. Setup-family Audit

| view         | group_col    | group_value    |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:-------------|:-------------|:---------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| SETUP_FAMILY | setup_family | ACTIVE_BURST   |       12 |               12 |                      2.14 |               2.14 |                  2.23 |           0.81 |           0.81 |           1    |              0.37 |                -0.19 |                            nan |                        nan |           22.22 |           11.11 |                   0 |                             0 |                  66.67 |                          0 |
| SETUP_FAMILY | setup_family | DELAYED_EP     |        4 |                4 |                      2.24 |               2.24 |                  2.28 |           5.56 |           5.56 |          -2.88 |              1.04 |                 8.44 |                            nan |                        nan |           66.67 |           33.33 |                   0 |                             0 |                  33.33 |                          0 |
| SETUP_FAMILY | setup_family | EP_ACTIVE      |       11 |               11 |                      1.83 |               1.83 |                  2.05 |           0.33 |           0.33 |           1.29 |              0.36 |                -0.96 |                            nan |                        nan |            0    |            0    |                   0 |                             0 |                 100    |                          0 |
| SETUP_FAMILY | setup_family | MOMENTUM_BURST |        1 |                1 |                    nan    |             nan    |                nan    |         nan    |         nan    |         nan    |            nan    |               nan    |                            nan |                        nan |          nan    |          nan    |                 nan |                           nan |                 nan    |                        nan |
| SETUP_FAMILY | setup_family | SLINGSHOT      |        2 |                2 |                      2.17 |               2.17 |                  2.17 |           0.92 |           0.92 |           1.72 |              0.92 |                -0.8  |                            nan |                        nan |           50    |            0    |                   0 |                             0 |                  50    |                          0 |
| SETUP_FAMILY | setup_family | UNKNOWN        |        1 |                1 |                      3.3  |               3.3  |                nan    |         nan    |         nan    |         nan    |            nan    |               nan    |                            nan |                        nan |          nan    |          nan    |                 nan |                           nan |                 nan    |                        nan |

## 6. Resistance Audit (by nearest_resistance_type)

| view                    | group_col               | group_value   |   n_rows |   n_with_5d_data |   avg_computed_planned_rr |   avg_effective_rr |   avg_actual_entry_rr |   avg_max_r_5d |   avg_mfe_5d_r |   avg_mae_5d_r |   median_max_r_5d |   expectancy_proxy_r |   pct_rr_overstated_resistance |   pct_rr_overstated_200sma |   pct_hit_1r_5d |   pct_hit_2r_5d |   pct_hit_target_5d |   pct_hit_effective_target_5d |   pct_failed_before_1r |   pct_major_rr_degradation |
|:------------------------|:------------------------|:--------------|---------:|-----------------:|--------------------------:|-------------------:|----------------------:|---------------:|---------------:|---------------:|------------------:|---------------------:|-------------------------------:|---------------------------:|----------------:|----------------:|--------------------:|------------------------------:|-----------------------:|---------------------------:|
| NEAREST_RESISTANCE_TYPE | nearest_resistance_type | NONE          |       31 |               31 |                      2.08 |               2.08 |                  2.16 |           1.29 |           1.29 |           0.64 |              0.37 |                 0.65 |                            nan |                        nan |           22.73 |            9.09 |                   0 |                             0 |                  72.73 |                          0 |

## 7. Top Warning Rows (computed_planned_rr ≥ 2.0 but effective or actual < 2.0)

_No rows._

## 8. Missing-field Diagnostics

- skill_pack_candidate_outcomes_source: MISSING — sma_200/close fields will be NaN; 200SMA resistance audit will collapse to NONE.
- v59_target_tag_missing: 4 rows lacked the [V5.9 R:R floor] tag (likely pre-V5.8.9 rows). Target/R:R fields are NaN for these.
- v59_rr_tag_missing: 5 rows lacked a parseable R:R value. Reported as RR_NOT_LOGGED in target_realism_flag where target was parseable.

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
