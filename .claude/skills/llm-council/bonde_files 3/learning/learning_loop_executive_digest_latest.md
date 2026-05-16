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

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     32 |
| COUNCIL              |      2 |
| REJECT               |      1 |


## 2. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. EP9M is the headline research lead: n=32, T+5 win rate 75.00%, avg T+5 5.82%. Treat as context/observability only; do not ship an EP9M boost yet.
2. Sugar Baby=True candidates show 1.74% avg T+5 versus -1.18% for non-Sugar Baby candidates (evaluated n=995 vs 613). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
3. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
4. Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
5. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
6. Council resolver outcome-join still needs attention; council rows are found, but calibration is blocked until the outcome join is clean.
7. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 3. Key findings from current data
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


## 4. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        8 |
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
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        8 |                7 | LOW_SAMPLE      |            33.3333 |           1.23757 |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        5 |                5 | LOW_SAMPLE      |             0      |          -7.29049 |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- If A1 remains absent post-V5.9.19, test whether criteria are intentionally rare or unreachable.

## 5. EP9M overlay
Current read: **promising context overlay, not a trade signal.**
- EP9M rows: **32**
- T+5 evaluable rows: **32**
- T+5 win rate: **75.00%**
- Avg T+5 triggered return: **5.82%**
- Interpretation: EP9M is detecting strong continuation/attention, but the current evidence is raw `setup_family=EP9M`, not the V5.9.20 cohort test of `EP9M_PLUS_REAL_SETUP` versus unstacked peers.
- Guardrail: do **not** promote EP9M-only rows. EP9M still needs a real setup, valid trigger, stop, R:R, and no hard reject.
- V5.9.20 status: identify and measure EP9M now; keep `ep9m_priority_boost=0` and `ranking_context_score=0` until tagged cohorts mature.
### EP9M action-label breakdown
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP9M           | AUDIT_ONLY      | D              | REJECT               |       26 |               26 | ACTIONABLE_SAMPLE |            76.9231 |           5.58257 |
| EP9M           | AUDIT_ONLY      | C              | WATCH                |        6 |                6 | LOW_SAMPLE        |            66.6667 |           6.84269 |

### EP9M caveats
- Momentum-continuation artifact risk is high; EP9M fires near significant price/volume events.
- Current n is near the lower evidence boundary, not comfortably mature.
- EP9M-only rows may lack executable entry/stop/R:R, so they are not comparable to A2 rows.
- Formal verdict requires V5.9.20 fields populated for several weeks and a matched-family comparison.

## 6. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   |   higher_n_eval |   higher_avg_5d |   higher_wr_5d | lower_label   |   lower_n_eval |   lower_avg_5d |   lower_wr_5d |   avg_gap_lower_minus_higher |
|:---------------|:---------------|----------------:|----------------:|---------------:|:--------------|---------------:|---------------:|--------------:|-----------------------------:|
| PAUSE          | B              |              35 |       -2.23005  |        30.303  | C             |             26 |        2.52003 |       69.2308 |                      4.75008 |
| ACTIVE_BURST   | C              |             159 |        0.244815 |        48.4277 | D             |            113 |        1.67148 |       55.7522 |                      1.42666 |

Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 7. Hypothesis tracker / shadow validation
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family       | current_test                                             |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------|:---------------------------------------------------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5 |           113 |         1.67148 |           159 |        0.244815 |               1.42666 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE    | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5    |            11 |        -7.63812 |           nan |      nan        |              -7.63812 | 2026-05-16       |         0 |       nan |               nan | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE        | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                |            26 |         2.52003 |            35 |       -2.23005  |               4.75008 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **2** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.

## 8. ACTIVE_BURST Gate-6 Observational Watchlist
Rows in this section remain `REJECT` in the decision log. This is an observational research/watchlist section only; it does not alter `final_trade_status`, action labels, ranking, R:R, or hard-reject behavior.
- Observational watchlist rows: **2**
- Output file: `active_burst_gate6_observational_watchlist_latest.md`
- Source shadow CSV: `active_burst_gate6_shadow_candidates_v41328.csv`
- Required manual check: only consider these for live attention if they have a defensible trigger, invalidation, R:R, liquidity, DTE safety, and no hard reject.
| signal_date   | date       | ticker   | setup_family   | primary_setup   | action_label   | final_trade_status   |   trigger_price |   invalidation_price |   ret_5d_close_pct |
|:--------------|:-----------|:---------|:---------------|:----------------|:---------------|:---------------------|----------------:|---------------------:|-------------------:|
| 2026-04-27    | 2026-04-27 | PENG     | ACTIVE_BURST   | lowfloat        | D              | REJECT               |             nan |                  nan |           11.5318  |
| 2026-04-28    | 2026-04-28 | LSCC     | ACTIVE_BURST   | Momentum_Burst  | D              | REJECT               |             nan |                  nan |            7.33912 |


## 9. Council resolver status
- Council/disagreement resolver rows: **2**
| outcome_status   |   rows |
|:-----------------|-------:|
| PENDING          |      2 |

