# Bonde Learning Loop Executive Digest — 2026-05-16

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._

## 1. Operational status
- Master decision-log rows: **1,226**
- Decision-log source files: **15**
- Latest decision-log sources: `daily_decision_log_2026-05-07.csv`, `daily_decision_log_2026-05-09.csv`, `daily_decision_log_2026-05-12.csv`, `daily_decision_log_2026-05-13.csv`, `daily_decision_log_2026-05-15.csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    833 |
| REJECT               |    360 |
| COUNCIL              |     33 |


## 2. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| ACTIVE_BURST   |      340 |              333 | ACTIONABLE_SAMPLE |        96.4706  |            51.5432 |         1.22636   |
| PAUSE          |       98 |               68 | ACTIONABLE_SAMPLE |        88.7755  |            48.4848 |        -0.0454482 |
| EP_ACTIVE      |       59 |               44 | ACTIONABLE_SAMPLE |        89.8305  |            41.4634 |         0.534111  |
| EP9M           |       32 |               32 | ACTIONABLE_SAMPLE |       100       |            75      |         5.81884   |
| DELAYED_EP     |       24 |               16 | BUILDING_SAMPLE   |        87.5     |            50      |        -0.917773  |
| ANTICIPATION   |       11 |               10 | BUILDING_SAMPLE   |       100       |            60      |         0.0242493 |
| EP_SPIKE       |        8 |                8 | LOW_SAMPLE        |       100       |            50      |         2.90928   |
| SLINGSHOT      |       23 |                0 | PARTIAL_OUTCOME   |         8.69565 |           nan      |       nan         |
| PRE_BURST      |        2 |                0 | PARTIAL_OUTCOME   |         0       |           nan      |       nan         |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP9M           | AUDIT_ONLY      | C              | WATCH                |        6 |                6 | LOW_SAMPLE        |            66.6667 |           6.84269 |
| EP9M           | AUDIT_ONLY      | D              | REJECT               |       26 |               26 | ACTIONABLE_SAMPLE |            76.9231 |           5.58257 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       50 |               49 | ACTIONABLE_SAMPLE |            57.1429 |           3.83974 |
| EP_ACTIVE      | WATCH_ONLY      | B              | WATCH                |       16 |                7 | LOW_SAMPLE        |            42.8571 |           3.65683 |
| EP_ACTIVE      | REJECT          | D              | REJECT               |       15 |               12 | BUILDING_SAMPLE   |            33.3333 |           3.48787 |
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       38 |               26 | ACTIONABLE_SAMPLE |            69.2308 |           2.52003 |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |      115 |              113 | ACTIONABLE_SAMPLE |            55.7522 |           1.67148 |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        8 |                7 | LOW_SAMPLE        |            33.3333 |           1.23757 |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |        9 |                6 | LOW_SAMPLE        |            25      |        -7.92781   |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        5 |                5 | LOW_SAMPLE        |             0      |        -7.29049   |
| DELAYED_EP     | WATCH_ONLY      | C              | WATCH                |        6 |                6 | LOW_SAMPLE        |            16.6667 |        -2.88868   |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       53 |               35 | ACTIONABLE_SAMPLE |            30.303  |        -2.23005   |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       63 |               63 | ACTIONABLE_SAMPLE |            36.5079 |        -0.26508   |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        8 |                7 | LOW_SAMPLE        |            71.4286 |        -0.0582839 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        8 |                5 | LOW_SAMPLE        |            25      |         0.210662  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       13 |                6 | LOW_SAMPLE        |            66.6667 |         0.483523  |


## 3. Council resolver status
- Council/disagreement resolver rows: **2**
| outcome_status   |   rows |
|:-----------------|-------:|
| PENDING          |      2 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                       |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:-----------------------------------------------------------------------|
| SPIR     | SLINGSHOT      | DEFER             | PENDING          | PENDING         | PENDING                     | outcomes DataFrame missing required columns: ['ticker', 'signal_date'] |
| WRBY     | DELAYED_EP     | DEFER             | PENDING          | PENDING         | PENDING                     | outcomes DataFrame missing required columns: ['ticker', 'signal_date'] |


## 4. Day-1 shape diagnostics
### Source-capable coverage
| scope          | primary_setup    | field                   |   n_total |   n_populated |   coverage_pct | status   |
|:---------------|:-----------------|:------------------------|----------:|--------------:|---------------:|:---------|
| SOURCE_CAPABLE | (source-capable) | day1_close_pct_in_range |        58 |            58 |            100 | OK       |
| SOURCE_CAPABLE | (source-capable) | day1_move_pct           |        58 |            58 |            100 | OK       |
| SOURCE_CAPABLE | (source-capable) | day1_vol_ratio          |        58 |            58 |            100 | OK       |

### All-row coverage (info only; legacy rows included)
| scope              | primary_setup   | field                   |   n_total |   n_populated |   coverage_pct | status                   |
|:-------------------|:----------------|:------------------------|----------:|--------------:|---------------:|:-------------------------|
| ALL_ROWS_INFO_ONLY | (all)           | day1_close_pct_in_range |      1226 |            58 |            4.7 | INFO_LEGACY_MIXED_SCHEMA |
| ALL_ROWS_INFO_ONLY | (all)           | day1_move_pct           |      1226 |            58 |            4.7 | INFO_LEGACY_MIXED_SCHEMA |
| ALL_ROWS_INFO_ONLY | (all)           | day1_vol_ratio          |      1226 |            58 |            4.7 | INFO_LEGACY_MIXED_SCHEMA |

### Day-1 hypothesis verdicts
| test                    | verdict                      |   n_high |   n_low |
|:------------------------|:-----------------------------|---------:|--------:|
| day1_close_pct_in_range | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |
| day1_move_pct           | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |
| day1_vol_ratio          | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |
| day1_combined           | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |


## 5. SLINGSHOT diagnostics
- SLINGSHOT diagnostic rows: **208**
- R:R ≥ 2: **0 / 208** (non-missing 0)
- resolved outcomes: **0 / 208** (non-missing 208)
### Bucket-performance snapshot
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|
| contraction_quality | 30-40    |       35 |            0 |              nan |        nan |
| contraction_quality | 40-50    |       45 |            0 |              nan |        nan |
| contraction_quality | 50-60    |       51 |            0 |              nan |        nan |
| contraction_quality | <30      |       46 |            0 |              nan |        nan |
| contraction_quality | >=60     |       31 |            0 |              nan |        nan |
| volume_ratio        | 0.8-1.0x |       33 |            0 |              nan |        nan |
| volume_ratio        | 1.0-1.2x |       21 |            0 |              nan |        nan |
| volume_ratio        | <0.8x    |       40 |            0 |              nan |        nan |
| volume_ratio        | >=1.2x   |      114 |            0 |              nan |        nan |
| distance_from_21ema | 3-5%     |       23 |            0 |              nan |        nan |
| distance_from_21ema | 5-8%     |       39 |            0 |              nan |        nan |
| distance_from_21ema | 8-12%    |       41 |            0 |              nan |        nan |
| distance_from_21ema | <=3%     |       51 |            0 |              nan |        nan |
| distance_from_21ema | >12%     |       54 |            0 |              nan |        nan |
| risk_pct            | 3-5%     |       49 |            0 |              nan |        nan |


## 6. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Sugar Babies ticker lookup rows: **399**
### Sugar Baby vs non-Sugar Baby
| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     2027 |                 996 |              1.73976 |               45.0803 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     1817 |                 901 |              1.62072 |               44.7281 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     1181 |                 613 |             -1.18492 |               42.2512 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     1011 |                 533 |             -1.13341 |               41.0882 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Recurrence buckets
| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 0             |     1011 |                 533 |            -1.13341  |               41.0882 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      153 |                  96 |            -0.74999  |               40.625  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      214 |                 106 |             2.33091  |               42.4528 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      333 |                 163 |             0.464646 |               46.6258 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 8+            |     1117 |                 536 |             2.25644  |               45.3358 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Setup-family × Sugar Baby=True
| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     1649 |                 810 |              1.27622 |               43.9506 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      143 |                  78 |              4.7581  |               48.7179 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |       99 |                  52 |              1.89756 |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |       48 |                  28 |              4.84145 |               46.4286 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |       53 |                  20 |              5.8566  |               60      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       11 |                   7 |             -2.43556 |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        2 |                   1 |             -6.39038 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |       21 |                   0 |            nan       |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        1 |                   0 |            nan       |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

- Council context export: `latest_sugar_babies_context.md` + `latest_sugar_babies_ticker_context.csv`.

## 7. Open caveats / next actions
- Day-1 fields are being captured, but verdicts remain insufficient until resolved sample sizes mature.
- SLINGSHOT diagnostics are structurally alive but have no resolved outcomes yet.
- SLINGSHOT R:R values are still missing; use gate-distribution diagnostics only until upstream R:R is available.
- Council rows are found but still pending; no council calibration conclusions yet.

## 8. Evidence discipline
- This digest is monitoring context, not permission to change rules.
- Rule-change evidence should come from weekly cohorts with mature T+5/T+10/T+20 windows and repeated effects across cohorts.
- `final_trade_status` remains the executable decision field; `tier` is dashboard/source context only.
