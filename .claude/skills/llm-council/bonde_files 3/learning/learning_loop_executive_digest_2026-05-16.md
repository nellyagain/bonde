# Bonde Learning Loop Executive Digest — 2026-05-16

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._

## 1. Today's required action
1. **No rule changes.** (§9 hypothesis tracker / verdict gates — all monitoring-only, no SUPPORTED verdicts)
2. **Wait for SLINGSHOT future bars.** Earliest T+5 maturity: **2026-05-22**. (§13)
3. **Watch A1/A2 zero-TRADE issue.** Confirm whether A1 is intentionally rare or unreachable and whether clean A1/A2 rows are over-routed. (§6)
4. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
5. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **1**. (§15)

## 2. Changed since last run
### Pipeline changes
- SLINGSHOT decision-log target/R:R backfilled inside the learning loop: **21** rows.
- Tiny-geometry hygiene audit added / active: **4** rows flagged.
- Dedup diagnostics active: **45** raw full-plan+price rows → **21** unique ticker-date rows.
- Backfill source attribution simplified to `slingshot_backfill_source` enum.

### Data changes
- No new hypothesis verdicts crossed a rule-change threshold.
- No Day-1 shape verdicts crossed threshold.
- Realized P&L remains sample-immature: `n_with_realized_r` = **1**.

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.
- SLINGSHOT `OK_EVALUABLE` rows remain 0 until future bars mature.

## 3. Operational status
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

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Sugar Baby=True candidates show 1.74% avg T+5 versus -1.18% for non-Sugar Baby candidates (evaluated n=996 vs 613). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
2. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
3. Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
4. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
5. Realized P&L attribution is live but sample-immature: 2 closed realized rows and 1 with realized R. Use it as plumbing proof only until n_with_realized_r >= 30; do not use it for calibration yet.
6. Corpus reconciliation is now active: 0 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
7. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
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


## 6. A1 / A2 executable-signal health
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

