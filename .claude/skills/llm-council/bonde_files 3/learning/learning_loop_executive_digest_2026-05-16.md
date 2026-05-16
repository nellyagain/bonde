# Bonde Learning Loop Executive Digest — 2026-05-16

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._

## 1. Operational status
- Master decision-log rows: **729**
- Decision-log source files: **7**
- Latest decision-log sources: `daily_decision_log_2026-05-07.csv`, `daily_decision_log_2026-05-09.csv`, `daily_decision_log_2026-05-12.csv`, `daily_decision_log_2026-05-13.csv`, `daily_decision_log_2026-05-15.csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    605 |
| REJECT               |     97 |
| COUNCIL              |     27 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     32 |
| COUNCIL              |      2 |
| REJECT               |      1 |

### Corpus reconciliation
- Candidate decision-log files discovered: **7**
- Included decision-log files: **7**
- Excluded decision-log files: **0** (0 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **753 → 753 → 729**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 2. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Sugar Baby=True candidates show 1.74% avg T+5 versus -1.18% for non-Sugar Baby candidates (evaluated n=996 vs 613). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
2. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
3. Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
4. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
5. Realized P&L attribution is live but sample-immature: 2 closed realized rows and 1 with realized R. Use it as plumbing proof only until n_with_realized_r >= 30; do not use it for calibration yet.
6. Corpus reconciliation is now active: 0 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
7. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 3. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| ACTIVE_BURST   |       95 |               88 | ACTIONABLE_SAMPLE |        93.6842  |            38.8235 |        -0.579655  |
| PAUSE          |       69 |               39 | ACTIONABLE_SAMPLE |        84.058   |            51.3514 |         1.20807   |
| EP_ACTIVE      |       44 |               29 | ACTIONABLE_SAMPLE |        86.3636  |            50      |         0.63775   |
| DELAYED_EP     |       14 |                6 | LOW_SAMPLE        |        78.5714  |            83.3333 |         1.30515   |
| ANTICIPATION   |        7 |                6 | LOW_SAMPLE        |       100       |            50      |        -0.0623917 |
| SLINGSHOT      |       23 |                0 | PARTIAL_OUTCOME   |         8.69565 |           nan      |       nan         |
| PRE_BURST      |        2 |                0 | PARTIAL_OUTCOME   |         0       |           nan      |       nan         |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | WATCH_ONLY      | B              | WATCH                |       14 |                5 | LOW_SAMPLE        |            60      |          7.58384  |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       20 |               19 | BUILDING_SAMPLE   |            52.9412 |          4.91974  |
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       30 |               18 | BUILDING_SAMPLE   |            66.6667 |          2.77643  |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       12 |               12 | BUILDING_SAMPLE   |            66.6667 |          1.23244  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       12 |                5 | LOW_SAMPLE        |            80      |          0.876524 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        8 |                5 | LOW_SAMPLE        |            25      |          0.210662 |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       38 |               20 | ACTIONABLE_SAMPLE |            33.3333 |         -0.301985 |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       39 |               37 | ACTIONABLE_SAMPLE |            37.8378 |         -1.08773  |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |        9 |                6 | LOW_SAMPLE        |            25      |         -7.92781  |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        5 |                5 | LOW_SAMPLE        |             0      |         -7.29049  |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       26 |               26 | ACTIONABLE_SAMPLE |            30.7692 |         -4.09441  |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       39 |               37 | ACTIONABLE_SAMPLE |            37.8378 |         -1.08773  |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       38 |               20 | ACTIONABLE_SAMPLE |            33.3333 |         -0.301985 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        8 |                5 | LOW_SAMPLE        |            25      |          0.210662 |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       12 |                5 | LOW_SAMPLE        |            80      |          0.876524 |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       12 |               12 | BUILDING_SAMPLE   |            66.6667 |          1.23244  |


## 4. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        2 |
| ALL_ROWS       | A2             | COUNCIL              | EP_ACTIVE      |        5 |
| POST_V5_9_19   | A1/A2          | NONE                 | ALL            |        0 |
| LATEST_SESSION | A1/A2          | NONE                 | ALL            |        0 |

### Current interpretation
- A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
- Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
- All visible A2 rows route to COUNCIL. Treat A2 performance as marginal-A2 performance, not clean executable-A2 performance.
### A1/A2 forward-return slices
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d   |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:----------------|-------------------:|------------------:|
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        5 |                5 | LOW_SAMPLE      |                  0 |          -7.29049 |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        2 |                1 | LOW_SAMPLE      |                100 |          12.9519  |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- If A1 remains absent post-V5.9.19, test whether criteria are intentionally rare or unreachable.

## 5. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **143**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 6. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   |   higher_n_eval |   higher_avg_5d |   higher_wr_5d | lower_label   |   lower_n_eval |   lower_avg_5d |   lower_wr_5d |   avg_gap_lower_minus_higher |
|:---------------|:---------------|----------------:|----------------:|---------------:|:--------------|---------------:|---------------:|--------------:|-----------------------------:|
| PAUSE          | B              |              20 |       -0.301985 |        33.3333 | C             |             18 |        2.77643 |       66.6667 |                      3.07841 |
| ACTIVE_BURST   | C              |              26 |       -4.09441  |        30.7692 | D             |             37 |       -1.08773 |       37.8378 |                      3.00668 |

Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 7. Hypothesis tracker / shadow validation
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family       | current_test                                             |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------|:---------------------------------------------------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5 |            37 |        -1.08773 |            26 |       -4.09441  |               3.00668 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE    | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5    |            11 |        -7.63812 |           nan |      nan        |              -7.63812 | 2026-05-16       |         0 |       nan |               nan | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE        | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                |            18 |         2.77643 |            20 |       -0.301985 |               3.07841 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **1** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.

## 8. ACTIVE_BURST Gate-6 Observational Watchlist
Rows in this section remain `REJECT` in the decision log. This is an observational research/watchlist section only; it does not alter `final_trade_status`, action labels, ranking, R:R, or hard-reject behavior.
- Full shadow candidates: **1**
- Tradeability-review watchlist rows: **0**
- Context-only rows excluded for missing trigger/invalidation: **1**
- Output file: `active_burst_gate6_observational_watchlist_latest.md`
- Source shadow CSV: `active_burst_gate6_shadow_candidates_v41328.csv`
- Required manual check: only consider these for live attention if they have a defensible trigger, invalidation, R:R, liquidity, DTE safety, and no hard reject.
_No tradeability-review rows found. Shadow candidates exist, but they are context-only because trigger and/or invalidation is missing._

## 9. Council resolver status
- Council/disagreement resolver rows: **2**
| outcome_status   |   rows |
|:-----------------|-------:|
| PENDING          |      2 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                  |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:------------------------------------------------------------------|
| SPIR     | SLINGSHOT      | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| WRBY     | DELAYED_EP     | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |


## 10. Day-1 shape diagnostics
### Source-capable coverage
| scope          | primary_setup    | field                   |   n_total |   n_populated |   coverage_pct | status   |
|:---------------|:-----------------|:------------------------|----------:|--------------:|---------------:|:---------|
| SOURCE_CAPABLE | (source-capable) | day1_close_pct_in_range |        58 |            58 |            100 | OK       |
| SOURCE_CAPABLE | (source-capable) | day1_move_pct           |        58 |            58 |            100 | OK       |
| SOURCE_CAPABLE | (source-capable) | day1_vol_ratio          |        58 |            58 |            100 | OK       |

### All-row coverage (info only; legacy rows included)
| scope              | primary_setup   | field                   |   n_total |   n_populated |   coverage_pct | status                   |
|:-------------------|:----------------|:------------------------|----------:|--------------:|---------------:|:-------------------------|
| ALL_ROWS_INFO_ONLY | (all)           | day1_close_pct_in_range |       729 |            58 |              8 | INFO_LEGACY_MIXED_SCHEMA |
| ALL_ROWS_INFO_ONLY | (all)           | day1_move_pct           |       729 |            58 |              8 | INFO_LEGACY_MIXED_SCHEMA |
| ALL_ROWS_INFO_ONLY | (all)           | day1_vol_ratio          |       729 |            58 |              8 | INFO_LEGACY_MIXED_SCHEMA |

### Day-1 hypothesis verdicts
| test                    | verdict                      |   n_high |   n_low |
|:------------------------|:-----------------------------|---------:|--------:|
| day1_close_pct_in_range | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |
| day1_move_pct           | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |
| day1_vol_ratio          | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |
| day1_combined           | INSUFFICIENT_RESOLVED_SAMPLE |        0 |       0 |


## 11. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. This is a measurement section, not SLINGSHOT rule-change evidence.
- SLINGSHOT evaluability rows: **231**
- Rows with entry/trigger: **47 / 231**
- Rows with stop/invalidation: **47 / 231**
- Rows with target: **26 / 231**
- Rows with planned R:R: **26 / 231**
- Rows with price/outcome data: **51 / 231**
- Rows with ≥5 future bars: **0 / 231**
- Rows triggered within 5d: **0 / 231**
- Rows stopped within 5d: **0 / 231**
- OK-evaluable rows: **0 / 231**
### Top missing/evaluability reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_ENTRY            |    184 |
| INSUFFICIENT_FUTURE_BARS |     24 |
| MISSING_TARGET           |     21 |
| NO_PRICE_DATA            |      2 |

- Audit files: `slingshot_evaluability_audit_latest.md` and `slingshot_evaluability_audit_latest.csv`.
- Interpretation: missing R:R is now treated as a field/evaluability issue, not as zero R:R or negative SLINGSHOT expectancy.
### Bucket-distribution snapshot
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


## 12. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Current read: Sugar Baby=True candidates show 1.74% avg T+5 versus -1.18% for non-Sugar Baby candidates (evaluated n=996 vs 613).
- Interpretation: Sugar Babies currently has broader sample support than EP9M for a future `ranking_context_score` contribution, but still needs out-of-sample / mature-week validation before any non-zero boost.
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

## 13. Realized P&L attribution
- Status: **available but sample-immature**. This is trading-layer attribution, not just signal-date forward return.
- Maturity: **2** closed realized rows; **1** with realized R. Calibration threshold: **30+ realized-R rows**.
### Overall realized P&L / R
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| OVERALL      | ALL           |        2 |               2 |                   1 |            2.02265 |          2.02265 |             2.02265 |           50 |       2.02265 |              0 |               nan |     237.919 |   118.959 |

### By setup_family
| slice_name   | slice_value   |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:-------------|:--------------|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| setup_family | EP_ACTIVE     |        1 |                   1 |            2.02265 |          2.02265 |          100 |               nan |    218.446  |
| setup_family | nan           |        1 |                   0 |          nan       |        nan       |          nan |               nan |     19.4723 |

### By action_label
| slice_name   | slice_value   |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:-------------|:--------------|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| action_label | B             |        1 |                   1 |            2.02265 |          2.02265 |          100 |               nan |    218.446  |
| action_label | nan           |        1 |                   0 |          nan       |        nan       |          nan |               nan |     19.4723 |

### By final_trade_status
| slice_name         | slice_value   |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:-------------------|:--------------|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| final_trade_status | WATCH         |        1 |                   1 |            2.02265 |          2.02265 |          100 |               nan |    218.446  |
| final_trade_status | nan           |        1 |                   0 |          nan       |        nan       |          nan |               nan |     19.4723 |

### By council_verdict
| slice_name      |   slice_value |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:----------------|--------------:|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| council_verdict |           nan |        2 |                   1 |            2.02265 |          2.02265 |           50 |               nan |     237.919 |

### By sugar_baby_flag
| slice_name      |   slice_value |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:----------------|--------------:|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| sugar_baby_flag |           nan |        2 |                   1 |            2.02265 |          2.02265 |           50 |               nan |     237.919 |

### By ep9m_context_type
| slice_name        |   slice_value |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:------------------|--------------:|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| ep9m_context_type |           nan |        2 |                   1 |            2.02265 |          2.02265 |           50 |               nan |     237.919 |

- Interpretation: realized R should be used to validate whether Layer 5 execution is selecting the right subset from WATCH/COUNCIL candidates.

## 14. Investigation queue
| priority   | item                                         | why                                                                                                                                                                                                                         |
|:-----------|:---------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1         | Realized-P&L correlation check               | Once n_with_realized_r >= 30, compare realized R by setup_family/action_label/final_trade_status against learning-loop forward-return expectancy. This is the key bridge between signal quality and actual trading quality. |
| P1         | A1/A2 executable-signal health check         | Confirm A1 count, A2 routing, and whether zero clean TRADE rows is intended strictness or over-routing.                                                                                                                     |
| P1         | Confirm zero-TRADE root cause                | Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.                                                                                             |
| P1         | Investigate reject/watch and B/C/D inversion | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.                                                                                |
| P1         | Track pre-registered rule-change hypotheses  | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, and H_PAUSE_BC_INVERT daily with OOS and realized-R gates before any V5.9.21 rule patch.                                                                  |
| P2         | Sugar Babies validation                      | Candidate for first ranking_context_score contribution, but validate out-of-sample and by setup family before non-zero boost.                                                                                               |
| P1         | Fix SLINGSHOT evaluability path              | SLINGSHOT detection is alive but zero rows are OK-evaluable. Use `slingshot_evaluability_audit_latest.md` to fix missing entry/stop/target/R:R/outcome fields before drawing setup conclusions.                             |


## 15. Open caveats / next actions
- Day-1 fields are being captured, but verdicts remain insufficient until resolved sample sizes mature.
- SLINGSHOT is detected but has zero OK-evaluable rows; use the evaluability audit to fix missing entry/stop/target/R:R/outcome data before judging expectancy.
- Council rows are found but still pending; no council calibration conclusions yet.

## 16. Evidence discipline
- This digest is monitoring context, not permission to change rules.
- Rule-change evidence should come from weekly cohorts with mature T+5/T+10/T+20 windows and repeated effects across cohorts.
- `final_trade_status` remains the executable decision field; `tier` is dashboard/source context only.
- EP9M and Sugar Babies may inform review priority only after validated; neither can override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering, or bad data.
