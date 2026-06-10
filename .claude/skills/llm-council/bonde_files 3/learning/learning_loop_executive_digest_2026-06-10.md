# Bonde Learning Loop Executive Digest — 2026-06-10

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-06-10 14:39 UTC_
_Notebook: v4.14.23 — CANONICAL_CORPUS_SOURCE_HEALTH_FIX (corpus-integrity/source-health/provenance; non-trading)_

## 1. Today's required action
1. **No automatic rule changes.** Any READY/SUPPORTED item from the rule-readiness monitor still requires manual review before patching. (§9 hypothesis tracker / verdict gates)
2. **Review first SLINGSHOT OK-evaluable cohort under H_SLINGSHOT_TARGET_BASIS; no rule change yet.** OK_EVALUABLE rows: **675**; rows ≥5 future bars: **1,734**; unique full-plan+price ticker-date rows: **434**. (§13)
3. **A1 remains absent; TRADE path is now alive.** Monitor whether A1 is intentionally rare or unreachable. Post-V5.9.19 TRADE rows: **10**; A1 rows: **0**; A2 rows: **16**. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is alive, low sample (n=107), measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **1**. (§15)
7. **Rule-readiness item(s) require manual review before any patch.** Ready: H_EP_ACTIVE_FADE_RISK. Candidates: H_ACTIVE_BURST_MB_EXIT, H_MB_EXIT_DAY3_FILTER, H_PAUSE_NO_THRUST_MISFIRE, H_PAUSE_REPEAT_STALE. Soft cautions: none. (§RR)
   _Rule-readiness source: RULE_READINESS_MONITOR_V14_DF; ID column: candidate_rule_id; monitor rows: 17; non-observe rows: 5._

## 2. Changed since last run — 2026-06-10 13:33 UTC → 2026-06-10 14:39 UTC
Changed since last run: same-run-date prior snapshot detected; comparison suppressed. Showing current status only.

### Current pipeline status
- SLINGSHOT decision-log target/R:R backfilled rows: **569**.
- Tiny-geometry hygiene flagged rows: **28**.
- Dedup diagnostics: **744** raw full-plan+price rows → **434** unique ticker-date rows.
- SLINGSHOT current state: **OK_EVALUABLE rows = 675** (non-zero; H_SLINGSHOT_TARGET_BASIS measurement live). Rows ≥5 future bars: 1,734.

### Current trading-state
- Post-V5.9.19 TRADE rows: **10**; A1: **0**; A2: **16**. TRADE path is alive.
- KK confirmation: alive, sample n=107, measurement-only.
- KK funnel audit (`kk_gate_funnel_latest.*`): not present.
- PAUSE reconciliation: main tracker = **WATCHING_NOT_RULE_EVIDENCE**; diagnostic = **REJECTED / NOT_CONFIRMED**.
- Realized P&L: `n_with_realized_r` = **1** (threshold 30).

### Rule-readiness state
- **1** READY/SUPPORTED item(s) — manual review required: H_EP_ACTIVE_FADE_RISK. Candidates: 4. Soft cautions: 0.

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.