## 7. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **143**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 8. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   |   higher_n_eval |   higher_avg_5d |   higher_wr_5d | lower_label   |   lower_n_eval |   lower_avg_5d |   lower_wr_5d |   avg_gap_lower_minus_higher |
|:---------------|:---------------|----------------:|----------------:|---------------:|:--------------|---------------:|---------------:|--------------:|-----------------------------:|
| PAUSE          | B              |              20 |       -0.301985 |        33.3333 | C             |             18 |        2.77643 |       66.6667 |                      3.07841 |
| ACTIVE_BURST   | C              |              26 |       -4.09441  |        30.7692 | D             |             37 |       -1.08773 |       37.8378 |                      3.00668 |

Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family       | current_test                                             |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------|:---------------------------------------------------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5 |            37 |        -1.08773 |            26 |       -4.09441  |               3.00668 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE    | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5    |            11 |        -7.63812 |           nan |      nan        |              -7.63812 | 2026-05-16       |         0 |       nan |               nan | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE        | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                |            18 |         2.77643 |            20 |       -0.301985 |               3.07841 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **1** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.
### Pre-registered verdict gates
These gates are binding review criteria. A rule patch should not ship unless its hypothesis has a pre-registered SUPPORTED verdict or a separate explicitly documented emergency bug rationale.
| hypothesis_id                  | current_state                                                                                                       | required_sample                                                                                           | oos_window                                      | earliest_review                                         | pre_registered_prediction                                                                                              | supported_if                                                                              | rejected_if                                                                                          | ambiguous_if                                                                                    | if_supported                                                                                                                          | if_rejected                                                           |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------|:------------------------------------------------|:--------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN    | current effect 3.01; n_a=37; n_b=26; status=WATCHING_NOT_RULE_EVIDENCE                                              | OOS n_C >= 30 and n_D >= 30, with mature T+5/T+10/T+20 windows.                                           | 2026-05-16 onward                               | When both OOS slices meet sample and maturity gates.    | D/REJECT minus C/WATCH spread remains >= +1.5% OOS.                                                                    | OOS spread >= +1.5% and confidence interval / robustness check does not collapse to zero. | OOS spread < +0.5% or direction inverts.                                                             | OOS spread is +0.5% to +1.5% or sample composition is unstable.                                 | Draft V5.9.21-G6-SOFTEN spec; do not ship until patch text is reviewed.                                                               | File hypothesis; no Gate6 softening.                                  |
| H_EP_ACTIVE_COUNCIL_TIGHTEN    | current effect -7.64; n_a=11; status=WATCHING_LOW_SAMPLE                                                            | OOS EP_ACTIVE COUNCIL n >= 30 with mature T+5 and at least 10 T+20 rows.                                  | 2026-05-16 onward                               | When OOS council-routed EP_ACTIVE rows reach n>=30.     | EP_ACTIVE COUNCIL average T+5 remains <= -3.0% OOS.                                                                    | OOS avg T+5 <= -3.0% and win rate <= 35% without one-stock distortion.                    | OOS avg T+5 >= 0% or win rate normalizes above 45%.                                                  | OOS avg T+5 is -3.0% to 0% or driven by one outlier.                                            | Draft V5.9.21-EPACTIVE-COUNCIL-TIGHTEN review spec.                                                                                   | Keep EP_ACTIVE council routing unchanged.                             |
| H_PAUSE_BC_INVERT              | current effect 3.08; n_a=18; n_b=20; status=WATCHING_NOT_RULE_EVIDENCE                                              | OOS PAUSE B/WATCH n >= 30 and PAUSE C/WATCH n >= 30.                                                      | 2026-05-16 onward                               | When both OOS PAUSE slices hit n>=30 and T+5 is mature. | PAUSE C/WATCH minus B/WATCH spread remains >= +1.5% OOS.                                                               | OOS spread >= +1.5% and persists after removing tiny/liquidity outliers.                  | OOS spread < +0.5% or B resumes leadership.                                                          | OOS spread is +0.5% to +1.5% or sample is too concentrated.                                     | Draft V5.9.21-PAUSE-RANK-REVIEW spec; do not change B/C labels before review.                                                         | Keep PAUSE B/C rank mapping unchanged.                                |
| H_SLINGSHOT_TARGET_BASIS       | 45 raw full-plan+price rows; 21 unique full-plan+price ticker-date rows; 0 unique OK_EVALUABLE ticker-date rows.    | unique_ok_evaluable_ticker_date_rows >= 30 and at least 10 OOS rows after 2026-05-22.                     | Starts 2026-05-22                               | When unique OK_EVALUABLE ticker-date rows reach n>=30.  | >=40% of SLINGSHOT_PRIMARY full-plan unique ticker-date rows clear V5.9 R:R floor >= 2.0.                              | R:R>=2.0 pass rate >=40% and T+5 expectancy is not worse than ACTIVE_BURST baseline.      | R:R>=2.0 pass rate <30% or T+5 expectancy materially underperforms ACTIVE_BURST.                     | R:R pass rate is 30–40% or expectancy is positive but under-sampled.                            | Keep SLINGSHOT measurement path live; consider later context/ranking overlay only after 100+ unique OK_EVALUABLE rows.                | Do not promote SLINGSHOT; review target-basis and detection criteria. |
| H_SUGAR_BABIES_CONTEXT_OVERLAY | Sugar Baby=True candidates show 1.74% avg T+5 versus -1.18% for non-Sugar Baby candidates (evaluated n=996 vs 613). | OOS >= 100 evaluated Sugar=True and >= 100 Sugar=False rows, plus at least two setup families with n>=30. | Next mature weekly cohorts after current digest | When OOS rows and family spread requirements are met.   | Sugar=True retains >= +1.0% avg T+5 spread over Sugar=False without worsening win-rate materially.                     | OOS avg spread >= +1.0% and at least two families have non-negative confirmation.         | OOS spread < +0.25% or driven by one family only.                                                    | OOS spread +0.25% to +1.0% or family split is mixed.                                            | Draft Sugar Babies ranking_context_score proposal; cannot override R:R, DTE, hard rejects, failed EP, dilution/offering, or bad data. | Keep Sugar Babies as monitoring-only context.                         |
| H_REALIZED_PNL_CORRELATION     | 1 realized-R rows; threshold not met.                                                                               | n_with_realized_r >= 30 total, then >=10 per major setup/action slice before slice-level claims.          | Broker-export rows as they arrive               | When realized-R count reaches n>=30.                    | Layer 5 realized-R selection should outperform raw WATCH/COUNCIL forward-return expectancy on comparable setup slices. | Realized R is positive overall and aligns with the strongest forward-return slices.       | Realized R is negative despite positive forward-return slices, implying execution/selection failure. | Positive P&L but too concentrated in one trade or mismatch between broker rows and system rows. | Use realized-R weighting in weekly system review; do not change signal rules solely from P&L.                                         | Prioritize execution/selection review before signal-rule changes.     |


