# Bonde Learning Report — 2026-05-17

_v4.10 daily report. For evidence-grade rule-change conversations, use the weekly cohort report instead._

## Scope

- Rows in master decision log: 35
- Rows with evaluated / partial outcomes: 0
- Rows pending future bars or missing data: 35

## Reading this report

- Every metric has two views: `_all` (every row) and `_trig` (rows where the entry trigger fired or no trigger price was set).
- `confidence_5d` flags whether a row is evidence (`ACTIONABLE_SAMPLE` ≥ 20 evaluable, `BUILDING_SAMPLE` 10–19, `LOW_SAMPLE` < 10, `PARTIAL_OUTCOME` 0). Do not act on `LOW_SAMPLE` or `PARTIAL_OUTCOME` rows.
- `confidence_20d` flags whether the longer-window data is mature (≥ 30 evaluable rows at T+20).
- Rule-change discussions belong in the weekly cohort report, not here.
- `final_trade_status` is the executable decision field. `tier` is a source/dashboard focus tier and must not be read as trade permission.

## Watch Items

- No watch items met the threshold this run.

## Setup-Family Summary

_Whitelisted setup families only. Workflow/source classifications (EXCLUSION, DIAGNOSTIC, etc.) are in the source-bucket section below._

| setup_family   |   n_rows |   n_evaluable_5d |   n_evaluable_20d | confidence_5d   | confidence_20d   |   pct_triggered |   win_rate_5d_all |   win_rate_5d_trig |   avg_ret_5d_all |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|------------------:|:----------------|:-----------------|----------------:|------------------:|-------------------:|-----------------:|------------------:|
| SLINGSHOT      |       23 |                0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |            8.7  |               nan |                nan |              nan |               nan |
| PAUSE          |        9 |                0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |           22.22 |               nan |                nan |              nan |               nan |
| DELAYED_EP     |        2 |                0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |            0    |               nan |                nan |              nan |               nan |
| EP_ACTIVE      |        1 |                0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |          100    |               nan |                nan |              nan |               nan |

## Source-Bucket Summary

_For audit only. These are not setup families and should not be used to evaluate setup performance._

_No rows._

## Actionability Summary

| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d   |   pct_triggered |   win_rate_5d_all |   win_rate_5d_trig |   avg_ret_5d_all |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:----------------|----------------:|------------------:|-------------------:|-----------------:|------------------:|
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |       20 |                0 | PARTIAL_OUTCOME |              10 |               nan |                nan |              nan |               nan |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |        7 |                0 | PARTIAL_OUTCOME |               0 |               nan |                nan |              nan |               nan |
| PAUSE          | WATCH_ONLY      | C              | WATCH                |        2 |                0 | PARTIAL_OUTCOME |             100 |               nan |                nan |              nan |               nan |
| SLINGSHOT      | WATCH_ONLY      | B              | WATCH                |        2 |                0 | PARTIAL_OUTCOME |               0 |               nan |                nan |              nan |               nan |
| EP_ACTIVE      | REJECT          | D              | REJECT               |        1 |                0 | PARTIAL_OUTCOME |             100 |               nan |                nan |              nan |               nan |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |        1 |                0 | PARTIAL_OUTCOME |               0 |               nan |                nan |              nan |               nan |
| DELAYED_EP     | UNKNOWN         | B+_C1          | COUNCIL              |        1 |                0 | PARTIAL_OUTCOME |               0 |               nan |                nan |              nan |               nan |
| SLINGSHOT      | UNKNOWN         | B+_C1          | COUNCIL              |        1 |                0 | PARTIAL_OUTCOME |               0 |               nan |                nan |              nan |               nan |

## Catalyst × Setup-Family Summary

_Stratifies catalyst grade by setup family to prevent Simpson's-paradox readings (e.g., Grade C appearing better than Grade A only because Grade C names happen to be in stronger families)._