## 3. Operational status
- Master decision-log rows: **1,601**
- Decision-log source files: **18**
- Latest decision-log sources: `daily_decision_log_2026-05-29.csv`, `daily_decision_log_2026-06-02.csv`, `daily_decision_log_2026-06-03.csv`, `daily_decision_log_2026-06-05.csv`, `daily_decision_log_2026-06-10.csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |   1394 |
| REJECT               |    155 |
| COUNCIL              |     42 |
| TRADE                |     10 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    818 |
| REJECT               |     59 |
| COUNCIL              |     17 |
| TRADE                |     10 |

### Corpus reconciliation
- Candidate decision-log files discovered: **28**
- Included decision-log files: **18**
- Excluded decision-log files: **10** (1 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **1,625 → 1,625 → 1,601**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Sugar Baby=True candidates show 0.37% avg T+5 versus -0.55% for non-Sugar Baby candidates (evaluated n=4318 vs 2730). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
2. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
3. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
4. Realized P&L attribution is live but sample-immature: 2 closed realized rows and 1 with realized R. Use it as plumbing proof only until n_with_realized_r >= 30; do not use it for calibration yet.
5. Corpus reconciliation is now active: 10 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
6. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| SLINGSHOT      |      572 |              349 | ACTIONABLE_SAMPLE |         88.1119 |            49.0566 |         0.0355819 |
| ACTIVE_BURST   |      191 |              174 | ACTIONABLE_SAMPLE |         92.6702 |            39.375  |        -0.990504  |
| PAUSE          |      172 |              147 | ACTIONABLE_SAMPLE |         80.814  |            55.4622 |         1.01195   |
| EP_ACTIVE      |       90 |               84 | ACTIONABLE_SAMPLE |         84.4444 |            48.5714 |         0.543341  |
| DELAYED_EP     |       59 |               55 | ACTIONABLE_SAMPLE |         86.4407 |            51.0638 |         0.215511  |
| ANTICIPATION   |       18 |               18 | BUILDING_SAMPLE   |         83.3333 |            53.3333 |         0.0872136 |
| PRE_BURST      |       10 |               10 | BUILDING_SAMPLE   |         20      |           100      |         3.27077   |
| EP_SPIKE       |        7 |                7 | LOW_SAMPLE        |         85.7143 |            16.6667 |        -5.05739   |
| MOMENTUM_PAUSE |        2 |                2 | LOW_SAMPLE        |        100      |           100      |         0.169841  |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | WATCH_ONLY      | B              | WATCH                |       35 |               31 | ACTIONABLE_SAMPLE |            59.2593 |          4.30406  |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |       10 |               10 | BUILDING_SAMPLE   |            33.3333 |          3.6796   |
| PRE_BURST      | WATCH_ONLY      | B              | WATCH                |        7 |                7 | LOW_SAMPLE        |           100      |          3.27077  |
| DELAYED_EP     | WATCH_ONLY      | C              | WATCH                |        8 |                8 | LOW_SAMPLE        |            57.1429 |          3.21309  |
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       46 |               42 | ACTIONABLE_SAMPLE |            59.375  |          1.56497  |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |      122 |              102 | ACTIONABLE_SAMPLE |            54.7619 |          0.969453 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       60 |               46 | ACTIONABLE_SAMPLE |            44.186  |          0.842018 |
| ANTICIPATION   | WATCH_ONLY      | B              | WATCH                |       10 |               10 | BUILDING_SAMPLE   |            62.5    |          0.487499 |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        7 |                7 | LOW_SAMPLE        |            20      |         -5.16839  |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |       11 |               11 | BUILDING_SAMPLE   |            28.5714 |         -4.75749  |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       75 |               73 | ACTIONABLE_SAMPLE |            36.1111 |         -2.49864  |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       41 |               40 | ACTIONABLE_SAMPLE |            38.8889 |         -1.37494  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       43 |               39 | ACTIONABLE_SAMPLE |            43.75   |         -1.26771  |
| EP_ACTIVE      | REJECT          | D              | REJECT               |       17 |               16 | BUILDING_SAMPLE   |            35.7143 |         -1.19292  |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        8 |                8 | LOW_SAMPLE        |            42.8571 |         -0.370256 |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |      286 |              214 | ACTIONABLE_SAMPLE |            43.9153 |         -0.194363 |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        2 |
| ALL_ROWS       | A2             | COUNCIL              | DELAYED_EP     |        1 |
| ALL_ROWS       | A2             | COUNCIL              | EP_ACTIVE      |        7 |
| ALL_ROWS       | A2             | COUNCIL              | SLINGSHOT      |        3 |
| ALL_ROWS       | A2             | TRADE                | ACTIVE_BURST   |        3 |
| ALL_ROWS       | A2             | TRADE                | DELAYED_EP     |        2 |
| ALL_ROWS       | A2             | TRADE                | EP_ACTIVE      |        1 |
| ALL_ROWS       | A2             | TRADE                | SLINGSHOT      |        4 |
| POST_V5_9_19   | A2             | COUNCIL              | DELAYED_EP     |        1 |
| POST_V5_9_19   | A2             | COUNCIL              | EP_ACTIVE      |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | SLINGSHOT      |        3 |
| POST_V5_9_19   | A2             | TRADE                | ACTIVE_BURST   |        3 |
| POST_V5_9_19   | A2             | TRADE                | DELAYED_EP     |        2 |
| POST_V5_9_19   | A2             | TRADE                | EP_ACTIVE      |        1 |
| POST_V5_9_19   | A2             | TRADE                | SLINGSHOT      |        4 |
| LATEST_SESSION | A2             | TRADE                | SLINGSHOT      |        1 |

### Current interpretation
- A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
### Council A1/A2 reachability audit
- Source: `council_reachability_audit_*.csv` from the Council skill. Diagnostic only; does not change labels or trading rules.
| A1_REACHABLE   | A2_EXECUTABLE_REACHABLE   | ZERO_TRADE_CAUSE    |   n_A1 |   n_A2 |   n_TRADE |   n_A2_to_COUNCIL |
|:---------------|:--------------------------|:--------------------|-------:|-------:|----------:|------------------:|
| NOT_EVALUABLE  | TRUE                      | NO_ZERO_TRADE_ISSUE |      0 |      3 |         2 |                 1 |

- Latest reachability audit source: `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_reachability_audit_latest.csv`
- Top Council demotion reasons from latest audit:
| demotion_reason                                            |   rows |
|:-----------------------------------------------------------|-------:|
| UNKNOWN                                                    |      3 |
| rr_floor_fail_day1_entry_1.36R_lt_2.0_clean_trigger_missed |      1 |

### A1/A2 forward-return slices
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d   |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:----------------|-------------------:|------------------:|
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        7 |                7 | LOW_SAMPLE      |            20      |         -5.16839  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | TRADE                |        3 |                3 | LOW_SAMPLE      |           100      |          3.05238  |
| SLINGSHOT      | ACTIONABLE      | A2             | TRADE                |        4 |                3 | LOW_SAMPLE      |            66.6667 |          0.107715 |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |            50      |          4.79142  |
| DELAYED_EP     | ACTIONABLE      | A2             | TRADE                |        2 |                2 | LOW_SAMPLE      |           100      |          4.53354  |
| SLINGSHOT      | UNKNOWN         | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |            50      |          0.713616 |
| DELAYED_EP     | ACTIONABLE      | A2             | COUNCIL              |        1 |                1 | LOW_SAMPLE      |           100      |          4.158    |
| SLINGSHOT      | ACTIONABLE      | A2             | COUNCIL              |        1 |                1 | LOW_SAMPLE      |             0      |         -1.71882  |
| EP_ACTIVE      | ACTIONABLE      | A2             | TRADE                |        1 |                1 | LOW_SAMPLE      |           nan      |        nan        |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- If A1 remains absent post-V5.9.19, test whether criteria are intentionally rare or unreachable.

## 7. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **215**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 8. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   |   higher_n_eval |   higher_avg_5d |   higher_wr_5d | lower_label   |   lower_n_eval |   lower_avg_5d |   lower_wr_5d |   avg_gap_lower_minus_higher |
|:---------------|:---------------|----------------:|----------------:|---------------:|:--------------|---------------:|---------------:|--------------:|-----------------------------:|
| PAUSE          | B              |             102 |        0.969453 |        54.7619 | C             |             42 |        1.56497 |        59.375 |                      0.59552 |

Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family                         | current_test                                                                               | method_note                                                                                                                                                          | regime_context   |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------------------------|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST                   | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5                                   | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-On          |            73 |        -2.49864 |            40 |       -1.37494  |              -1.12371 | 2026-05-16       |        34 |        14 |          -3.65069 | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE                      | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5                                      | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-On          |            18 |        -4.91728 |           nan |      nan        |              -4.91728 | 2026-05-16       |         4 |       nan |           2.51199 | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE                          | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                                                  | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-On          |            42 |         1.56497 |           102 |        0.969453 |               0.59552 | 2026-05-16       |        16 |        66 |          -2.75171 | WATCHING_NOT_RULE_EVIDENCE |
| H_KK_CONFIRMATION           | ANTICIPATION / KK_CONFIRMATION | Bonde anticipation WITH KK confirmation minus WITHOUT KK confirmation avg T+5 alpha vs SPY | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-On          |             3 |         2.29367 |           104 |        0.250384 |               2.04329 | 2026-05-17       |         2 |        62 |           2.18539 | WATCHING_LOW_SAMPLE        |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **1** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.
### Pre-registered verdict gates
These gates are binding review criteria. A rule patch should not ship unless its hypothesis has a pre-registered SUPPORTED verdict or a separate explicitly documented emergency bug rationale.
| hypothesis_id                  | method_note                                                                                                                                                          | regime_context   | current_state                                                                                                         | required_sample                                                                                                                                      | oos_window                                      | earliest_review                                                                                                       | pre_registered_prediction                                                                                              | supported_if                                                                                                                                                 | rejected_if                                                                                          | ambiguous_if                                                                                                                                             | if_supported                                                                                                                          | if_rejected                                                                         |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN    | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-On          | current effect -1.12; n_a=73; n_b=40; status=WATCHING_NOT_RULE_EVIDENCE                                               | OOS n_C >= 30 and n_D >= 30, with mature T+5/T+10/T+20 windows.                                                                                      | 2026-05-16 onward                               | When both OOS slices meet sample and maturity gates.                                                                  | D/REJECT minus C/WATCH spread remains >= +1.5% OOS.                                                                    | OOS spread >= +1.5% and confidence interval / robustness check does not collapse to zero.                                                                    | OOS spread < +0.5% or direction inverts.                                                             | OOS spread is +0.5% to +1.5% or sample composition is unstable.                                                                                          | Draft V5.9.21-G6-SOFTEN spec; do not ship until patch text is reviewed.                                                               | File hypothesis; no Gate6 softening.                                                |
| H_EP_ACTIVE_COUNCIL_TIGHTEN    | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-On          | current effect -4.92; n_a=18; status=WATCHING_LOW_SAMPLE                                                              | OOS EP_ACTIVE COUNCIL n >= 30 with mature T+5 and at least 10 T+20 rows.                                                                             | 2026-05-16 onward                               | When OOS council-routed EP_ACTIVE rows reach n>=30.                                                                   | EP_ACTIVE COUNCIL average T+5 remains <= -3.0% OOS.                                                                    | OOS avg T+5 <= -3.0% and win rate <= 35% without one-stock distortion.                                                                                       | OOS avg T+5 >= 0% or win rate normalizes above 45%.                                                  | OOS avg T+5 is -3.0% to 0% or driven by one outlier.                                                                                                     | Draft V5.9.21-EPACTIVE-COUNCIL-TIGHTEN review spec.                                                                                   | Keep EP_ACTIVE council routing unchanged.                                           |
| H_PAUSE_BC_INVERT              | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-On          | current effect 0.60; n_a=42; n_b=102; status=WATCHING_NOT_RULE_EVIDENCE                                               | OOS PAUSE B/WATCH n >= 30 and PAUSE C/WATCH n >= 30.                                                                                                 | 2026-05-16 onward                               | When both OOS PAUSE slices hit n>=30 and T+5 is mature.                                                               | PAUSE C/WATCH minus B/WATCH spread remains >= +1.5% OOS.                                                               | OOS spread >= +1.5% and persists after removing tiny/liquidity outliers.                                                                                     | OOS spread < +0.5% or B resumes leadership.                                                          | OOS spread is +0.5% to +1.5% or sample is too concentrated.                                                                                              | Draft V5.9.21-PAUSE-RANK-REVIEW spec; do not change B/C labels before review.                                                         | Keep PAUSE B/C rank mapping unchanged.                                              |
| H_KK_CONFIRMATION              | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-On          | current effect 2.04; n_a=3; n_b=104; status=WATCHING_LOW_SAMPLE                                                       | OOS n >= 30 confirmed AND n >= 30 unconfirmed Bonde anticipation rows with mature T+5 outcomes; both cohorts must satisfy signal_date >= 2026-05-17. | 2026-05-17 onward                               | When both confirmed and unconfirmed cohorts reach n>=30 with mature T+5; component regression only at n>=100 KK rows. | Confirmed cohort T+5 alpha vs SPY exceeds unconfirmed cohort by at least +0.50 percentage points.                      | T+5 alpha spread >= +0.50 pp, T+10 or T+20 confirms direction, no single ticker >40% of spread, weekly consistency >=60%, and bootstrap_supported_pct >=80%. | T+5 alpha spread <= 0 or unconfirmed cohort outperforms after sample gates.                          | T+5 alpha spread is 0 to +0.50 pp, multi-horizon direction is mixed, ticker/week concentration is excessive, or bootstrap robustness is below threshold. | Use KK confirmation as Layer 5 priority/confidence signal only; do not hard-reject unconfirmed Bonde rows.                            | Deprecate KK confirmation in Layer 5 decisions; keep KK fields as diagnostics only. |
| H_SLINGSHOT_TARGET_BASIS       | Measure SLINGSHOT_PRIMARY full-plan unique ticker-date rows for R:R>=2.0 and later T+5 expectancy after evaluability gates pass.                                     | Risk-On          | 744 raw full-plan+price rows; 434 unique full-plan+price ticker-date rows; 301 unique OK_EVALUABLE ticker-date rows.  | unique_ok_evaluable_ticker_date_rows >= 30 and at least 10 OOS rows after 2026-05-22.                                                                | Starts 2026-05-22                               | When unique OK_EVALUABLE ticker-date rows reach n>=30.                                                                | >=40% of SLINGSHOT_PRIMARY full-plan unique ticker-date rows clear V5.9 R:R floor >= 2.0.                              | R:R>=2.0 pass rate >=40% and T+5 expectancy is not worse than ACTIVE_BURST baseline.                                                                         | R:R>=2.0 pass rate <30% or T+5 expectancy materially underperforms ACTIVE_BURST.                     | R:R pass rate is 30–40% or expectancy is positive but under-sampled.                                                                                     | Keep SLINGSHOT measurement path live; consider later context/ranking overlay only after 100+ unique OK_EVALUABLE rows.                | Do not promote SLINGSHOT; review target-basis and detection criteria.               |
| H_SUGAR_BABIES_CONTEXT_OVERLAY | Compare Sugar Baby=True vs False rows by mature T+5, then require OOS and family-level confirmation before any ranking-context boost.                                | Risk-On          | Sugar Baby=True candidates show 0.37% avg T+5 versus -0.55% for non-Sugar Baby candidates (evaluated n=4318 vs 2730). | OOS >= 100 evaluated Sugar=True and >= 100 Sugar=False rows, plus at least two setup families with n>=30.                                            | Next mature weekly cohorts after current digest | When OOS rows and family spread requirements are met.                                                                 | Sugar=True retains >= +1.0% avg T+5 spread over Sugar=False without worsening win-rate materially.                     | OOS avg spread >= +1.0% and at least two families have non-negative confirmation.                                                                            | OOS spread < +0.25% or driven by one family only.                                                    | OOS spread +0.25% to +1.0% or family split is mixed.                                                                                                     | Draft Sugar Babies ranking_context_score proposal; cannot override R:R, DTE, hard rejects, failed EP, dilution/offering, or bad data. | Keep Sugar Babies as monitoring-only context.                                       |
| H_REALIZED_PNL_CORRELATION     | Compare actual broker realized R/P&L against system setup/action/final-status slices once n_with_realized_r >= 30.                                                   | Risk-On          | 1 realized-R rows; threshold not met.                                                                                 | n_with_realized_r >= 30 total, then >=10 per major setup/action slice before slice-level claims.                                                     | Broker-export rows as they arrive               | When realized-R count reaches n>=30.                                                                                  | Layer 5 realized-R selection should outperform raw WATCH/COUNCIL forward-return expectancy on comparable setup slices. | Realized R is positive overall and aligns with the strongest forward-return slices.                                                                          | Realized R is negative despite positive forward-return slices, implying execution/selection failure. | Positive P&L but too concentrated in one trade or mismatch between broker rows and system rows.                                                          | Use realized-R weighting in weekly system review; do not change signal rules solely from P&L.                                         | Prioritize execution/selection review before signal-rule changes.                   |

### PAUSE reconciliation (v4.14.06)
- Main tracker status: **WATCHING_NOT_RULE_EVIDENCE**.
- PAUSE diagnostic status: **REJECTED / NOT_CONFIRMED**.
- Interpretation: PAUSE B/C inversion remains tracked in the broad hypothesis table, but current PAUSE diagnostic evidence does not confirm a rule-change-ready inversion.

### KK summary (v4.14.06)
- KK confirmation: alive, low sample (n=107), measurement-only.
- KK Monster / Extension: not proven; no mature rows or required columns missing.
- No KK hard gate or ranking change authorized.
- KK funnel audit (`kk_gate_funnel_latest.*`): not present this run.

### KK confirmation study
Research-only: tests whether Bonde anticipation rows with KK leadership-quality confirmation outperform Bonde anticipation rows without KK confirmation. This does not alter trading labels, ranking, R:R, or hard gates.
**Operational definition:** `kk_research_confirmation = kk_extend_score >= 70 AND (kk_leadership_score >= 70 OR kk_group_strength_score >= 50) AND all KK hard-disqualifier flags are false except kk_pause_too_long. kk_low_price_for_extension remains a disqualifier.`
**OOS semantics:** current counts are cumulative mature evidence; OOS counts are strict `signal_date >= 2026-05-17` mature evidence.
**Realistic review timing:** earliest likely verdict review is late July–mid September 2026, depending on confirmed-row accumulation and T+5/T+10/T+20 maturity.
| hypothesis_id     | status              | baseline_available   |   confirmed_n_5d |   unconfirmed_n_5d |   spread_alpha_vs_spy_5d_pp |   supported_threshold_t5_alpha_spread_pp |   bootstrap_supported_pct |   supported_bootstrap_threshold_pct |   weekly_consistency_pct |   single_ticker_spread_share_pct |   invalid_signal_date_rows_dropped |
|:------------------|:--------------------|:---------------------|-----------------:|-------------------:|----------------------------:|-----------------------------------------:|--------------------------:|------------------------------------:|-------------------------:|---------------------------------:|-----------------------------------:|
| H_KK_CONFIRMATION | WATCHING_LOW_SAMPLE | True                 |                3 |                104 |                     2.04329 |                                      0.5 |                       nan |                                  80 |                      100 |                          12.2912 |                                  0 |

**Current cohort split (cumulative, in-sample baseline):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |      123 |              104 |         0.365527 |              0.250384 |                72 |          1.13162  |                23 |          0.368327 |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        3 |                3 |         0.902316 |              2.29367  |                 1 |          0.622096 |                 0 |        nan        |

**Strict OOS cohort split (signal_date >= 2026-05-17; drives verdict):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |       79 |               62 |         0.573038 |               1.07067 |                32 |           1.28204 |                 0 |               nan |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        2 |                2 |         0.731373 |               3.25606 |                 0 |         nan       |                 0 |               nan |

**KK classification audit sample:**
| ticker   | signal_date   | kk_research_confirmation   |   kk_extend_score |   kk_leadership_score |   kk_group_strength_score | kk_low_price_for_extension   | kk_pause_too_long   | kk_risk_too_wide   | kk_weak_liquidity   | kk_too_far_from_highs   | kk_major_breakdown   | kk_late_stage_proxy   | kk_bag_holder   | kk_weak_bonde_score   |
|:---------|:--------------|:---------------------------|------------------:|----------------------:|--------------------------:|:-----------------------------|:--------------------|:-------------------|:--------------------|:------------------------|:---------------------|:----------------------|:----------------|:----------------------|
| AVNS     | 2026-05-18    | False                      |           73.3579 |               92.5688 |                  16.0741  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| SILA     | 2026-05-18    | False                      |           71.589  |               83.8692 |                  29.3464  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| SILA     | 2026-05-19    | False                      |           70.9557 |               83.4916 |                  28.2179  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-20    | False                      |           72.3139 |               92.5688 |                  14.4052  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| TBRG     | 2026-05-21    | False                      |           72.0825 |               89.3302 |                   7.44879 | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-21    | False                      |           71.7059 |               92.2271 |                  13.2879  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| TBRG     | 2026-05-22    | False                      |           73.9513 |               87.8889 |                   7.44879 | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-22    | False                      |           69.4722 |               91.2918 |                  13.6603  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| TBRG     | 2026-05-27    | False                      |           71.1344 |               86.7037 |                   8.93855 | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| KALV     | 2026-05-29    | False                      |           78.583  |               91.6667 |                  42.149   | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |

**KK confirmed cohort rows plus unconfirmed sample:**
| ticker   | signal_date   | kk_research_confirmation   | kk_confirmation_cohort                     | kk_base_source                | source_kk_file                         | _kk_trade_key   |   _kk_duplicate_key_count | kept_for_hypothesis   |   kk_extend_score |   kk_low_price_for_extension |   kk_pause_too_long |
|:---------|:--------------|:---------------------------|:-------------------------------------------|:------------------------------|:---------------------------------------|:----------------|--------------------------:|:----------------------|------------------:|-----------------------------:|--------------------:|
| GSAT     | 2026-05-15    | True                       | BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    | skill_pack_candidate_outcomes | nan                                    | GSAT|2026-05-15 |                         1 | True                  |           72.0487 |                            0 |                   1 |
| XOMA     | 2026-05-29    | True                       | BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    | skill_pack_candidate_outcomes | bonde_kk_final_decision_2026-05-29.csv | XOMA|2026-05-29 |                         1 | True                  |           75.0056 |                            0 |                   1 |
| XOMA     | 2026-06-01    | True                       | BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    | skill_pack_candidate_outcomes | bonde_kk_final_decision_2026-06-01.csv | XOMA|2026-06-01 |                         1 | True                  |           74.3869 |                            0 |                   1 |
| TALK     | 2026-05-04    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | TALK|2026-05-04 |                         1 | True                  |          nan      |                          nan |                 nan |
| EHAB     | 2026-05-04    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | EHAB|2026-05-04 |                         1 | True                  |          nan      |                          nan |                 nan |
| GSAT     | 2026-05-04    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | GSAT|2026-05-04 |                         1 | True                  |          nan      |                          nan |                 nan |
| IBTA     | 2026-05-04    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | IBTA|2026-05-04 |                         1 | True                  |          nan      |                          nan |                 nan |
| CXW      | 2026-05-04    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | CXW|2026-05-04  |                         1 | True                  |          nan      |                          nan |                 nan |
| TERN     | 2026-05-04    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | TERN|2026-05-04 |                         1 | True                  |          nan      |                          nan |                 nan |
| VRE      | 2026-05-05    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | VRE|2026-05-05  |                         1 | True                  |          nan      |                          nan |                 nan |
| EHAB     | 2026-05-05    | False                      | BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION | skill_pack_candidate_outcomes | nan                                    | EHAB|2026-05-05 |                         1 | True                  |          nan      |                          nan |                 nan |

- KK standalone report: `kk_confirmation_report_latest.md`
- Pre-registered action: if SUPPORTED, use KK only as a Layer 5 priority/confidence signal; if REJECTED, keep KK diagnostics but stop using it for Layer 5 confirmation.
### Hypothesis discipline meta-rules
- Maximum active WATCHING hypotheses: **7**. Current pre-registered hypotheses: **7**.
- New hypotheses should not be added unless one existing hypothesis closes as `SUPPORTED`, `REJECTED`, or `AMBIGUOUS`, or unless there is a separately documented emergency/data-capture rationale. KK confirmation is the documented data-capture exception: without capturing cohorts now, the next 8–12 weeks would not answer the question.
- After a `SUPPORTED` hypothesis ships a patch, no new hypothesis from the same family should be opened for **90 days** unless there is an emergency bug rationale.
- If `H_REALIZED_PNL_CORRELATION` returns `REJECTED`, all signal-rule patches pause until execution / selection quality is reviewed.
- These meta-rules are designed to prevent hypothesis creep and post-hoc rule changes while OOS evidence matures.

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
- Council/disagreement resolver rows: **25**
| outcome_status   |   rows |
|:-----------------|-------:|
| PENDING          |     14 |
| RESOLVED         |     10 |
| NOT_APPLICABLE   |      1 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                  |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:------------------------------------------------------------------|
| PGNY     | DELAYED_EP     | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | nan                                                               |
| DBX      | ACTIVE_BURST   | CANCEL            | RESOLVED         | NEVER_TRIGGERED | ALIGNED                     | nan                                                               |
| SEZL     | DELAYED_EP     | CANCEL            | RESOLVED         | AMBIGUOUS       | ALIGNED                     | nan                                                               |
| LOCO     | DELAYED_EP     | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| SEZL     | DELAYED_EP     | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| CLSK     | SLINGSHOT      | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| IFS      | SLINGSHOT      | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| CGCT     | SLINGSHOT      | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| LLY      | SLINGSHOT      | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| KGS      | PAUSE          | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| EFC      | PAUSE          | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |
| KEX      | PAUSE          | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=0 |


**Council resolver determinism audit (v4.13.61+ source-priority + round-aware):**
- Raw Council resolver rows loaded: **27.0**
- Rows after latest-run dedup: **25.0**
- Latest source per ticker:
| ticker   | signal_date   | setup_family   | council_verdict   | source_file                          |   source_priority |   run_round |
|:---------|:--------------|:---------------|:------------------|:-------------------------------------|------------------:|------------:|
| PGNY     | 2026-05-18    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-19.csv |               100 |           0 |
| DBX      | 2026-05-18    | ACTIVE_BURST   | CANCEL            | council_disagreements_2026-05-19.csv |               100 |           0 |
| SEZL     | 2026-05-18    | DELAYED_EP     | CANCEL            | council_disagreements_2026-05-19.csv |               100 |           0 |
| LOCO     | 2026-05-19    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| SEZL     | 2026-05-19    | DELAYED_EP     | CANCEL            | council_disagreements_2026-05-20.csv |               100 |           0 |
| CLSK     | 2026-05-19    | SLINGSHOT      | CANCEL            | council_disagreements_2026-05-20.csv |               100 |           0 |
| IFS      | 2026-05-19    | SLINGSHOT      | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| CGCT     | 2026-05-19    | SLINGSHOT      | CANCEL            | council_disagreements_2026-05-20.csv |               100 |           0 |
| LLY      | 2026-05-19    | SLINGSHOT      | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| KGS      | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| EFC      | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| KEX      | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| CDNA     | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| ARM      | 2026-05-19    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| TTMI     | 2026-05-19    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| ALAB     | 2026-05-19    | ACTIVE_BURST   | DEFER             | council_disagreements_2026-05-20.csv |               100 |           0 |
| RLAY     | 2026-05-19    | EP_ACTIVE      | CANCEL            | council_disagreements_2026-05-20.csv |               100 |           0 |
| AAP      | 2026-05-21    | EP_ACTIVE      | DEFER             | council_disagreements_2026-05-22.csv |               100 |           0 |
| GFS      | 2026-05-21    | EP_ACTIVE      | DEFER             | council_disagreements_2026-05-22.csv |               100 |           0 |
| ADEA     | 2026-06-02    | SLINGSHOT      | DEFER             | council_disagreements_2026-06-03.csv |               100 |           0 |


## 12. Day-1 shape diagnostics
Compact executive view. Full coverage/verdict tables remain in the Day-1 audit CSV/markdown outputs.
- Source-capable coverage minimum: **99.0%**
- All-row coverage minimum, legacy rows included: **57.5%**
- Source-capable field statuses:
| field                   |   coverage_pct | status   |
|:------------------------|---------------:|:---------|
| day1_close_pct_in_range |           99.5 | OK       |
| day1_move_pct           |           99.7 | OK       |
| day1_vol_ratio          |           99   | OK       |

- Day-1 verdict summary:
| verdict                      |   rows |
|:-----------------------------|-------:|
| INSUFFICIENT_RESOLVED_SAMPLE |      4 |


## 13. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. Measurement only; no SLINGSHOT rule-change evidence yet.
- Rows: **2,318**; full-plan proxy rows: **1,058**; rows with ≥5 future bars: **1,734**; OK-evaluable rows: **675**.
- DECISION_LOG rows target/R:R enriched inside learning loop from universe planning fields: **569**
- Entry-source classification (v4.13.73): **CAPTURED_AT_TRIGGER=2,135** (verdict-eligible pool, gated on T+5 maturity); BACKFILLED_FROM_SIGNAL_CLOSE=178 (robustness panel only, excluded from verdict); MISSING_ENTRY_UNRECOVERABLE=5 (excluded).
- Latest pack health: `2026-06-09` **249/249** rows CAPTURED_AT_TRIGGER (entry capture healthy).
- Top missing/evaluability reasons:
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| NO_PRICE_DATA            |    862 |
| OK_EVALUABLE             |    675 |
| INSUFFICIENT_FUTURE_BARS |    441 |
| MISSING_ENTRY            |    183 |
| NEVER_TRIGGERED          |     94 |

- Full detail retained in: `slingshot_evaluability_audit_latest.md/csv`, `slingshot_scope_price_diagnostics_latest.md`, `slingshot_hygiene_diagnostics_latest.md`, and the corresponding summary CSVs.
- Interpretation: missing R:R is a field/evaluability issue, not zero R:R or negative SLINGSHOT expectancy.
- Bucket-distribution snapshot available in SLINGSHOT diagnostics exports; omitted here for compactness.

## 14. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Current read: Sugar Baby=True candidates show 0.37% avg T+5 versus -0.55% for non-Sugar Baby candidates (evaluated n=4318 vs 2730).
- Interpretation: Sugar Babies currently has broader sample support than EP9M for a future `ranking_context_score` contribution, but still needs out-of-sample / mature-week validation before any non-zero boost.
- Sugar Babies ticker lookup rows: **488**
### Sugar Baby vs non-Sugar Baby
| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     5052 |                4318 |             0.367751 |               46.5493 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     4419 |                3782 |             0.654804 |               47.4881 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     3253 |                2730 |            -0.545881 |               48.5714 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     2821 |                2376 |            -0.463399 |               48.4428 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Recurrence buckets
| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 0             |     2821 |                2376 |            -0.463399 |               48.4428 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      311 |                 287 |            -0.331842 |               43.554  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      269 |                 231 |             0.16892  |               48.4848 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      397 |                 343 |            -0.216488 |               46.0641 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 8+            |     3442 |                2921 |             0.892482 |               47.963  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Setup-family × Sugar Baby=True
| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     3960 |                3367 |             0.519098 |               47.1933 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      383 |                 361 |            -0.661735 |               40.1662 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |      215 |                 183 |             1.75616  |               51.9126 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      166 |                 149 |            -1.99994  |               36.2416 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |      126 |                 116 |             0.428779 |               43.9655 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |      161 |                 107 |             0.049633 |               53.271  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       24 |                  23 |            -0.879836 |               43.4783 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        7 |                   6 |            -1.74923  |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        9 |                   5 |             6.2245   |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DIAGNOSTICS    |        1 |                   1 |             0.207796 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

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
| ep9m_context_type |           nan |        1 |                   1 |            2.02265 |          2.02265 |          100 |               nan |    218.446  |
| ep9m_context_type |           nan |        1 |                   0 |          nan       |        nan       |          nan |               nan |     19.4723 |

- Interpretation: realized R should be used to validate whether Layer 5 execution is selecting the right subset from WATCH/COUNCIL candidates.

## 16. Investigation queue
### New this run
- None auto-detected.
### Carried forward
| priority   | item                                                  | why                                                                                                                                                                                                                                                      |
|:-----------|:------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1         | Realized-P&L correlation check                        | Once n_with_realized_r >= 30, compare realized R by setup_family/action_label/final_trade_status against learning-loop forward-return expectancy. This is the key bridge between signal quality and actual trading quality.                              |
| P1         | A1/A2 executable-signal health check                  | Confirm A1 count, A2 routing, and whether zero clean TRADE rows is intended strictness or over-routing.                                                                                                                                                  |
| P1         | Investigate reject/watch and B/C/D inversion          | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.                                                                                                             |
| P1         | Track pre-registered rule-change hypotheses           | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, H_PAUSE_BC_INVERT, and H_KK_CONFIRMATION daily with OOS and realized-R gates before any rule patch.                                                                                    |
| P1         | Accumulate KK confirmation cohorts                    | Keep H_KK_CONFIRMATION unchanged until n>=30 confirmed and n>=30 unconfirmed rows have mature T+5 outcomes.                                                                                                                                              |
| P2         | Sugar Babies validation                               | Candidate for first ranking_context_score contribution, but validate out-of-sample and by setup family before non-zero boost.                                                                                                                            |
| P1         | Keep SLINGSHOT target/R:R enrichment in learning loop | Learning loop backfilled 569 DECISION_LOG row(s) from diagnostic/skill-pack planning fields. Actionability skill remains stable; continue measurement-layer enrichment from universe outputs until the raw decision-log schema is intentionally revised. |
| P2         | SLINGSHOT hygiene verification                        | Before first OK_EVALUABLE rows mature, review tiny-geometry flags, duplicate ticker-date rows, and backfill-source attribution in `slingshot_hygiene_diagnostics_latest.md`.                                                                             |

### Resolved since last run
- None auto-detected.
- Persistent queue files: `investigation_queue_latest.csv`, `investigation_queue_history_latest.csv`

## 17. Open caveats / next actions
- Day-1 fields are being captured, but verdicts remain insufficient until resolved sample sizes mature.

## 18. Evidence discipline
- This digest is monitoring context, not permission to change rules.
- Rule-change evidence should come from weekly cohorts with mature T+5/T+10/T+20 windows and repeated effects across cohorts.
- `final_trade_status` remains the executable decision field; `tier` is dashboard/source context only.
- EP9M, KK confirmation, and Sugar Babies may inform review priority only after validated; none can override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering, or bad data.

## PAUSE Diagnostics

_Learning-loop-derived, post-decision diagnostic. Not known to actionability at decision time. No trading-rule changes. Source: v4.13.77 PAUSE diagnostics layer._

Rows analyzed: 174
Data issue rows: 38
Repeat stale rows: 30
Valid 20-bar thrust rows: 47
Valid longer-lookback thrust rows: 28
Weak-thrust-only rows: 15
No-real-thrust rows: 15
Insufficient-price-data rows: 1

Raw flag counts:
- data_issue_flag: 38
- repeat_pause_signal_10d_ge2: 55
- repeat_pause_signal_10d_ge3: 35
- valid_longer_lookback_thrust_flag: 73
- weak_thrust_only_flag: 15
- no_real_thrust_flag: 15

Top repeat tickers:
| ticker | count_10d | first_signal_date | last_signal_date |
|---|---|---|---|
| WSR | 7 | 2026-05-05 | 2026-06-09 |
| SILA | 6 | 2026-05-05 | 2026-06-09 |
| TWO | 6 | 2026-05-15 | 2026-06-09 |
| RAMP | 4 | 2026-05-27 | 2026-06-04 |
| APLS | 3 | 2026-05-05 | 2026-05-15 |
| TALK | 3 | 2026-05-05 | 2026-05-11 |
| EFC | 2 | 2026-05-12 | 2026-05-27 |
| KALV | 2 | 2026-05-05 | 2026-06-02 |
| TBRG | 2 | 2026-05-05 | 2026-06-02 |
| ASRT | 2 | 2026-05-27 | 2026-06-04 |

Manual review queue (top 15 by priority):
| priority | ticker | signal_date | class | reason |
|---|---|---|---|---|
| 1 | ACLX | 2026-04-29 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=77.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | ACLX | 2026-04-29 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=77.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AIRG | 2026-05-27 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=21.1%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-12 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-15 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-15 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-06-09 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | CCRN | 2026-05-27 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=29.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | CNTA | 2026-05-27 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=44.0%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | DAWN | 2026-04-24 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=65.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | DAWN | 2026-04-24 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=65.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | FA | 2026-05-27 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=23.1%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | FLYW | 2026-05-22 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=20.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |

**Hypothesis state (v4.13.77):**
- `H_PAUSE_BC_INVERT` = REJECTED / NOT_CONFIRMED — outlier-driven, threshold-fragile.
- `H_PAUSE_FRESHNESS_COOLDOWN` = CANDIDATE — repeat PAUSE within 10 trading sessions without a fresh thrust underperforms first PAUSE signals. **No production rule shipped.**

## Council Effectiveness

_Diagnostic measurement only — run_date 2026-06-10, spec v1.0. No rule, skill, or schema changes._

Rows analyzed: 1601
Rows matched to council artifacts: 10
Rows with mature T+5: 1340
Rows immature / no-data: 261

### Council vs Actionability Matrix

| actionability | council | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | avg_t20 |
|---|---|---|---|---|---|---|---|
| REJECT | UNKNOWN | 155 | 152 | -1.74% | 41.06% | -6.74% | 6.62% |
| TAKE | UNKNOWN | 10 | 9 | -1.84% | 55.56% | -4.62% | n/a |
| WATCH | APPROVE | 5 | 5 | -1.57% | 40.00% | -5.23% | n/a |
| WATCH | REJECT | 5 | 5 | 1.03% | 60.00% | 6.33% | n/a |
| WATCH | UNKNOWN | 1426 | 1169 | -0.10% | 43.40% | -0.62% | 5.10% |

### TAKE Challenge Value

| group | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 | avg_t20 | win_rate_t20 |
|---|---|---|---|---|---|---|---|---|
| TAKE_APPROVED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_DOWNGRADED_OR_REJECTED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_NEUTRAL_OR_UNKNOWN_COUNCIL | 10 | 9 | -1.84% | 55.56% | -4.62% | 44.44% | n/a | n/a |

### Council Flags (T+5 mature)

| metric | n | rate |
|---|---|---|
| saved_loss_count | 2 | n/a |
| cut_winner_count | 3 | n/a |
| found_winner_count | 0 | n/a |
| missed_loser_count | 0 | n/a |
| saved_loss_rate_among_downgrades | 2 | 40.00% |
| cut_winner_rate_among_downgrades | 3 | 60.00% |
| found_winner_rate_among_upgrades | 0 | n/a |
| missed_loser_rate_among_approvals | 0 | n/a |

### Reason-Category Performance (council-opined rows, T+5 mature)

| reason_category | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 |
|---|---|---|---|---|---|---|
| OTHER | 2 | 2 | 2.31% | 100.00% | -3.09% | 0.00% |
| RISK_REWARD_WEAK | 8 | 8 | -0.91% | 37.50% | 0.19% | 66.67% |

### Interpretation

- If council-downgraded TAKE rows underperform approved TAKE rows, council is adding value.
- If council-downgraded TAKE rows outperform, council is too conservative.
- Require n>=30 per comparison bucket before treating this as evidence.

### Operational Quality

- NOT_APPLICABLE rows: 0
- Join failures (NO_MATCH): 1591
- Rows missing trigger_price: 885
- Rows missing invalidation_price: 878

## Rule-Readiness Summary

_Report date: 2026-06-10_  
_Evidence run_date: 2026-06-04_  
_Evidence freshness: WARNING — 4 business days behind report; monitor may not have advanced (WARNING if > 1)_  
_Source: GLOBAL:RULE_READINESS_MONITOR_V14_DF_  
_Monitor rows: 17_

Rule-Readiness is diagnostic only. It does not change trading rules, position sizing, the actionability skill, the council skill, or the dashboard.

SOURCE_MISSING and REQUIRED_COLUMNS_MISSING rows are tracked for transparency but do not count as independent evidence windows.

A rule should not be changed until the relevant candidate reaches RULE_REVIEW_READY and is manually reviewed.

### Ready for Rule Review

| candidate_rule_id | rule_module | setup_family | spread_t5 | trimmed_spread_t5 | n_smaller_bucket | independent_windows_observed | recommended_action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| H_EP_ACTIVE_FADE_RISK | MB_EXIT | EP_ACTIVE_vs_ACTIVE_BURST | 6.1968 | 6.6725 | 62 | 3 | RULE_REVIEW_READY |

### Candidate Hypotheses

| candidate_rule_id | rule_module | setup_family | spread_t5 | trimmed_spread_t5 | n_smaller_bucket | independent_windows_observed | recommended_action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| H_PAUSE_REPEAT_STALE | PAUSE | PAUSE_REPEAT_VS_FRESH | 1.0392 | 0.2152 | 47 | 3 | ADD_TO_DIGEST |
| H_MB_EXIT_DAY3_FILTER | MB_EXIT | ALL_APPLICABLE | 11.4940 | 10.6417 | 45 | 3 | ADD_TO_DIGEST |
| H_ACTIVE_BURST_MB_EXIT | MB_EXIT | ACTIVE_BURST | 11.4490 | 10.4424 | 31 | 3 | ADD_TO_DIGEST |
| H_PAUSE_NO_THRUST_MISFIRE | PAUSE | PAUSE_NO_THRUST_VS_FOUND | 0.3386 | -0.2915 | 30 | 3 | ADD_TO_DIGEST |

### Soft Cautions

_None._

### Source / Evidence Gaps

| candidate_rule_id | rule_module | data_quality_warning | independent_windows_observed |
| --- | --- | --- | --- |
| H_REGIME_AGGRESSIVE_SUPPORTS_TAKE | REGIME | SOURCE_MISSING | 0 |
| H_REGIME_DEFENSIVE_FILTERS_TAKE | REGIME | SOURCE_MISSING | 0 |
| H_SLINGSHOT_VOLUME_BASIS_VALUE | SLINGSHOT | REQUIRED_COLUMNS_MISSING:ep9m_vol_ratio_50|vol_ratio_50|rel_vol_50 | 0 |

## Probe Trade Experiment Status

- **probe_experiment_status:** ACTIVE
- **probe_kill_switch_status:** ACTIVE
- **learning_loop_probe_split:** READY (v4.14.22)
- **permits_new_live_probe:** True

Today:
- probe_rows_today: 0 (probe_trade_rows_today=0, probe_eligible_watch_rows_today=0)

Cumulative realized probes (persisted realized master, lane=probe):
- probe_realized_rows: 0 / 30 to first verdict (30 more needed)
- probe_avg_realized_r: 0.0
- probe_win_rate: n/a
- probe_total_r: 0.0
- probe_max_drawdown_r: 0.0