**Known issue:** resolver found council rows but outcome calibration is blocked by an outcome-join/schema warning. Fix notebook plumbing before drawing council calibration conclusions.
| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                       |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:-----------------------------------------------------------------------|
| SPIR     | SLINGSHOT      | DEFER             | PENDING          | PENDING         | PENDING                     | outcomes DataFrame missing required columns: ['ticker', 'signal_date'] |
| WRBY     | DELAYED_EP     | DEFER             | PENDING          | PENDING         | PENDING                     | outcomes DataFrame missing required columns: ['ticker', 'signal_date'] |


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


## 11. SLINGSHOT diagnostics
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


## 12. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Current read: Sugar Baby=True candidates show 1.74% avg T+5 versus -1.18% for non-Sugar Baby candidates (evaluated n=995 vs 613).
- Interpretation: Sugar Babies currently has broader sample support than EP9M for a future `ranking_context_score` contribution, but still needs out-of-sample / mature-week validation before any non-zero boost.
- Sugar Babies ticker lookup rows: **399**
### Sugar Baby vs non-Sugar Baby
| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     2027 |                 995 |              1.7415  |               45.1256 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     1817 |                 900 |              1.62252 |               44.7778 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     1181 |                 613 |             -1.18492 |               42.2512 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     1011 |                 533 |             -1.13341 |               41.0882 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Recurrence buckets
| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 0             |     1011 |                 533 |            -1.13341  |               41.0882 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      153 |                  96 |            -0.74999  |               40.625  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      214 |                 105 |             2.35311  |               42.8571 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      333 |                 163 |             0.464646 |               46.6258 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 8+            |     1117 |                 536 |             2.25644  |               45.3358 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Setup-family × Sugar Baby=True
| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     1649 |                 810 |              1.27622 |               43.9506 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      143 |                  78 |              4.7581  |               48.7179 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |       99 |                  52 |              1.89756 |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |       48 |                  28 |              4.84145 |               46.4286 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |       53 |                  19 |              6.16485 |               63.1579 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       11 |                   7 |             -2.43556 |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        2 |                   1 |             -6.39038 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |       21 |                   0 |            nan       |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        1 |                   0 |            nan       |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

- Council context export: `latest_sugar_babies_context.md` + `latest_sugar_babies_ticker_context.csv`.

## 13. Realized P&L attribution
- Status: **wired but no realized trade data ingested yet**.
- Drop a raw IBKR/broker CSV into `bonde_learning/_inbox/` using a name like `ibkr_trades_YYYY-MM-DD.csv`, `broker_trades_YYYY-MM-DD.csv`, or `executions_YYYY-MM-DD.csv`. The notebook will infer signal date, join system context, and compute realized R where stop/risk is available. No manual R sheet is required.
- This is the next major validation step if the system is already making money: connect signal quality to actual realized R/P&L.

## 14. Investigation queue
| priority   | item                                         | why                                                                                                                                                        |
|:-----------|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| P0         | Add realized-P&L attribution file            | Upload `realized_trades_YYYY-MM-DD.csv` to `_inbox/` so the loop can validate actual realized R against signal/council/context slices.                     |
| P0         | Fix council resolver outcome join            | Council rows are found, but calibration is blocked by missing/invalid outcome join columns.                                                                |
| P1         | A1/A2 executable-signal health check         | Confirm A1 count, A2 routing, and whether zero clean TRADE rows is intended strictness or over-routing.                                                    |
| P1         | Confirm zero-TRADE root cause                | Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.                            |
| P1         | Investigate reject/watch and B/C/D inversion | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.               |
| P1         | Track pre-registered rule-change hypotheses  | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, and H_PAUSE_BC_INVERT daily with OOS and realized-R gates before any V5.9.21 rule patch. |
| P2         | EP9M formal cohort test                      | Do not ship an EP9M boost yet. Wait for V5.9.20 EP9M_ONLY vs EP9M_PLUS_REAL_SETUP tagged cohorts and matched-family comparison.                            |
| P2         | Sugar Babies validation                      | Candidate for first ranking_context_score contribution, but validate out-of-sample and by setup family before non-zero boost.                              |
| P2         | Add SLINGSHOT R:R values                     | SLINGSHOT diagnostics are alive but cannot test R:R until upstream R:R fields are available.                                                               |


## 15. Open caveats / next actions
- Day-1 fields are being captured, but verdicts remain insufficient until resolved sample sizes mature.
- SLINGSHOT diagnostics are structurally alive but have no resolved outcomes yet.
- SLINGSHOT R:R values are still missing; use gate-distribution diagnostics only until upstream R:R is available.
- Council rows are found but still pending; no council calibration conclusions yet.
- Council resolver outcome join warning remains; fix before using council calibration.

## 16. Evidence discipline
- This digest is monitoring context, not permission to change rules.
- Rule-change evidence should come from weekly cohorts with mature T+5/T+10/T+20 windows and repeated effects across cohorts.
- `final_trade_status` remains the executable decision field; `tier` is dashboard/source context only.
- EP9M and Sugar Babies may inform review priority only after validated; neither can override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering, or bad data.