| setup_family   | catalyst_grade   |   n_rows |   n_evaluable_5d | confidence_5d   |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:-----------------|---------:|-----------------:|:----------------|----------------:|-------------------:|------------------:|
| SLINGSHOT      | UNKNOWN          |       22 |                0 | PARTIAL_OUTCOME |            9.09 |                nan |               nan |
| PAUSE          | UNKNOWN          |        9 |                0 | PARTIAL_OUTCOME |           22.22 |                nan |               nan |
| DELAYED_EP     | B                |        1 |                0 | PARTIAL_OUTCOME |            0    |                nan |               nan |
| DELAYED_EP     | A                |        1 |                0 | PARTIAL_OUTCOME |            0    |                nan |               nan |
| EP_ACTIVE      | UNKNOWN          |        1 |                0 | PARTIAL_OUTCOME |          100    |                nan |               nan |
| SLINGSHOT      | B                |        1 |                0 | PARTIAL_OUTCOME |            0    |                nan |               nan |

## Pre-Burst Conversion Summary

_No rows._

## Reject Audit Summary

| setup_family   | catalyst_type                 | summary_type   |   n_rows |   n_evaluable_1d |   n_evaluable_3d |   n_evaluable_5d |   n_evaluable_10d |   n_evaluable_20d | confidence_5d   | confidence_20d   |   n_triggered |   n_no_trigger_set |   pct_triggered |   avg_ret_1d_all |   median_ret_1d_all |   win_rate_1d_all |   avg_ret_1d_trig |   median_ret_1d_trig |   win_rate_1d_trig |   avg_ret_3d_all |   median_ret_3d_all |   win_rate_3d_all |   avg_ret_3d_trig |   median_ret_3d_trig |   win_rate_3d_trig |   avg_ret_5d_all |   median_ret_5d_all |   win_rate_5d_all |   avg_ret_5d_trig |   median_ret_5d_trig |   win_rate_5d_trig |   avg_ret_10d_all |   median_ret_10d_all |   win_rate_10d_all |   avg_ret_10d_trig |   median_ret_10d_trig |   win_rate_10d_trig |   avg_ret_20d_all |   median_ret_20d_all |   win_rate_20d_all |   avg_ret_20d_trig |   median_ret_20d_trig |   win_rate_20d_trig |   trigger_hit_5d_pct |   pre_burst_triggered_5d_pct |
|:---------------|:------------------------------|:---------------|---------:|-----------------:|-----------------:|-----------------:|------------------:|------------------:|:----------------|:-----------------|--------------:|-------------------:|----------------:|-----------------:|--------------------:|------------------:|------------------:|---------------------:|-------------------:|-----------------:|--------------------:|------------------:|------------------:|---------------------:|-------------------:|-----------------:|--------------------:|------------------:|------------------:|---------------------:|-------------------:|------------------:|---------------------:|-------------------:|-------------------:|----------------------:|--------------------:|------------------:|---------------------:|-------------------:|-------------------:|----------------------:|--------------------:|---------------------:|-----------------------------:|
| EP_ACTIVE      | Unknown / Recent gap-and-fade | rejects        |        1 |                0 |                0 |                0 |                 0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |             1 |                  1 |             100 |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |                  nan |                          nan |

## Catalyst Summary (un-stratified)

_Kept for backward compatibility. The catalyst × setup-family table above is the right view for decision-making._