## 10. ACTIVE_BURST Gate-6 Observational Watchlist
Rows in this section remain `REJECT` in the decision log. This is an observational research/watchlist section only; it does not alter `final_trade_status`, action labels, ranking, R:R, or hard-reject behavior.
- Full shadow candidates: **1**
- Tradeability-review watchlist rows: **0**
- Context-only rows excluded for missing trigger/invalidation: **1**
- Output file: `active_burst_gate6_observational_watchlist_latest.md`
- Source shadow CSV: `active_burst_gate6_shadow_candidates_v41328.csv`
- Required manual check: only consider these for live attention if they have a defensible trigger, invalidation, R:R, liquidity, DTE safety, and no hard reject.
_No tradeability-review rows found. Shadow candidates exist, but they are context-only because trigger and/or invalidation is missing._

## 11. Council resolver status
- Council/disagreement resolver rows: **2**
| outcome_status   |   rows |
|:-----------------|-------:|
| PENDING          |      2 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                  |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:------------------------------------------------------------------|
| SPIR     | SLINGSHOT      | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| WRBY     | DELAYED_EP     | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |


## 12. Day-1 shape diagnostics
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


## 13. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. This is a measurement section, not SLINGSHOT rule-change evidence.
- SLINGSHOT evaluability rows: **231**
- Rows with entry/trigger: **47 / 231**
- Rows with stop/invalidation: **47 / 231**
- Rows with target: **47 / 231**
- Rows with planned R:R: **47 / 231**
- Rows with price/outcome data: **51 / 231**
- Rows with ≥5 future bars: **0 / 231**
- Rows triggered within 5d: **0 / 231**
- Rows stopped within 5d: **0 / 231**
- OK-evaluable rows: **0 / 231**
- DECISION_LOG rows target/R:R enriched inside learning loop from universe planning fields: **21**
### Top missing/evaluability reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_ENTRY            |    184 |
| INSUFFICIENT_FUTURE_BARS |     45 |
| NO_PRICE_DATA            |      2 |

- Audit files: `slingshot_evaluability_audit_latest.md` and `slingshot_evaluability_audit_latest.csv`.
### Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| MISSING_ENTRY                     |    184 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |     45 |
| FULL_PLAN_NO_PRICE_DATA           |      2 |

### Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    144 |           21 |          21 |            21 |                21 |                23 |                     0 |              0 |                                         0 |                                   2 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   2 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |     23 |           21 |          21 |            21 |                21 |                23 |                     0 |              0 |                                        21 |                                   1 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |      7 |            5 |           5 |             5 |                 5 |                 5 |                     0 |              0 |                                         0 |                                   1 |

### Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |    167 |           42 |          42 |            42 |                42 |                46 |                     0 |              0 |                                        21 |                                 2   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2.5 |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |      3 |            3 |           3 |             3 |                 3 |                 2 |                     0 |              0 |                                         0 |                                 1   |
| EP9M           | SLINGSHOT_OVERLAY               |      2 |            1 |           1 |             1 |                 1 |                 2 |                     0 |              0 |                                         0 |                                 1   |
| PAUSE          | SLINGSHOT_OVERLAY               |      2 |            1 |           1 |             1 |                 1 |                 1 |                     0 |              0 |                                         0 |                                 1   |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 3   |

