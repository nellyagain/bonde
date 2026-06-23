# Bonde Learning Loop Executive Digest — 2026-06-23

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-06-23 05:13 UTC_
_Notebook: v4.14.40 — DATA_ISSUE quarantine on learning-evidence pool; research-only, no trading-rule changes_

## 1. Today's required action
1. **No automatic rule changes.** Any READY/SUPPORTED item from the rule-readiness monitor still requires manual review before patching. (§9 hypothesis tracker / verdict gates)
2. **Review first SLINGSHOT OK-evaluable cohort under H_SLINGSHOT_TARGET_BASIS; no rule change yet.** OK_EVALUABLE rows: **1,342**; rows ≥5 future bars: **2,826**; unique full-plan+price ticker-date rows: **632**. (§13)
3. **A1 absence is resolved by the A2-floor audit: V5.9.46 has no distinct mechanical A1 gate. A2 is the mechanical top tier.** A1 is not a mechanical rule problem — monitor A2-floor execution quality and realized outcomes, not A1 reachability. PASS_A2_FLOOR rows: **15**; Post-V5.9.19 TRADE rows: **12**; A1 rows: **0**; A2 rows: **35**. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is alive, low sample (n=136), measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **1**. (§15)
7. **Primary rule-review item: H_EP_ACTIVE_FADE_RISK. Manual review required before any rule change.** No rule change has been auto-applied. Ready: H_EP_ACTIVE_FADE_RISK, H_MB_EXIT_DAY3_FILTER. Candidates: H_ACTIVE_BURST_MB_EXIT. Soft cautions: none. (§RR)
   _Rule-readiness source: rule_readiness_monitor_latest.csv; ID column: candidate_rule_id; monitor rows: 3; non-observe rows: 3._

## 2. Changed since last run — 2026-06-18 07:54 UTC → 2026-06-23 05:13 UTC
- Prior digest date: **2026-06-18**
- Current digest date: **2026-06-23**
- Comparison window: **2026-06-18 → 2026-06-23**

### Current pipeline status
- SLINGSHOT decision-log target/R:R backfilled rows: **767**.
- Tiny-geometry hygiene flagged rows: **56**.
- Dedup diagnostics: **1,173** raw full-plan+price rows → **632** unique ticker-date rows.
- SLINGSHOT current state: **OK_EVALUABLE rows = 1,342** (non-zero; H_SLINGSHOT_TARGET_BASIS measurement live). Rows ≥5 future bars: 2,826.

### Current trading-state
- Post-V5.9.19 TRADE rows: **12**; A1: **0**; A2: **35**. TRADE path is alive.
- KK confirmation: alive, sample n=136, measurement-only.
- KK funnel audit (`kk_gate_funnel_latest.*`): not present.
- PAUSE reconciliation: main tracker = **WATCHING_NOT_RULE_EVIDENCE**; diagnostic = **REJECTED / NOT_CONFIRMED**.
- Realized P&L: `n_with_realized_r` = **1** (threshold 30).

### Rule-readiness state
- **2** READY/SUPPORTED item(s) — manual review required: H_EP_ACTIVE_FADE_RISK, H_MB_EXIT_DAY3_FILTER. Candidates: 1. Soft cautions: 0.

### Deltas vs prior run
- SLINGSHOT OK_EVALUABLE rows: **1,342** (prior 1,135, Δ +207).
- SLINGSHOT rows ≥5 future bars: **2,826** (prior 2,386, Δ +440).
- Post-V5.9.19 TRADE rows: **12** (prior 12, Δ +0).
- A1 rows: **0** (prior 0, Δ +0).
- A2 rows: **35** (prior 20, Δ +15).
- TRADE row identity: unchanged (n=12).
- Rule-readiness READY/SUPPORTED ids: **2** (prior 2).
- Rule-readiness CANDIDATE ids: **1** (prior 1).
- Rule-readiness SOFT_CAUTION ids: **0** (prior 0).

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.