| catalyst_grade   | summary_type   |   n_rows |   n_evaluable_1d |   n_evaluable_3d |   n_evaluable_5d |   n_evaluable_10d |   n_evaluable_20d | confidence_5d   | confidence_20d   |   n_triggered |   n_no_trigger_set |   pct_triggered |   avg_ret_1d_all |   median_ret_1d_all |   win_rate_1d_all |   avg_ret_1d_trig |   median_ret_1d_trig |   win_rate_1d_trig |   avg_ret_3d_all |   median_ret_3d_all |   win_rate_3d_all |   avg_ret_3d_trig |   median_ret_3d_trig |   win_rate_3d_trig |   avg_ret_5d_all |   median_ret_5d_all |   win_rate_5d_all |   avg_ret_5d_trig |   median_ret_5d_trig |   win_rate_5d_trig |   avg_ret_10d_all |   median_ret_10d_all |   win_rate_10d_all |   avg_ret_10d_trig |   median_ret_10d_trig |   win_rate_10d_trig |   avg_ret_20d_all |   median_ret_20d_all |   win_rate_20d_all |   avg_ret_20d_trig |   median_ret_20d_trig |   win_rate_20d_trig |   trigger_hit_5d_pct |   pre_burst_triggered_5d_pct |
|:-----------------|:---------------|---------:|-----------------:|-----------------:|-----------------:|------------------:|------------------:|:----------------|:-----------------|--------------:|-------------------:|----------------:|-----------------:|--------------------:|------------------:|------------------:|---------------------:|-------------------:|-----------------:|--------------------:|------------------:|------------------:|---------------------:|-------------------:|-----------------:|--------------------:|------------------:|------------------:|---------------------:|-------------------:|------------------:|---------------------:|-------------------:|-------------------:|----------------------:|--------------------:|------------------:|---------------------:|-------------------:|-------------------:|----------------------:|--------------------:|---------------------:|-----------------------------:|
| UNKNOWN          | catalyst_grade |       32 |                0 |                0 |                0 |                 0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |             5 |                  5 |           15.62 |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |                  nan |                          nan |
| B                | catalyst_grade |        2 |                0 |                0 |                0 |                 0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |             0 |                  0 |            0    |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |                  nan |                          nan |
| A                | catalyst_grade |        1 |                0 |                0 |                0 |                 0 |                 0 | PARTIAL_OUTCOME | IMMATURE_20D     |             0 |                  0 |            0    |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |              nan |                 nan |               nan |               nan |                  nan |                nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |               nan |                  nan |                nan |                nan |                   nan |                 nan |                  nan |                          nan |

## Notes

- Pre-burst rows are evaluated by trigger conversion, not day-zero P&L.
- Active-burst rows are evaluated over T+1/T+3/T+5; KK extension/monster rows over T+10/T+20 once mature.
- Win rate uses dropna() — pending rows do not count as losses (this is a v4.10 bug fix; prior versions understated win rate).
- Do not change rules from one day of data. Evidence for rule changes lives in the weekly cohort report.

## Section 5 — V5.9.9 Day-1 Shape Hypothesis Verdicts (v4.13.8)

Four-test hypothesis evaluation framework. Tests refuse to produce a verdict below 30 resolved Day-1-relevant trades (single-field tests) or 30 rows in either COMBINED_HIGH/LOW bucket (combination test). No trading-rule changes; this is monitoring only.

| Test | Verdict | n_high | n_low | exp_high_R | exp_low_R | gap_R | coverage |
|---|---|---|---|---|---|---|---|
| day1_close_pct_in_range | INSUFFICIENT_RESOLVED_SAMPLE | 0 | 0 | n/a | n/a | n/a | n/a |
| day1_move_pct | INSUFFICIENT_RESOLVED_SAMPLE | 0 | 0 | n/a | n/a | n/a | n/a |
| day1_vol_ratio | INSUFFICIENT_RESOLVED_SAMPLE | 0 | 0 | n/a | n/a | n/a | n/a |
| day1_combined | INSUFFICIENT_RESOLVED_SAMPLE | 0 | 0 | n/a | n/a | n/a | n/a |

## Section 6 — SLINGSHOT Gate Diagnostics (v4.13.14 monitoring only)

Monitoring-only diagnostic. No SLINGSHOT gate or tier logic changed.

- Source frame: `decision_outcomes`
- SLINGSHOT rows: 23
- Active family rows: 23
- Precedence-absorbed rows: 0
- Row diagnostics CSV: `slingshot_diagnostics_rows_v41314.csv`
- Bucket summary CSV: `slingshot_bucket_performance_v41314.csv`
- Standalone report: `slingshot_diagnostics_report_v41314.md`

| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|
| contraction_quality | MISSING  |       23 |            0 |              nan |        nan |
| volume_ratio        | MISSING  |       23 |            0 |              nan |        nan |
| distance_from_21ema | MISSING  |       23 |            0 |              nan |        nan |
| risk_pct            | MISSING  |       23 |            0 |              nan |        nan |
| range_break         | MISSING  |       23 |            0 |              nan |        nan |
| custom_rs_rating    | MISSING  |       23 |            0 |              nan |        nan |
| rr_pass             | MISSING  |       23 |            0 |              nan |        nan |
| vol_gate            | MISSING  |       23 |            0 |              nan |        nan |
| contraction_gate    | MISSING  |       23 |            0 |              nan |        nan |