### Signal-date / recency summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     30 |           26 |          26 |            26 |                26 |                28 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-15           | DECISION_LOG            |     23 |           21 |          21 |            21 |                21 |                23 |                     0 |              0 |                                        21 |                                   1 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   2 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   3 |

### Hygiene diagnostics
Measurement-only checks: tiny measured-move geometry, duplicate ticker-date outcomes, and backfill-source attribution. No trading rules changed.
**Hygiene summary**
| metric                                  |   value |
|:----------------------------------------|--------:|
| rows_total                              |     231 |
| full_plan_rows                          |      47 |
| tiny_geometry_flag_rows                 |       4 |
| tiny_stop_pct_rows                      |       4 |
| tiny_stop_abs_rows                      |       3 |
| tiny_target_abs_rows                    |       2 |
| nonpositive_geometry_rows               |       0 |
| raw_full_plan_price_rows                |      45 |
| unique_ticker_date_rows                 |     155 |
| unique_full_plan_price_ticker_date_rows |      21 |
| raw_ok_evaluable_rows                   |       0 |
| unique_ok_evaluable_ticker_date_rows    |       0 |
| duplicate_trade_key_rows                |     139 |

**Backfill source attribution**
| slingshot_backfill_source    |   rows |
|:-----------------------------|-------:|
| NONE                         |    210 |
| DIAGNOSTIC_AND_UNIVERSE_PLAN |     21 |

**Duplicate ticker-date rows (sample)**
| _ss_unique_trade_key   | ticker   | signal_date   | _ss_source_scope     | setup_family   |   planned_rr |   _ss_duplicate_trade_key_count | _ss_recommended_dedup_keep   | slingshot_geometry_tiny_flag   | slingshot_backfill_source    |
|:-----------------------|:---------|:--------------|:---------------------|:---------------|-------------:|--------------------------------:|:-----------------------------|:-------------------------------|:-----------------------------|
| ACLX|2026-05-15        | ACLX     | 2026-05-15    | DECISION_LOG         | SLINGSHOT      |   nan        |                               4 | True                         | False                          | NONE                         |
| ACLX|2026-05-15        | ACLX     | 2026-05-15    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               4 | False                        | False                          | NONE                         |
| ACLX|2026-05-15        | ACLX     | 2026-05-15    | SLINGSHOT_DIAGNOSTIC | EP9M           |   nan        |                               4 | False                        | False                          | NONE                         |
| ACLX|2026-05-15        | ACLX     | 2026-05-15    | SLINGSHOT_DIAGNOSTIC | PAUSE          |   nan        |                               4 | False                        | False                          | NONE                         |
| AMRC|2026-05-14        | AMRC     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | ACTIVE_BURST   |   nan        |                               2 | True                         | False                          | NONE                         |
| AMRC|2026-05-14        | AMRC     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               2 | False                        | False                          | NONE                         |
| ANET|2026-05-14        | ANET     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               2 | True                         | False                          | NONE                         |
| ANET|2026-05-14        | ANET     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | EP9M           |   nan        |                               2 | False                        | False                          | NONE                         |
| AOSL|2026-05-13        | AOSL     | 2026-05-13    | SLINGSHOT_DIAGNOSTIC | ACTIVE_BURST   |   nan        |                               2 | True                         | False                          | NONE                         |
| AOSL|2026-05-13        | AOSL     | 2026-05-13    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               2 | False                        | False                          | NONE                         |
| APA|2026-05-15         | APA      | 2026-05-15    | DECISION_LOG         | SLINGSHOT      |     0.487655 |                               2 | True                         | False                          | DIAGNOSTIC_AND_UNIVERSE_PLAN |
| APA|2026-05-15         | APA      | 2026-05-15    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |     0.481598 |                               2 | False                        | False                          | NONE                         |
| ARCB|2026-05-14        | ARCB     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | ACTIVE_BURST   |   nan        |                               2 | True                         | False                          | NONE                         |
| ARCB|2026-05-14        | ARCB     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               2 | False                        | False                          | NONE                         |
| AVGO|2026-05-14        | AVGO     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               2 | True                         | False                          | NONE                         |
| AVGO|2026-05-14        | AVGO     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | EP9M           |   nan        |                               2 | False                        | False                          | NONE                         |
| AVT|2026-05-13         | AVT      | 2026-05-13    | SLINGSHOT_DIAGNOSTIC | ACTIVE_BURST   |   nan        |                               2 | True                         | False                          | NONE                         |
| AVT|2026-05-13         | AVT      | 2026-05-13    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               2 | False                        | False                          | NONE                         |
| BTDR|2026-05-14        | BTDR     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | ACTIVE_BURST   |   nan        |                               3 | True                         | False                          | NONE                         |
| BTDR|2026-05-14        | BTDR     | 2026-05-14    | SLINGSHOT_DIAGNOSTIC | SLINGSHOT      |   nan        |                               3 | False                        | False                          | NONE                         |