## 3. Operational status
- Master decision-log rows: **2,076**
- Decision-log source files: **24**
- Latest decision-log sources: `daily_decision_log_2026-06-13.csv`, `daily_decision_log_2026-06-16.csv`, `daily_decision_log_2026-06-17.csv`, `daily_decision_log_2026-06-19.csv`, `daily_decision_log_2026-06-23.csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |   1808 |
| REJECT               |    198 |
| COUNCIL              |     58 |
| TRADE                |     12 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |   1232 |
| REJECT               |    102 |
| COUNCIL              |     33 |
| TRADE                |     12 |

### Corpus reconciliation
- Candidate decision-log files discovered: **35**
- Included decision-log files: **24**
- Excluded decision-log files: **11** (2 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **2,100 → 2,100 → 2,076**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Sugar Baby=True candidates show 0.55% avg T+5 versus -0.12% for non-Sugar Baby candidates (evaluated n=5624 vs 3578). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
2. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
3. A1 has zero post-V5.9.19 rows — RESOLVED by the v4.14.27 A2-floor reachability audit (as of 2026-06-18): A1 has no distinct mechanical gate in V5.9.46; 15 row(s) pass every mechanical gate and are withheld from A1 only by discretionary promotion. A1 emptiness is expected, not a bug.
4. Realized P&L attribution is live but sample-immature: 2 closed realized rows and 1 with realized R. Use it as plumbing proof only until n_with_realized_r >= 30; do not use it for calibration yet.
5. Corpus reconciliation is now active: 11 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
6. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| SLINGSHOT      |      771 |              692 | ACTIONABLE_SAMPLE |         92.0882 |            62.8882 |         1.38627   |
| ACTIVE_BURST   |      251 |              216 | ACTIONABLE_SAMPLE |         94.4223 |            47.0297 |         0.124024  |
| PAUSE          |      305 |              196 | ACTIONABLE_SAMPLE |         82.9508 |            59.2814 |         1.07904   |
| EP_ACTIVE      |      129 |               96 | ACTIONABLE_SAMPLE |         89.1473 |            50      |         0.928488  |
| DELAYED_EP     |       81 |               70 | ACTIONABLE_SAMPLE |         90.1235 |            56.4516 |         0.938274  |
| ANTICIPATION   |       25 |               20 | ACTIONABLE_SAMPLE |         88      |            52.9412 |         0.512665  |
| PRE_BURST      |       17 |               11 | BUILDING_SAMPLE   |         11.7647 |           100      |         3.27077   |
| EP_SPIKE       |       15 |               11 | BUILDING_SAMPLE   |         93.3333 |            50      |        -0.0485799 |
| MOMENTUM_PAUSE |        2 |                2 | LOW_SAMPLE        |        100      |           100      |         0.169841  |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | WATCH_ONLY      | B              | WATCH                |       56 |               39 | ACTIONABLE_SAMPLE |            60      |           4.49474 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |       10 |               10 | BUILDING_SAMPLE   |            33.3333 |           3.6796  |
| PRE_BURST      | WATCH_ONLY      | B              | WATCH                |       10 |                8 | LOW_SAMPLE        |           100      |           3.27077 |
| DELAYED_EP     | WATCH_ONLY      | C              | WATCH                |       15 |                8 | LOW_SAMPLE        |            57.1429 |           3.21309 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       89 |               77 | ACTIONABLE_SAMPLE |            58.1081 |           2.43305 |
| SLINGSHOT      | WATCH_ONLY      | B              | WATCH                |      343 |              303 | ACTIONABLE_SAMPLE |            71.6783 |           1.72151 |
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       85 |               42 | ACTIONABLE_SAMPLE |            59.375  |           1.56497 |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |      401 |              377 | ACTIONABLE_SAMPLE |            56.4841 |           1.18624 |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        7 |                7 | LOW_SAMPLE        |            20      |        -5.16839   |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |       11 |               11 | BUILDING_SAMPLE   |            28.5714 |        -4.75749   |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |      100 |               81 | ACTIONABLE_SAMPLE |            40      |        -1.87488   |
| EP_ACTIVE      | REJECT          | D              | REJECT               |       28 |               17 | BUILDING_SAMPLE   |            33.3333 |        -1.87384   |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       47 |               43 | ACTIONABLE_SAMPLE |            41.0256 |        -1.01834   |
| PAUSE          | REJECT          | D              | REJECT               |       10 |                6 | LOW_SAMPLE        |            66.6667 |        -0.414417  |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |       11 |                8 | LOW_SAMPLE        |            42.8571 |        -0.370256  |
| EP_SPIKE       | WATCH_ONLY      | B              | WATCH                |        9 |                7 | LOW_SAMPLE        |            57.1429 |        -0.0759348 |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        2 |
| ALL_ROWS       | A2             | COUNCIL              | DELAYED_EP     |        2 |
| ALL_ROWS       | A2             | COUNCIL              | EP_ACTIVE      |        7 |
| ALL_ROWS       | A2             | COUNCIL              | SLINGSHOT      |       18 |
| ALL_ROWS       | A2             | TRADE                | ACTIVE_BURST   |        3 |
| ALL_ROWS       | A2             | TRADE                | DELAYED_EP     |        2 |
| ALL_ROWS       | A2             | TRADE                | EP_ACTIVE      |        1 |
| ALL_ROWS       | A2             | TRADE                | PAUSE          |        2 |
| ALL_ROWS       | A2             | TRADE                | SLINGSHOT      |        4 |
| ALL_ROWS       | A2             | WATCH                | SLINGSHOT      |        1 |
| POST_V5_9_19   | A2             | COUNCIL              | DELAYED_EP     |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | EP_ACTIVE      |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | SLINGSHOT      |       18 |
| POST_V5_9_19   | A2             | TRADE                | ACTIVE_BURST   |        3 |
| POST_V5_9_19   | A2             | TRADE                | DELAYED_EP     |        2 |
| POST_V5_9_19   | A2             | TRADE                | EP_ACTIVE      |        1 |
| POST_V5_9_19   | A2             | TRADE                | PAUSE          |        2 |
| POST_V5_9_19   | A2             | TRADE                | SLINGSHOT      |        4 |
| POST_V5_9_19   | A2             | WATCH                | SLINGSHOT      |        1 |
| LATEST_SESSION | A1/A2          | NONE                 | ALL            |        0 |

### A2-floor reachability funnel (v4.14.27 audit, as of 2026-06-18)
| gate                          |   rows_entering |   rows_passing |   rows_failed |   rows_not_reconstructable |
|:------------------------------|----------------:|---------------:|--------------:|---------------------------:|
| G00_start_rows                |            1998 |           1998 |             0 |                          0 |
| G01_setup_family_eligible     |            1998 |           1442 |           556 |                          0 |
| G02_actionable_candidate      |            1442 |             44 |          1398 |                          0 |
| G03_entry_and_stop_present    |              44 |             41 |             3 |                          0 |
| G04_planned_rr_present        |              41 |             19 |            22 |                          0 |
| G05_rr_floor_ge_2R            |              19 |             19 |             0 |                          0 |
| G06_long_geometry             |              19 |             19 |             0 |                          0 |
| G07_slingshot_clean_structure |              19 |             17 |             2 |                          0 |
| G09_slingshot_vol_gate        |              17 |             17 |             0 |                          0 |
| G10_catalyst_grade_ok         |              17 |             16 |             1 |                          0 |
| G11_dte_gate                  |              16 |             15 |             0 |                          1 |

- First failed gate per row:
| first_failed_gate                  |   n_rows |
|:-----------------------------------|---------:|
| G02_actionable_candidate           |     1398 |
| G01_setup_family_eligible          |      556 |
| G04_planned_rr_present             |       22 |
| PASS_A2_FLOOR                      |       15 |
| G03_entry_and_stop_present         |        3 |
| G07_slingshot_clean_structure      |        2 |
| G10_catalyst_grade_ok              |        1 |
| NOT_RECONSTRUCTABLE_FROM_48COL_LOG |        1 |

- Conclusion: **15** row(s) pass every mechanical gate (PASS_A2_FLOOR). A1 has no distinct mechanical gate in V5.9.46 — A1/A2 share the gate stack — so A1 emptiness is expected, not a bug. Row-level detail: `a1_near_misses_latest.csv`.
### Current interpretation
- A1 has zero post-V5.9.19 rows — RESOLVED by the v4.14.27 A2-floor reachability audit (as of 2026-06-18): A1 has no distinct mechanical gate in V5.9.46; 15 row(s) pass every mechanical gate and are withheld from A1 only by discretionary promotion. A1 emptiness is expected, not a bug.
### Council A1/A2 reachability audit
- Source: `council_reachability_audit_*.csv` from the Council skill. Diagnostic only; does not change labels or trading rules.
| A1_REACHABLE   | A2_EXECUTABLE_REACHABLE   | ZERO_TRADE_CAUSE       |   n_A1 |   n_A2 |   n_TRADE |   n_A2_to_COUNCIL |
|:---------------|:--------------------------|:-----------------------|-------:|-------:|----------:|------------------:|
| NOT_EVALUABLE  | TRUE                      | INTENTIONAL_STRICTNESS |      0 |      6 |         0 |                 6 |

- Latest reachability audit source: `/content/bonde_repo/bonde_screener_cache/council_queues/council_reachability_audit_2026-06-18.csv`
- Top Council demotion reasons from latest audit:
| demotion_reason                                                                 |   rows |
|:--------------------------------------------------------------------------------|-------:|
| UNKNOWN                                                                         |      2 |
| un_triggered_close_5.65_below_trigger_5.80;flat_day1_2.05x_vol_absorption       |      1 |
| below_200sma_-1.57pct_no_reclaim;un_triggered;vol_1.09x;weak_CIR_30.8           |      1 |
| rr_floor_pinned_2.01R;~12pct_stop;weak_CIR_23.7_down_day;un_triggered           |      1 |
| light_volume_0.65x_no_participation;un_triggered;needs_+5.5pct                  |      1 |
| below_200sma_-2.08pct_no_reclaim;un_triggered;light_vol_0.90x;rr_floor_illusion |      1 |

### A1/A2 forward-return slices
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d   |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:----------------|-------------------:|------------------:|
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        7 |                7 | LOW_SAMPLE      |                 20 |         -5.16839  |
| SLINGSHOT      | ACTIONABLE      | A2             | TRADE                |        4 |                4 | LOW_SAMPLE      |                 50 |         -1.10673  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | TRADE                |        3 |                3 | LOW_SAMPLE      |                100 |          3.05238  |
| DELAYED_EP     | ACTIONABLE      | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |                100 |          5.53459  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |                 50 |          4.79142  |
| DELAYED_EP     | ACTIONABLE      | A2             | TRADE                |        2 |                2 | LOW_SAMPLE      |                100 |          4.53354  |
| SLINGSHOT      | UNKNOWN         | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |                 50 |          0.713616 |
| SLINGSHOT      | ACTIONABLE      | A2             | COUNCIL              |       16 |                1 | LOW_SAMPLE      |                  0 |         -1.71882  |
| SLINGSHOT      | UNKNOWN         | A2             | WATCH                |        1 |                1 | LOW_SAMPLE      |                  0 |         -4.20108  |
| EP_ACTIVE      | ACTIONABLE      | A2             | TRADE                |        1 |                1 | LOW_SAMPLE      |                nan |        nan        |
| PAUSE          | ACTIONABLE      | A2             | TRADE                |        2 |                0 | PARTIAL_OUTCOME |                nan |        nan        |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- A1 absence is explained by the A2-floor reachability funnel above; no further A1 reachability investigation is required unless the funnel changes.

## 7. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **237**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 8. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   | higher_n_eval   | higher_avg_5d   | higher_wr_5d   | lower_label   | lower_n_eval   | lower_avg_5d   | lower_wr_5d   | avg_gap_lower_minus_higher   | linked_hypothesis     | oos_spread   | hypothesis_status                                 |
|:---------------|:---------------|:----------------|:----------------|:---------------|:--------------|:---------------|:---------------|:--------------|:-----------------------------|:----------------------|:-------------|:--------------------------------------------------|
| ~~PAUSE~~      | ~~B~~          | ~~148~~         | ~~1.028~~       | ~~58.91~~      | ~~C~~         | ~~42~~         | ~~1.565~~      | ~~59.38~~     | ~~+0.54~~                    | ~~H_PAUSE_BC_INVERT~~ | ~~-2.47~~    | ~~CLOSED (diagnostic: REJECTED / NOT_CONFIRMED)~~ |

Struck rows: linked hypothesis REJECTED by the diagnostic — shown for auditability, status CLOSED; not a live trigger.
Annotation (v4.14.34 E2-inv): linked_hypothesis/oos_spread/hypothesis_status come from the pre-registered hypothesis tracker and the PAUSE diagnostic verdict; UNTRACKED rows have no pre-registered hypothesis. In-sample inversion is not rule-change evidence; OOS spread drives the verdict.
Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family                         | current_test                                                                               | method_note                                                                                                                                                          | regime_context   |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------------------------|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST                   | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5                                   | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-on          |            81 |        -1.87488 |            43 |       -1.01834  |             -0.856539 | 2026-05-16       |        42 |        17 |          -2.81694 | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE                      | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5                                      | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-on          |            18 |        -4.91728 |           nan |      nan        |             -4.91728  | 2026-05-16       |         4 |       nan |           2.51199 | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE                          | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                                                  | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-on          |            42 |         1.56497 |           148 |        1.02796  |              0.537009 | 2026-05-16       |        15 |        86 |          -2.47084 | WATCHING_NOT_RULE_EVIDENCE |
| H_KK_CONFIRMATION           | ANTICIPATION / KK_CONFIRMATION | Bonde anticipation WITH KK confirmation minus WITHOUT KK confirmation avg T+5 alpha vs SPY | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-on          |             3 |         2.29367 |           133 |        0.118817 |              2.17485  | 2026-05-17       |         2 |        91 |           2.63909 | WATCHING_LOW_SAMPLE        |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **1** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.
### Pre-registered verdict gates
These gates are binding review criteria. A rule patch should not ship unless its hypothesis has a pre-registered SUPPORTED verdict or a separate explicitly documented emergency bug rationale.
| hypothesis_id                  | method_note                                                                                                                                                          | regime_context   | current_state                                                                                                          | required_sample                                                                                                                                      | oos_window                                      | earliest_review                                                                                                       | pre_registered_prediction                                                                                              | supported_if                                                                                                                                                 | rejected_if                                                                                          | ambiguous_if                                                                                                                                             | if_supported                                                                                                                          | if_rejected                                                                         |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:-----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN    | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-on          | current effect -0.86; n_a=81; n_b=43; status=WATCHING_NOT_RULE_EVIDENCE                                                | OOS n_C >= 30 and n_D >= 30, with mature T+5/T+10/T+20 windows.                                                                                      | 2026-05-16 onward                               | When both OOS slices meet sample and maturity gates.                                                                  | D/REJECT minus C/WATCH spread remains >= +1.5% OOS.                                                                    | OOS spread >= +1.5% and confidence interval / robustness check does not collapse to zero.                                                                    | OOS spread < +0.5% or direction inverts.                                                             | OOS spread is +0.5% to +1.5% or sample composition is unstable.                                                                                          | Draft V5.9.21-G6-SOFTEN spec; do not ship until patch text is reviewed.                                                               | File hypothesis; no Gate6 softening.                                                |
| H_EP_ACTIVE_COUNCIL_TIGHTEN    | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-on          | current effect -4.92; n_a=18; status=WATCHING_LOW_SAMPLE                                                               | OOS EP_ACTIVE COUNCIL n >= 30 with mature T+5 and at least 10 T+20 rows.                                                                             | 2026-05-16 onward                               | When OOS council-routed EP_ACTIVE rows reach n>=30.                                                                   | EP_ACTIVE COUNCIL average T+5 remains <= -3.0% OOS.                                                                    | OOS avg T+5 <= -3.0% and win rate <= 35% without one-stock distortion.                                                                                       | OOS avg T+5 >= 0% or win rate normalizes above 45%.                                                  | OOS avg T+5 is -3.0% to 0% or driven by one outlier.                                                                                                     | Draft V5.9.21-EPACTIVE-COUNCIL-TIGHTEN review spec.                                                                                   | Keep EP_ACTIVE council routing unchanged.                                           |
| H_PAUSE_BC_INVERT              | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-on          | current effect 0.54; n_a=42; n_b=148; status=WATCHING_NOT_RULE_EVIDENCE                                                | OOS PAUSE B/WATCH n >= 30 and PAUSE C/WATCH n >= 30.                                                                                                 | 2026-05-16 onward                               | When both OOS PAUSE slices hit n>=30 and T+5 is mature.                                                               | PAUSE C/WATCH minus B/WATCH spread remains >= +1.5% OOS.                                                               | OOS spread >= +1.5% and persists after removing tiny/liquidity outliers.                                                                                     | OOS spread < +0.5% or B resumes leadership.                                                          | OOS spread is +0.5% to +1.5% or sample is too concentrated.                                                                                              | Draft V5.9.21-PAUSE-RANK-REVIEW spec; do not change B/C labels before review.                                                         | Keep PAUSE B/C rank mapping unchanged.                                              |
| H_KK_CONFIRMATION              | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-on          | current effect 2.17; n_a=3; n_b=133; status=WATCHING_LOW_SAMPLE                                                        | OOS n >= 30 confirmed AND n >= 30 unconfirmed Bonde anticipation rows with mature T+5 outcomes; both cohorts must satisfy signal_date >= 2026-05-17. | 2026-05-17 onward                               | When both confirmed and unconfirmed cohorts reach n>=30 with mature T+5; component regression only at n>=100 KK rows. | Confirmed cohort T+5 alpha vs SPY exceeds unconfirmed cohort by at least +0.50 percentage points.                      | T+5 alpha spread >= +0.50 pp, T+10 or T+20 confirms direction, no single ticker >40% of spread, weekly consistency >=60%, and bootstrap_supported_pct >=80%. | T+5 alpha spread <= 0 or unconfirmed cohort outperforms after sample gates.                          | T+5 alpha spread is 0 to +0.50 pp, multi-horizon direction is mixed, ticker/week concentration is excessive, or bootstrap robustness is below threshold. | Use KK confirmation as Layer 5 priority/confidence signal only; do not hard-reject unconfirmed Bonde rows.                            | Deprecate KK confirmation in Layer 5 decisions; keep KK fields as diagnostics only. |
| H_SLINGSHOT_TARGET_BASIS       | Measure SLINGSHOT_PRIMARY full-plan unique ticker-date rows for R:R>=2.0 and later T+5 expectancy after evaluability gates pass.                                     | Risk-on          | 1,173 raw full-plan+price rows; 632 unique full-plan+price ticker-date rows; 620 unique OK_EVALUABLE ticker-date rows. | unique_ok_evaluable_ticker_date_rows >= 30 and at least 10 OOS rows after 2026-05-22.                                                                | Starts 2026-05-22                               | When unique OK_EVALUABLE ticker-date rows reach n>=30.                                                                | >=40% of SLINGSHOT_PRIMARY full-plan unique ticker-date rows clear V5.9 R:R floor >= 2.0.                              | R:R>=2.0 pass rate >=40% and T+5 expectancy is not worse than ACTIVE_BURST baseline.                                                                         | R:R>=2.0 pass rate <30% or T+5 expectancy materially underperforms ACTIVE_BURST.                     | R:R pass rate is 30–40% or expectancy is positive but under-sampled.                                                                                     | Keep SLINGSHOT measurement path live; consider later context/ranking overlay only after 100+ unique OK_EVALUABLE rows.                | Do not promote SLINGSHOT; review target-basis and detection criteria.               |
| H_SUGAR_BABIES_CONTEXT_OVERLAY | Compare Sugar Baby=True vs False rows by mature T+5, then require OOS and family-level confirmation before any ranking-context boost.                                | Risk-on          | Sugar Baby=True candidates show 0.55% avg T+5 versus -0.12% for non-Sugar Baby candidates (evaluated n=5624 vs 3578).  | OOS >= 100 evaluated Sugar=True and >= 100 Sugar=False rows, plus at least two setup families with n>=30.                                            | Next mature weekly cohorts after current digest | When OOS rows and family spread requirements are met.                                                                 | Sugar=True retains >= +1.0% avg T+5 spread over Sugar=False without worsening win-rate materially.                     | OOS avg spread >= +1.0% and at least two families have non-negative confirmation.                                                                            | OOS spread < +0.25% or driven by one family only.                                                    | OOS spread +0.25% to +1.0% or family split is mixed.                                                                                                     | Draft Sugar Babies ranking_context_score proposal; cannot override R:R, DTE, hard rejects, failed EP, dilution/offering, or bad data. | Keep Sugar Babies as monitoring-only context.                                       |
| H_REALIZED_PNL_CORRELATION     | Compare actual broker realized R/P&L against system setup/action/final-status slices once n_with_realized_r >= 30.                                                   | Risk-on          | 1 realized-R rows; threshold not met.                                                                                  | n_with_realized_r >= 30 total, then >=10 per major setup/action slice before slice-level claims.                                                     | Broker-export rows as they arrive               | When realized-R count reaches n>=30.                                                                                  | Layer 5 realized-R selection should outperform raw WATCH/COUNCIL forward-return expectancy on comparable setup slices. | Realized R is positive overall and aligns with the strongest forward-return slices.                                                                          | Realized R is negative despite positive forward-return slices, implying execution/selection failure. | Positive P&L but too concentrated in one trade or mismatch between broker rows and system rows.                                                          | Use realized-R weighting in weekly system review; do not change signal rules solely from P&L.                                         | Prioritize execution/selection review before signal-rule changes.                   |

### PAUSE reconciliation (v4.14.06)
- Main tracker status: **WATCHING_NOT_RULE_EVIDENCE**.
- PAUSE diagnostic status: **REJECTED / NOT_CONFIRMED**.
- Interpretation: PAUSE B/C inversion remains tracked in the broad hypothesis table, but current PAUSE diagnostic evidence does not confirm a rule-change-ready inversion.

### KK summary (v4.14.06)
- KK confirmation: alive, low sample (n=136), measurement-only.
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
| H_KK_CONFIRMATION | WATCHING_LOW_SAMPLE | True                 |                3 |                133 |                     2.17485 |                                      0.5 |                       nan |                                  80 |                      100 |                          11.8836 |                                  0 |

**Current cohort split (cumulative, in-sample baseline):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |      163 |              133 |         0.382393 |              0.118817 |               106 |          1.25165  |                53 |          1.7305   |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        3 |                3 |         0.902316 |              2.29367  |                 3 |          0.479186 |                 1 |         -0.256168 |

**Strict OOS cohort split (signal_date >= 2026-05-17; drives verdict):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |      119 |               91 |         0.531558 |              0.616971 |                66 |           1.39732 |                17 |           3.81456 |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        2 |                2 |         0.731373 |              3.25606  |                 2 |           0.40773 |                 0 |         nan       |

**KK classification audit sample:**
_Row table suppressed until n>=10/slice; current confirmed n=2, distinct flag patterns=45._
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
- Council/disagreement resolver rows: **31**
| outcome_status   |   rows |
|:-----------------|-------:|
| RESOLVED         |     23 |
| NOT_APPLICABLE   |      7 |
| PENDING          |      1 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                                                                       |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| PGNY     | DELAYED_EP     | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | nan                                                                                                                    |
| DBX      | ACTIVE_BURST   | CANCEL            | RESOLVED         | NEVER_TRIGGERED | ALIGNED                     | nan                                                                                                                    |
| SEZL     | DELAYED_EP     | CANCEL            | RESOLVED         | AMBIGUOUS       | ALIGNED                     | nan                                                                                                                    |
| LOCO     | DELAYED_EP     | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| SEZL     | DELAYED_EP     | CANCEL            | RESOLVED         | LOSER           | ALIGNED                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| CLSK     | SLINGSHOT      | CANCEL            | RESOLVED         | WINNER          | MISALIGNED                  | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| IFS      | SLINGSHOT      | DEFER             | RESOLVED         | WINNER          | MISALIGNED                  | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| CGCT     | SLINGSHOT      | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=NO_PRICE_DATA; available_future_bars=22; OUTCOME_PENDING_NO_PRICE_DATA |
| LLY      | SLINGSHOT      | DEFER             | RESOLVED         | WINNER          | MISALIGNED                  | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| KGS      | PAUSE          | DEFER             | RESOLVED         | LOSER           | ALIGNED                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| EFC      | PAUSE          | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |
| KEX      | PAUSE          | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=22                               |


_STALE_PENDING_DATA_GAP alarm (v4.14.30): none detected._

**Council resolver determinism audit (v4.13.61+ source-priority + round-aware):**
- Raw Council resolver rows loaded: **33.0**
- Rows after latest-run dedup: **31.0**
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
- Source-capable coverage minimum: **99.2%**
- All-row coverage minimum, legacy rows included: **67.1%**
- Source-capable field statuses:
| field                   |   coverage_pct | status   |
|:------------------------|---------------:|:---------|
| day1_close_pct_in_range |           99.6 | OK       |
| day1_move_pct           |           99.2 | OK       |
| day1_vol_ratio          |           99.4 | OK       |

- Day-1 verdict summary:
| verdict                      |   rows |
|:-----------------------------|-------:|
| INSUFFICIENT_RESOLVED_SAMPLE |      4 |


## 13. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. Measurement only; no SLINGSHOT rule-change evidence yet.
- Rows: **3,215**; full-plan proxy rows: **1,908**; rows with ≥5 future bars: **2,826**; OK-evaluable rows: **1,342**.
- DECISION_LOG rows target/R:R enriched inside learning loop from universe planning fields: **767**
- Entry-source classification (v4.13.73): **CAPTURED_AT_TRIGGER=3,030** (verdict-eligible pool, gated on T+5 maturity); BACKFILLED_FROM_SIGNAL_CLOSE=178 (robustness panel only, excluded from verdict); MISSING_ENTRY_UNRECOVERABLE=7 (excluded).
- Latest pack health: `2026-06-22` **111/111** rows CAPTURED_AT_TRIGGER (entry capture healthy).
- Top missing/evaluability reasons:
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| OK_EVALUABLE             |   1342 |
| NO_PRICE_DATA            |   1283 |
| MISSING_ENTRY            |    185 |
| INSUFFICIENT_FUTURE_BARS |    172 |
| NEVER_TRIGGERED          |    128 |

- Full detail retained in: `slingshot_evaluability_audit_latest.md/csv`, `slingshot_scope_price_diagnostics_latest.md`, `slingshot_hygiene_diagnostics_latest.md`, and the corresponding summary CSVs.
- Interpretation: missing R:R is a field/evaluability issue, not zero R:R or negative SLINGSHOT expectancy.
- Bucket-distribution snapshot available in SLINGSHOT diagnostics exports; omitted here for compactness.

## 14. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Current read: Sugar Baby=True candidates show 0.55% avg T+5 versus -0.12% for non-Sugar Baby candidates (evaluated n=5624 vs 3578).
- Interpretation: Sugar Babies currently has broader sample support than EP9M for a future `ranking_context_score` contribution, but still needs out-of-sample / mature-week validation before any non-zero boost.
- Sugar Babies ticker lookup rows: **529**
### Sugar Baby vs non-Sugar Baby
| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     6666 |                5624 |            0.554417  |               49.431  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     5909 |                4976 |            0.821041  |               50.1407 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     4244 |                3578 |           -0.121636  |               51.2577 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     3718 |                3169 |            0.0350069 |               51.846  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Recurrence buckets
| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 0             |     3718 |                3169 |           0.0350069  |               51.846  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      402 |                 321 |          -0.00219025 |               47.0405 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      361 |                 296 |           0.550935   |               50.6757 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      406 |                 336 |          -0.14186    |               47.9167 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 8+            |     4740 |                4023 |           0.987022   |               50.5344 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Setup-family × Sugar Baby=True
| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     5237 |                4394 |             0.63254  |               49.5676 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      474 |                 424 |            -0.509202 |               42.4528 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |      336 |                 296 |             1.94213  |               57.4324 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      190 |                 179 |            -1.18151  |               41.3408 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |      213 |                 144 |             0.363679 |               59.0278 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |      145 |                 131 |             0.65796  |               45.0382 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       48 |                  36 |             0.809706 |               47.2222 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |       15 |                  12 |             2.68806  |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        7 |                   7 |            -1.28307  |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DIAGNOSTICS    |        1 |                   1 |             0.191814 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

- Council context export: `latest_sugar_babies_context.md` + `latest_sugar_babies_ticker_context.csv`.

## 15. Realized P&L attribution
- Status: **available but sample-immature**. This is trading-layer attribution, not just signal-date forward return.
- Maturity: **2** closed realized rows; **1** with realized R. Calibration threshold: **30+ realized-R rows**.
### Overall realized P&L / R
_Row table suppressed until n>=10/slice; current n=1._
### By setup_family
_Row table suppressed until n>=10/slice; current n=1._
### By action_label
_Row table suppressed until n>=10/slice; current n=1._
### By final_trade_status
_Row table suppressed until n>=10/slice; current n=1._
### By council_verdict
_Row table suppressed until n>=10/slice; current n=1._
### By sugar_baby_flag
_Row table suppressed until n>=10/slice; current n=1._
### By ep9m_context_type
_Row table suppressed until n>=10/slice; current n=1._
- Interpretation: realized R should be used to validate whether Layer 5 execution is selecting the right subset from WATCH/COUNCIL candidates.

## 16. Investigation queue
### New this run
- None auto-detected.
### Carried forward
| priority   | item                                                  | why                                                                                                                                                                                                                                                      |
|:-----------|:------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1         | Realized-P&L correlation check                        | Once n_with_realized_r >= 30, compare realized R by setup_family/action_label/final_trade_status against learning-loop forward-return expectancy. This is the key bridge between signal quality and actual trading quality.                              |
| P1         | Investigate reject/watch and B/C/D inversion          | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.                                                                                                             |
| P1         | Track pre-registered rule-change hypotheses           | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, H_PAUSE_BC_INVERT, and H_KK_CONFIRMATION daily with OOS and realized-R gates before any rule patch.                                                                                    |
| P1         | Accumulate KK confirmation cohorts                    | Keep H_KK_CONFIRMATION unchanged until n>=30 confirmed and n>=30 unconfirmed rows have mature T+5 outcomes.                                                                                                                                              |
| P2         | Sugar Babies validation                               | Candidate for first ranking_context_score contribution, but validate out-of-sample and by setup family before non-zero boost.                                                                                                                            |
| P1         | Keep SLINGSHOT target/R:R enrichment in learning loop | Learning loop backfilled 767 DECISION_LOG row(s) from diagnostic/skill-pack planning fields. Actionability skill remains stable; continue measurement-layer enrichment from universe outputs until the raw decision-log schema is intentionally revised. |
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

Rows analyzed: 307
Data issue rows: 68
Repeat stale rows: 49
Valid 20-bar thrust rows: 67
Valid longer-lookback thrust rows: 48
Weak-thrust-only rows: 30
No-real-thrust rows: 44
Insufficient-price-data rows: 1

Raw flag counts:
- data_issue_flag: 68
- repeat_pause_signal_10d_ge2: 101
- repeat_pause_signal_10d_ge3: 67
- valid_longer_lookback_thrust_flag: 132
- weak_thrust_only_flag: 30
- no_real_thrust_flag: 45

Top repeat tickers:
| ticker | count_10d | first_signal_date | last_signal_date |
|---|---|---|---|
| WSR | 7 | 2026-05-05 | 2026-06-09 |
| SILA | 6 | 2026-05-05 | 2026-06-22 |
| TWO | 6 | 2026-05-15 | 2026-06-16 |
| RAMP | 5 | 2026-05-27 | 2026-06-22 |
| ASRT | 4 | 2026-05-27 | 2026-06-16 |
| AVNS | 4 | 2026-05-05 | 2026-06-16 |
| CPRX | 4 | 2026-05-27 | 2026-06-16 |
| TBRG | 3 | 2026-05-05 | 2026-06-16 |
| GBTG | 3 | 2026-05-27 | 2026-06-16 |
| TRIN | 3 | 2026-05-27 | 2026-06-16 |

Manual review queue (top 15 by priority; max 8 per class — full queue in CSV):
| priority | ticker | signal_date | class | reason |
|---|---|---|---|---|
| 1 | ACLX | 2026-04-29 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=77.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AIRG | 2026-05-27 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=21.1%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-12 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-15 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-06-08 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-06-09 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 2 | ASRT | 2026-06-08 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | ASRT | 2026-06-15 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | ASRT | 2026-06-16 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=4 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-08 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-15 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-16 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=4 (>=3 stale repeats in 10 trading sessions) |
| 2 | SILA | 2026-05-11 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |

**Hypothesis state (v4.13.77):**
- `H_PAUSE_BC_INVERT` = REJECTED / NOT_CONFIRMED — outlier-driven, threshold-fragile.
- `H_PAUSE_FRESHNESS_COOLDOWN` = CANDIDATE — repeat PAUSE within 10 trading sessions without a fresh thrust underperforms first PAUSE signals. **No production rule shipped.**

## Council Effectiveness

_Diagnostic measurement only — run_date 2026-06-23, spec v1.0. No rule, skill, or schema changes._

Rows analyzed: 2076
Rows matched to council artifacts: 11
Rows with mature T+5: 1810
Rows immature / no-data: 266

### Council vs Actionability Matrix

| actionability | council | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | avg_t20 |
|---|---|---|---|---|---|---|---|
| REJECT | UNKNOWN | 198 | 164 | -1.44% | 43.83% | -6.87% | 7.32% |
| TAKE | UNKNOWN | 12 | 10 | -2.13% | 50.00% | -4.62% | n/a |
| WATCH | APPROVE | 6 | 6 | -0.16% | 50.00% | -3.44% | 1.80% |
| WATCH | REJECT | 5 | 5 | 1.03% | 60.00% | 10.92% | 10.16% |
| WATCH | UNKNOWN | 1855 | 1625 | 0.62% | 51.56% | -0.68% | 4.43% |

### TAKE Challenge Value

| group | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 | avg_t20 | win_rate_t20 |
|---|---|---|---|---|---|---|---|---|
| TAKE_APPROVED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_DOWNGRADED_OR_REJECTED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_NEUTRAL_OR_UNKNOWN_COUNCIL | 12 | 10 | -2.13% | 50.00% | -4.62% | 44.44% | n/a | n/a |

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
| OTHER | 2 | 2 | 2.31% | 100.00% | 9.04% | 50.00% |
| RISK_REWARD_WEAK | 9 | 9 | -0.05% | 44.44% | 2.41% | 75.00% |

### Interpretation

- If council-downgraded TAKE rows underperform approved TAKE rows, council is adding value.
- If council-downgraded TAKE rows outperform, council is too conservative.
- Require n>=30 per comparison bucket before treating this as evidence.

### Operational Quality

- NOT_APPLICABLE rows: 0
- Join failures (NO_MATCH): 2065
- Rows missing trigger_price: 1177
- Rows missing invalidation_price: 1170

## Rule-Readiness Summary

_Report date: 2026-06-23_  
_Evidence run_date: 2026-06-22_  
_Evidence freshness: OK — 1 business day(s) behind report (WARNING if > 1)_  
_Source: DISK:rule_readiness_monitor_latest.csv_  
_Monitor rows: 3_

Rule-Readiness is diagnostic only. It does not change trading rules, position sizing, the actionability skill, the council skill, or the dashboard.

SOURCE_MISSING and REQUIRED_COLUMNS_MISSING rows are tracked for transparency but do not count as independent evidence windows.

A rule should not be changed until the relevant candidate reaches RULE_REVIEW_READY and is manually reviewed.

### Ready for Rule Review

| candidate_rule_id | rule_module | setup_family | spread_t5 | trimmed_spread_t5 | n_smaller_bucket | independent_windows_observed | recommended_action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| H_MB_EXIT_DAY3_FILTER | MB_EXIT | ALL_APPLICABLE | 11.5697 | 10.6994 | 53 | 6 | RULE_REVIEW_READY |
| H_EP_ACTIVE_FADE_RISK | MB_EXIT | EP_ACTIVE_vs_ACTIVE_BURST | 7.1332 | 7.5324 | 65 | 6 | RULE_REVIEW_READY |

### Candidate Hypotheses

| candidate_rule_id | rule_module | setup_family | spread_t5 | trimmed_spread_t5 | n_smaller_bucket | independent_windows_observed | recommended_action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| H_ACTIVE_BURST_MB_EXIT | MB_EXIT | ACTIVE_BURST | 11.4636 | 10.6729 | 38 | 6 | ADD_TO_DIGEST |

### Soft Cautions

_None._

### Source / Evidence Gaps

_None._

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