- Hygiene diagnostics: `slingshot_hygiene_diagnostics_latest.md`, `slingshot_hygiene_summary_latest.csv`, `slingshot_dedup_diagnostics_latest.csv`, `slingshot_backfill_attribution_latest.csv`.
- Scope/price diagnostics: `slingshot_scope_price_diagnostics_latest.md` plus `slingshot_evaluability_*_summary_latest.csv` files.
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
| risk_pct            | 3-5%     |        4 |            0 |              nan |        nan |


## 14. Sugar Babies overlay
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

## 15. Realized P&L attribution
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

## 16. Investigation queue
| priority   | item                                                  | why                                                                                                                                                                                                                                                     |
|:-----------|:------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1         | Realized-P&L correlation check                        | Once n_with_realized_r >= 30, compare realized R by setup_family/action_label/final_trade_status against learning-loop forward-return expectancy. This is the key bridge between signal quality and actual trading quality.                             |
| P1         | A1/A2 executable-signal health check                  | Confirm A1 count, A2 routing, and whether zero clean TRADE rows is intended strictness or over-routing.                                                                                                                                                 |
| P1         | Confirm zero-TRADE root cause                         | Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.                                                                                                                         |
| P1         | Investigate reject/watch and B/C/D inversion          | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.                                                                                                            |
| P1         | Track pre-registered rule-change hypotheses           | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, and H_PAUSE_BC_INVERT daily with OOS and realized-R gates before any V5.9.21 rule patch.                                                                                              |
| P2         | Sugar Babies validation                               | Candidate for first ranking_context_score contribution, but validate out-of-sample and by setup family before non-zero boost.                                                                                                                           |
| P1         | Keep SLINGSHOT target/R:R enrichment in learning loop | Learning loop backfilled 21 DECISION_LOG row(s) from diagnostic/skill-pack planning fields. Actionability skill remains stable; continue measurement-layer enrichment from universe outputs until the raw decision-log schema is intentionally revised. |
| P1         | Fix SLINGSHOT evaluability path                       | SLINGSHOT detection is alive but zero rows are OK-evaluable. Use `slingshot_evaluability_audit_latest.md` to fix missing entry/stop/target/R:R/outcome fields before drawing setup conclusions.                                                         |
| P2         | SLINGSHOT hygiene verification                        | Before first OK_EVALUABLE rows mature, review tiny-geometry flags, duplicate ticker-date rows, and backfill-source attribution in `slingshot_hygiene_diagnostics_latest.md`.                                                                            |


## 17. Open caveats / next actions
- Day-1 fields are being captured, but verdicts remain insufficient until resolved sample sizes mature.
- SLINGSHOT is detected but has zero OK-evaluable rows; use the evaluability audit to fix missing entry/stop/target/R:R/outcome data before judging expectancy.
- Council rows are found but still pending; no council calibration conclusions yet.

## 18. Evidence discipline
- This digest is monitoring context, not permission to change rules.
- Rule-change evidence should come from weekly cohorts with mature T+5/T+10/T+20 windows and repeated effects across cohorts.
- `final_trade_status` remains the executable decision field; `tier` is dashboard/source context only.
- EP9M and Sugar Babies may inform review priority only after validated; neither can override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering, or bad data.
