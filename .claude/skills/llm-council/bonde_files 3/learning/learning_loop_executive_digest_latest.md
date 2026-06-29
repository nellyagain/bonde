# Bonde Learning Loop Executive Digest — 2026-06-29

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-06-29 02:37 UTC_
_Notebook: v4.14.40 — DATA_ISSUE quarantine on learning-evidence pool; research-only, no trading-rule changes_

## 1. Today's required action
1. **No automatic rule changes.** Any READY/SUPPORTED item from the rule-readiness monitor still requires manual review before patching. (§9 hypothesis tracker / verdict gates)
2. **Review first SLINGSHOT OK-evaluable cohort under H_SLINGSHOT_TARGET_BASIS; no rule change yet.** OK_EVALUABLE rows: **1,497**; rows ≥5 future bars: **3,104**; unique full-plan+price ticker-date rows: **1,049**. (§13)
3. **A1 absence is resolved by the A2-floor audit: V5.9.46 has no distinct mechanical A1 gate. A2 is the mechanical top tier.** A1 is not a mechanical rule problem — monitor A2-floor execution quality and realized outcomes, not A1 reachability. PASS_A2_FLOOR rows: **18**; Post-V5.9.19 TRADE rows: **14**; A1 rows: **0**; A2 rows: **39**. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is alive, low sample (n=158), measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **1**. (§15)
7. **Primary rule-review item: H_EP_ACTIVE_FADE_RISK. Manual review required before any rule change.** No rule change has been auto-applied. Ready: H_EP_ACTIVE_FADE_RISK, H_MB_EXIT_DAY3_FILTER. Candidates: H_ACTIVE_BURST_MB_EXIT. Soft cautions: none. (§RR)
   _Rule-readiness source: rule_readiness_monitor_latest.csv; ID column: candidate_rule_id; monitor rows: 3; non-observe rows: 3._

## 2. Changed since last run — 2026-06-26 07:48 UTC → 2026-06-29 02:37 UTC
- Prior digest date: **2026-06-26**
- Current digest date: **2026-06-29**
- Comparison window: **2026-06-26 → 2026-06-29**

### Current pipeline status
- SLINGSHOT decision-log target/R:R backfilled rows: **1,191**.
- Tiny-geometry hygiene flagged rows: **81**.
- Dedup diagnostics: **2,065** raw full-plan+price rows → **1,049** unique ticker-date rows.
- SLINGSHOT current state: **OK_EVALUABLE rows = 1,497** (non-zero; H_SLINGSHOT_TARGET_BASIS measurement live). Rows ≥5 future bars: 3,104.

### Current trading-state
- Post-V5.9.19 TRADE rows: **14**; A1: **0**; A2: **39**. TRADE path is alive.
- KK confirmation: alive, sample n=158, measurement-only.
- KK funnel audit (`kk_gate_funnel_latest.*`): not present.
- PAUSE reconciliation: main tracker = **WATCHING_NOT_RULE_EVIDENCE**; diagnostic = **REJECTED / NOT_CONFIRMED**.
- Realized P&L: `n_with_realized_r` = **1** (threshold 30).

### Rule-readiness state
- **2** READY/SUPPORTED item(s) — manual review required: H_EP_ACTIVE_FADE_RISK, H_MB_EXIT_DAY3_FILTER. Candidates: 1. Soft cautions: 0.

### Deltas vs prior run
- SLINGSHOT OK_EVALUABLE rows: **1,497** (prior 1,427, Δ +70).
- SLINGSHOT rows ≥5 future bars: **3,104** (prior 2,951, Δ +153).
- Post-V5.9.19 TRADE rows: **14** (prior 14, Δ +0).
- A1 rows: **0** (prior 0, Δ +0).
- A2 rows: **39** (prior 38, Δ +1).
- TRADE row identity: unchanged (n=14).
- Rule-readiness READY/SUPPORTED ids: **2** (prior 2).
- Rule-readiness CANDIDATE ids: **1** (prior 1).
- Rule-readiness SOFT_CAUTION ids: **0** (prior 0).

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.

## 3. Operational status
- Master decision-log rows: **2,786**
- Decision-log source files: **27**
- Latest decision-log sources: `daily_decision_log_2026-06-19.csv`, `daily_decision_log_2026-06-23 (1).csv`, `daily_decision_log_2026-06-25.csv`, `daily_decision_log_2026-06-26.csv`, `daily_decision_log_2026-06-28.csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |   2416 |
| REJECT               |    297 |
| COUNCIL              |     59 |
| TRADE                |     14 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |   1840 |
| REJECT               |    201 |
| COUNCIL              |     34 |
| TRADE                |     14 |

### Corpus reconciliation
- Candidate decision-log files discovered: **39**
- Included decision-log files: **27**
- Excluded decision-log files: **12** (3 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **2,810 → 2,810 → 2,786**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Sugar Baby=True candidates show 0.14% avg T+5 versus 0.21% for non-Sugar Baby candidates (evaluated n=6553 vs 3897). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
2. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
3. A1 has zero post-V5.9.19 rows — RESOLVED by the v4.14.27 A2-floor reachability audit (as of 2026-06-26): A1 has no distinct mechanical gate in V5.9.46; 18 row(s) pass every mechanical gate and are withheld from A1 only by discretionary promotion. A1 emptiness is expected, not a bug.
4. Realized P&L attribution is live but sample-immature: 2 closed realized rows and 1 with realized R. Use it as plumbing proof only until n_with_realized_r >= 30; do not use it for calibration yet.
5. Corpus reconciliation is now active: 12 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
6. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| SLINGSHOT      |     1194 |              765 | ACTIONABLE_SAMPLE |         82.5796 |            62.0979 |         1.43991   |
| PAUSE          |      342 |              284 | ACTIONABLE_SAMPLE |         86.2573 |            63.9676 |         1.13905   |
| ACTIVE_BURST   |      454 |              248 | ACTIONABLE_SAMPLE |         96.9163 |            47.4359 |         1.01482   |
| EP_ACTIVE      |      130 |              125 | ACTIONABLE_SAMPLE |         89.2308 |            42.3423 |         0.0196782 |
| DELAYED_EP     |      120 |               81 | ACTIONABLE_SAMPLE |         92.5    |            61.6438 |         1.50869   |
| ANTICIPATION   |       27 |               25 | ACTIONABLE_SAMPLE |         88.8889 |            45.4545 |         0.273591  |
| PRE_BURST      |       19 |               17 | BUILDING_SAMPLE   |         10.5263 |           100      |         3.27077   |
| EP_SPIKE       |       18 |               15 | BUILDING_SAMPLE   |         94.4444 |            57.1429 |        10.7893    |
| MOMENTUM_PAUSE |        2 |                2 | LOW_SAMPLE        |        100      |           100      |         0.169841  |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_SPIKE       | WATCH_ONLY      | B              | WATCH                |       11 |                9 | LOW_SAMPLE        |            66.6667 |           7.08154 |
| SLINGSHOT      | ACTIONABLE      | A2             | COUNCIL              |       16 |               16 | BUILDING_SAMPLE   |            46.6667 |           5.61375 |
| DELAYED_EP     | WATCH_ONLY      | C              | WATCH                |       23 |               15 | BUILDING_SAMPLE   |            71.4286 |           4.22515 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |       10 |               10 | BUILDING_SAMPLE   |            33.3333 |           3.6796  |
| EP_ACTIVE      | WATCH_ONLY      | B              | WATCH                |       54 |               53 | ACTIONABLE_SAMPLE |            51.0204 |           3.3641  |
| PRE_BURST      | WATCH_ONLY      | B              | WATCH                |       10 |               10 | BUILDING_SAMPLE   |           100      |           3.27077 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |      187 |               86 | ACTIONABLE_SAMPLE |            55.4217 |           2.2019  |
| SLINGSHOT      | WATCH_ONLY      | B              | WATCH                |      608 |              342 | ACTIONABLE_SAMPLE |            70.5882 |           1.64556 |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        7 |                7 | LOW_SAMPLE        |            20      |         -5.16839  |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |       11 |               11 | BUILDING_SAMPLE   |            28.5714 |         -4.75749  |
| EP_ACTIVE      | REJECT          | D              | REJECT               |       30 |               27 | ACTIONABLE_SAMPLE |            28      |         -2.65093  |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       27 |               26 | ACTIONABLE_SAMPLE |            48      |         -1.48957  |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |       11 |               11 | BUILDING_SAMPLE   |            40      |         -0.263395 |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       59 |               47 | ACTIONABLE_SAMPLE |            44.186  |         -0.14024  |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |      193 |              100 | ACTIONABLE_SAMPLE |            42.4242 |          0.26291  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       88 |               57 | ACTIONABLE_SAMPLE |            56      |          0.317341 |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        2 |
| ALL_ROWS       | A2             | COUNCIL              | DELAYED_EP     |        2 |
| ALL_ROWS       | A2             | COUNCIL              | EP_ACTIVE      |        7 |
| ALL_ROWS       | A2             | COUNCIL              | SLINGSHOT      |       19 |
| ALL_ROWS       | A2             | TRADE                | ACTIVE_BURST   |        3 |
| ALL_ROWS       | A2             | TRADE                | DELAYED_EP     |        2 |
| ALL_ROWS       | A2             | TRADE                | EP_ACTIVE      |        1 |
| ALL_ROWS       | A2             | TRADE                | PAUSE          |        2 |
| ALL_ROWS       | A2             | TRADE                | SLINGSHOT      |        6 |
| ALL_ROWS       | A2             | WATCH                | SLINGSHOT      |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | DELAYED_EP     |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | EP_ACTIVE      |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | SLINGSHOT      |       19 |
| POST_V5_9_19   | A2             | TRADE                | ACTIVE_BURST   |        3 |
| POST_V5_9_19   | A2             | TRADE                | DELAYED_EP     |        2 |
| POST_V5_9_19   | A2             | TRADE                | EP_ACTIVE      |        1 |
| POST_V5_9_19   | A2             | TRADE                | PAUSE          |        2 |
| POST_V5_9_19   | A2             | TRADE                | SLINGSHOT      |        6 |
| POST_V5_9_19   | A2             | WATCH                | SLINGSHOT      |        2 |
| LATEST_SESSION | A2             | COUNCIL              | SLINGSHOT      |        1 |

### A2-floor reachability funnel (v4.14.27 audit, as of 2026-06-26)
| gate                          |   rows_entering |   rows_passing |   rows_failed |   rows_not_reconstructable |
|:------------------------------|----------------:|---------------:|--------------:|---------------------------:|
| G00_start_rows                |            2476 |           2476 |             0 |                          0 |
| G01_setup_family_eligible     |            2476 |           1910 |           566 |                          0 |
| G02_actionable_candidate      |            1910 |             62 |          1848 |                          0 |
| G03_entry_and_stop_present    |              62 |             59 |             3 |                          0 |
| G04_planned_rr_present        |              59 |             37 |            22 |                          0 |
| G05_rr_floor_ge_2R            |              37 |             37 |             0 |                          0 |
| G06_long_geometry             |              37 |             37 |             0 |                          0 |
| G07_slingshot_clean_structure |              37 |             22 |            15 |                          0 |
| G09_slingshot_vol_gate        |              22 |             22 |             0 |                          0 |
| G10_catalyst_grade_ok         |              22 |             21 |             1 |                          0 |
| G11_dte_gate                  |              21 |             18 |             0 |                          3 |

- First failed gate per row:
| first_failed_gate                  |   n_rows |
|:-----------------------------------|---------:|
| G02_actionable_candidate           |     1848 |
| G01_setup_family_eligible          |      566 |
| G04_planned_rr_present             |       22 |
| PASS_A2_FLOOR                      |       18 |
| G07_slingshot_clean_structure      |       15 |
| G03_entry_and_stop_present         |        3 |
| NOT_RECONSTRUCTABLE_FROM_48COL_LOG |        3 |
| G10_catalyst_grade_ok              |        1 |

- Conclusion: **18** row(s) pass every mechanical gate (PASS_A2_FLOOR). A1 has no distinct mechanical gate in V5.9.46 — A1/A2 share the gate stack — so A1 emptiness is expected, not a bug. Row-level detail: `a1_near_misses_latest.csv`.
### Current interpretation
- A1 has zero post-V5.9.19 rows — RESOLVED by the v4.14.27 A2-floor reachability audit (as of 2026-06-26): A1 has no distinct mechanical gate in V5.9.46; 18 row(s) pass every mechanical gate and are withheld from A1 only by discretionary promotion. A1 emptiness is expected, not a bug.
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
| SLINGSHOT      | ACTIONABLE      | A2             | COUNCIL              |       16 |               16 | BUILDING_SAMPLE |            46.6667 |          5.61375  |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        7 |                7 | LOW_SAMPLE      |            20      |         -5.16839  |
| SLINGSHOT      | ACTIONABLE      | A2             | TRADE                |        6 |                4 | LOW_SAMPLE      |            50      |         -1.10673  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | TRADE                |        3 |                3 | LOW_SAMPLE      |           100      |          3.05238  |
| DELAYED_EP     | ACTIONABLE      | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |           100      |          5.53459  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        2 |                2 | LOW_SAMPLE      |            50      |          4.79142  |
| DELAYED_EP     | ACTIONABLE      | A2             | TRADE                |        2 |                2 | LOW_SAMPLE      |           100      |          4.53354  |
| SLINGSHOT      | UNKNOWN         | A2             | COUNCIL              |        3 |                2 | LOW_SAMPLE      |            50      |          0.713616 |
| PAUSE          | ACTIONABLE      | A2             | TRADE                |        2 |                2 | LOW_SAMPLE      |           nan      |        nan        |
| SLINGSHOT      | UNKNOWN         | A2             | WATCH                |        2 |                1 | LOW_SAMPLE      |             0      |         -4.20108  |
| EP_ACTIVE      | ACTIONABLE      | A2             | TRADE                |        1 |                1 | LOW_SAMPLE      |           nan      |        nan        |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- A1 absence is explained by the A2-floor reachability funnel above; no further A1 reachability investigation is required unless the funnel changes.

## 7. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **289**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 8. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   | higher_n_eval   | higher_avg_5d   | higher_wr_5d   | lower_label   | lower_n_eval   | lower_avg_5d   | lower_wr_5d   | avg_gap_lower_minus_higher   | linked_hypothesis     | oos_spread   | hypothesis_status                                 |
|:---------------|:---------------|:----------------|:----------------|:---------------|:--------------|:---------------|:---------------|:--------------|:-----------------------------|:----------------------|:-------------|:--------------------------------------------------|
| ~~PAUSE~~      | ~~B~~          | ~~191~~         | ~~1.161~~       | ~~62.65~~      | ~~C~~         | ~~81~~         | ~~1.178~~      | ~~67.61~~     | ~~+0.02~~                    | ~~H_PAUSE_BC_INVERT~~ | ~~-0.03~~    | ~~CLOSED (diagnostic: REJECTED / NOT_CONFIRMED)~~ |

Struck rows: linked hypothesis REJECTED by the diagnostic — shown for auditability, status CLOSED; not a live trigger.
Annotation (v4.14.34 E2-inv): linked_hypothesis/oos_spread/hypothesis_status come from the pre-registered hypothesis tracker and the PAUSE diagnostic verdict; UNTRACKED rows have no pre-registered hypothesis. In-sample inversion is not rule-change evidence; OOS spread drives the verdict.
Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family                         | current_test                                                                               | method_note                                                                                                                                                          | regime_context   |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------------------------|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST                   | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5                                   | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-on          |           100 |         0.26291 |            47 |       -0.14024  |             0.40315   | 2026-05-16       |        61 |        21 |        -0.716103  | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE                      | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5                                      | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-on          |            18 |        -4.91728 |           nan |      nan        |            -4.91728   | 2026-05-16       |         4 |       nan |         2.51199   | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE                          | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                                                  | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-on          |            81 |         1.17822 |           191 |        1.16106  |             0.0171584 | 2026-05-16       |        45 |       120 |        -0.0301484 | WATCHING_NOT_RULE_EVIDENCE |
| H_KK_CONFIRMATION           | ANTICIPATION / KK_CONFIRMATION | Bonde anticipation WITH KK confirmation minus WITHOUT KK confirmation avg T+5 alpha vs SPY | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-on          |             3 |         2.29367 |           155 |        0.438121 |             1.85555   | 2026-05-17       |         2 |       113 |         2.29809   | WATCHING_LOW_SAMPLE        |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **1** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.
### Pre-registered verdict gates
These gates are binding review criteria. A rule patch should not ship unless its hypothesis has a pre-registered SUPPORTED verdict or a separate explicitly documented emergency bug rationale.
| hypothesis_id                  | method_note                                                                                                                                                          | regime_context   | current_state                                                                                                            | required_sample                                                                                                                                      | oos_window                                      | earliest_review                                                                                                       | pre_registered_prediction                                                                                              | supported_if                                                                                                                                                 | rejected_if                                                                                          | ambiguous_if                                                                                                                                             | if_supported                                                                                                                          | if_rejected                                                                         |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:-------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN    | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-on          | current effect 0.40; n_a=100; n_b=47; status=WATCHING_NOT_RULE_EVIDENCE                                                  | OOS n_C >= 30 and n_D >= 30, with mature T+5/T+10/T+20 windows.                                                                                      | 2026-05-16 onward                               | When both OOS slices meet sample and maturity gates.                                                                  | D/REJECT minus C/WATCH spread remains >= +1.5% OOS.                                                                    | OOS spread >= +1.5% and confidence interval / robustness check does not collapse to zero.                                                                    | OOS spread < +0.5% or direction inverts.                                                             | OOS spread is +0.5% to +1.5% or sample composition is unstable.                                                                                          | Draft V5.9.21-G6-SOFTEN spec; do not ship until patch text is reviewed.                                                               | File hypothesis; no Gate6 softening.                                                |
| H_EP_ACTIVE_COUNCIL_TIGHTEN    | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-on          | current effect -4.92; n_a=18; status=WATCHING_LOW_SAMPLE                                                                 | OOS EP_ACTIVE COUNCIL n >= 30 with mature T+5 and at least 10 T+20 rows.                                                                             | 2026-05-16 onward                               | When OOS council-routed EP_ACTIVE rows reach n>=30.                                                                   | EP_ACTIVE COUNCIL average T+5 remains <= -3.0% OOS.                                                                    | OOS avg T+5 <= -3.0% and win rate <= 35% without one-stock distortion.                                                                                       | OOS avg T+5 >= 0% or win rate normalizes above 45%.                                                  | OOS avg T+5 is -3.0% to 0% or driven by one outlier.                                                                                                     | Draft V5.9.21-EPACTIVE-COUNCIL-TIGHTEN review spec.                                                                                   | Keep EP_ACTIVE council routing unchanged.                                           |
| H_PAUSE_BC_INVERT              | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-on          | current effect 0.02; n_a=81; n_b=191; status=WATCHING_NOT_RULE_EVIDENCE                                                  | OOS PAUSE B/WATCH n >= 30 and PAUSE C/WATCH n >= 30.                                                                                                 | 2026-05-16 onward                               | When both OOS PAUSE slices hit n>=30 and T+5 is mature.                                                               | PAUSE C/WATCH minus B/WATCH spread remains >= +1.5% OOS.                                                               | OOS spread >= +1.5% and persists after removing tiny/liquidity outliers.                                                                                     | OOS spread < +0.5% or B resumes leadership.                                                          | OOS spread is +0.5% to +1.5% or sample is too concentrated.                                                                                              | Draft V5.9.21-PAUSE-RANK-REVIEW spec; do not change B/C labels before review.                                                         | Keep PAUSE B/C rank mapping unchanged.                                              |
| H_KK_CONFIRMATION              | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-on          | current effect 1.86; n_a=3; n_b=155; status=WATCHING_LOW_SAMPLE                                                          | OOS n >= 30 confirmed AND n >= 30 unconfirmed Bonde anticipation rows with mature T+5 outcomes; both cohorts must satisfy signal_date >= 2026-05-17. | 2026-05-17 onward                               | When both confirmed and unconfirmed cohorts reach n>=30 with mature T+5; component regression only at n>=100 KK rows. | Confirmed cohort T+5 alpha vs SPY exceeds unconfirmed cohort by at least +0.50 percentage points.                      | T+5 alpha spread >= +0.50 pp, T+10 or T+20 confirms direction, no single ticker >40% of spread, weekly consistency >=60%, and bootstrap_supported_pct >=80%. | T+5 alpha spread <= 0 or unconfirmed cohort outperforms after sample gates.                          | T+5 alpha spread is 0 to +0.50 pp, multi-horizon direction is mixed, ticker/week concentration is excessive, or bootstrap robustness is below threshold. | Use KK confirmation as Layer 5 priority/confidence signal only; do not hard-reject unconfirmed Bonde rows.                            | Deprecate KK confirmation in Layer 5 decisions; keep KK fields as diagnostics only. |
| H_SLINGSHOT_TARGET_BASIS       | Measure SLINGSHOT_PRIMARY full-plan unique ticker-date rows for R:R>=2.0 and later T+5 expectancy after evaluability gates pass.                                     | Risk-on          | 2,065 raw full-plan+price rows; 1,049 unique full-plan+price ticker-date rows; 692 unique OK_EVALUABLE ticker-date rows. | unique_ok_evaluable_ticker_date_rows >= 30 and at least 10 OOS rows after 2026-05-22.                                                                | Starts 2026-05-22                               | When unique OK_EVALUABLE ticker-date rows reach n>=30.                                                                | >=40% of SLINGSHOT_PRIMARY full-plan unique ticker-date rows clear V5.9 R:R floor >= 2.0.                              | R:R>=2.0 pass rate >=40% and T+5 expectancy is not worse than ACTIVE_BURST baseline.                                                                         | R:R>=2.0 pass rate <30% or T+5 expectancy materially underperforms ACTIVE_BURST.                     | R:R pass rate is 30–40% or expectancy is positive but under-sampled.                                                                                     | Keep SLINGSHOT measurement path live; consider later context/ranking overlay only after 100+ unique OK_EVALUABLE rows.                | Do not promote SLINGSHOT; review target-basis and detection criteria.               |
| H_SUGAR_BABIES_CONTEXT_OVERLAY | Compare Sugar Baby=True vs False rows by mature T+5, then require OOS and family-level confirmation before any ranking-context boost.                                | Risk-on          | Sugar Baby=True candidates show 0.14% avg T+5 versus 0.21% for non-Sugar Baby candidates (evaluated n=6553 vs 3897).     | OOS >= 100 evaluated Sugar=True and >= 100 Sugar=False rows, plus at least two setup families with n>=30.                                            | Next mature weekly cohorts after current digest | When OOS rows and family spread requirements are met.                                                                 | Sugar=True retains >= +1.0% avg T+5 spread over Sugar=False without worsening win-rate materially.                     | OOS avg spread >= +1.0% and at least two families have non-negative confirmation.                                                                            | OOS spread < +0.25% or driven by one family only.                                                    | OOS spread +0.25% to +1.0% or family split is mixed.                                                                                                     | Draft Sugar Babies ranking_context_score proposal; cannot override R:R, DTE, hard rejects, failed EP, dilution/offering, or bad data. | Keep Sugar Babies as monitoring-only context.                                       |
| H_REALIZED_PNL_CORRELATION     | Compare actual broker realized R/P&L against system setup/action/final-status slices once n_with_realized_r >= 30.                                                   | Risk-on          | 1 realized-R rows; threshold not met.                                                                                    | n_with_realized_r >= 30 total, then >=10 per major setup/action slice before slice-level claims.                                                     | Broker-export rows as they arrive               | When realized-R count reaches n>=30.                                                                                  | Layer 5 realized-R selection should outperform raw WATCH/COUNCIL forward-return expectancy on comparable setup slices. | Realized R is positive overall and aligns with the strongest forward-return slices.                                                                          | Realized R is negative despite positive forward-return slices, implying execution/selection failure. | Positive P&L but too concentrated in one trade or mismatch between broker rows and system rows.                                                          | Use realized-R weighting in weekly system review; do not change signal rules solely from P&L.                                         | Prioritize execution/selection review before signal-rule changes.                   |

### PAUSE reconciliation (v4.14.06)
- Main tracker status: **WATCHING_NOT_RULE_EVIDENCE**.
- PAUSE diagnostic status: **REJECTED / NOT_CONFIRMED**.
- Interpretation: PAUSE B/C inversion remains tracked in the broad hypothesis table, but current PAUSE diagnostic evidence does not confirm a rule-change-ready inversion.

### KK summary (v4.14.06)
- KK confirmation: alive, low sample (n=158), measurement-only.
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
| H_KK_CONFIRMATION | WATCHING_LOW_SAMPLE | True                 |                3 |                155 |                     1.85555 |                                      0.5 |                       nan |                                  80 |                      100 |                          11.2123 |                                  0 |

**Current cohort split (cumulative, in-sample baseline):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |      168 |              155 |         0.358644 |              0.438121 |               123 |          1.1613   |                68 |          1.20923  |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        3 |                3 |         0.902316 |              2.29367  |                 3 |          0.479186 |                 1 |         -0.256168 |

**Strict OOS cohort split (signal_date >= 2026-05-17; drives verdict):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |      124 |              113 |         0.469941 |              0.957969 |                83 |           1.23359 |                32 |           1.72995 |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        2 |                2 |         0.731373 |              3.25606  |                 2 |           0.40773 |                 0 |         nan       |

**KK classification audit sample:**
_Row table suppressed until n>=10/slice; current confirmed n=2, distinct flag patterns=47._
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
| LOCO     | DELAYED_EP     | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| SEZL     | DELAYED_EP     | CANCEL            | RESOLVED         | LOSER           | ALIGNED                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| CLSK     | SLINGSHOT      | CANCEL            | RESOLVED         | WINNER          | MISALIGNED                  | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| IFS      | SLINGSHOT      | DEFER             | RESOLVED         | WINNER          | MISALIGNED                  | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| CGCT     | SLINGSHOT      | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=NO_PRICE_DATA; available_future_bars=26; OUTCOME_PENDING_NO_PRICE_DATA |
| LLY      | SLINGSHOT      | DEFER             | RESOLVED         | WINNER          | MISALIGNED                  | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| KGS      | PAUSE          | DEFER             | RESOLVED         | LOSER           | ALIGNED                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| EFC      | PAUSE          | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |
| KEX      | PAUSE          | DEFER             | RESOLVED         | AMBIGUOUS       | NEUTRAL                     | OUTCOME_JOIN_FALLBACK_DIRECT_PRICE_EVAL: status=EVALUATED_FULL; available_future_bars=26                               |


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
- Source-capable coverage minimum: **93.4%**
- All-row coverage minimum, legacy rows included: **70.9%**
- Source-capable field statuses:
| field                   |   coverage_pct | status   |
|:------------------------|---------------:|:---------|
| day1_close_pct_in_range |           93.7 | OK       |
| day1_move_pct           |           93.4 | OK       |
| day1_vol_ratio          |           93.5 | OK       |

- Day-1 verdict summary:
| verdict                      |   rows |
|:-----------------------------|-------:|
| INSUFFICIENT_RESOLVED_SAMPLE |      4 |


## 13. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. Measurement only; no SLINGSHOT rule-change evidence yet.
- Rows: **4,169**; full-plan proxy rows: **2,808**; rows with ≥5 future bars: **3,104**; OK-evaluable rows: **1,497**.
- DECISION_LOG rows target/R:R enriched inside learning loop from universe planning fields: **1,191**
- Entry-source classification (v4.13.73): **CAPTURED_AT_TRIGGER=3,984** (verdict-eligible pool, gated on T+5 maturity); BACKFILLED_FROM_SIGNAL_CLOSE=178 (robustness panel only, excluded from verdict); MISSING_ENTRY_UNRECOVERABLE=7 (excluded).
- Latest pack health: `2026-06-26` **262/262** rows CAPTURED_AT_TRIGGER (entry capture healthy).
- Top missing/evaluability reasons:
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| OK_EVALUABLE             |   1497 |
| NO_PRICE_DATA            |   1291 |
| INSUFFICIENT_FUTURE_BARS |    906 |
| MISSING_ENTRY            |    185 |
| MISSING_TARGET           |    155 |

- Full detail retained in: `slingshot_evaluability_audit_latest.md/csv`, `slingshot_scope_price_diagnostics_latest.md`, `slingshot_hygiene_diagnostics_latest.md`, and the corresponding summary CSVs.
- Interpretation: missing R:R is a field/evaluability issue, not zero R:R or negative SLINGSHOT expectancy.
- Bucket-distribution snapshot available in SLINGSHOT diagnostics exports; omitted here for compactness.

## 14. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Current read: Sugar Baby=True candidates show 0.14% avg T+5 versus 0.21% for non-Sugar Baby candidates (evaluated n=6553 vs 3897).
- Interpretation: Sugar Babies currently has broader sample support than EP9M for a future `ranking_context_score` contribution, but still needs out-of-sample / mature-week validation before any non-zero boost.
- Sugar Babies ticker lookup rows: **595**
### Sugar Baby vs non-Sugar Baby
| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     7771 |                6553 |             0.140822 |               48.3137 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     6926 |                5840 |             0.365983 |               48.887  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     4882 |                3897 |             0.20726  |               52.04   | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     4303 |                3449 |             0.354973 |               52.6819 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Recurrence buckets
| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 0             |     4303 |                3449 |             0.354973 |               52.6819 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      599 |                 458 |             0.361426 |               50.655  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      413 |                 342 |             0.780929 |               53.5088 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      445 |                 372 |            -0.261587 |               48.9247 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 8+            |     5469 |                4668 |             0.386041 |               48.3719 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Setup-family × Sugar Baby=True
| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     6028 |                5061 |             0.144989 |               47.9352 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      567 |                 504 |            -1.05282  |               40.4762 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |      447 |                 369 |             2.01632  |               57.9946 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |      260 |                 193 |             0.671212 |               63.2124 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      203 |                 190 |            -1.23131  |               43.6842 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |      169 |                 156 |            -0.349493 |               42.9487 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       70 |                  55 |             2.06933  |               54.5455 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |       17 |                  16 |             1.88829  |               93.75   | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        9 |                   8 |            -1.20912  |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
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
| priority   | item                                                  | why                                                                                                                                                                                                                                                       |
|:-----------|:------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1         | Realized-P&L correlation check                        | Once n_with_realized_r >= 30, compare realized R by setup_family/action_label/final_trade_status against learning-loop forward-return expectancy. This is the key bridge between signal quality and actual trading quality.                               |
| P1         | Investigate reject/watch and B/C/D inversion          | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.                                                                                                              |
| P1         | Track pre-registered rule-change hypotheses           | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, H_PAUSE_BC_INVERT, and H_KK_CONFIRMATION daily with OOS and realized-R gates before any rule patch.                                                                                     |
| P1         | Accumulate KK confirmation cohorts                    | Keep H_KK_CONFIRMATION unchanged until n>=30 confirmed and n>=30 unconfirmed rows have mature T+5 outcomes.                                                                                                                                               |
| P2         | Sugar Babies validation                               | Candidate for first ranking_context_score contribution, but validate out-of-sample and by setup family before non-zero boost.                                                                                                                             |
| P1         | Keep SLINGSHOT target/R:R enrichment in learning loop | Learning loop backfilled 1191 DECISION_LOG row(s) from diagnostic/skill-pack planning fields. Actionability skill remains stable; continue measurement-layer enrichment from universe outputs until the raw decision-log schema is intentionally revised. |
| P2         | SLINGSHOT hygiene verification                        | Before first OK_EVALUABLE rows mature, review tiny-geometry flags, duplicate ticker-date rows, and backfill-source attribution in `slingshot_hygiene_diagnostics_latest.md`.                                                                              |

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

Rows analyzed: 344
Data issue rows: 82
Repeat stale rows: 56
Valid 20-bar thrust rows: 73
Valid longer-lookback thrust rows: 57
Weak-thrust-only rows: 31
No-real-thrust rows: 44
Insufficient-price-data rows: 1

Raw flag counts:
- data_issue_flag: 82
- repeat_pause_signal_10d_ge2: 118
- repeat_pause_signal_10d_ge3: 84
- valid_longer_lookback_thrust_flag: 156
- weak_thrust_only_flag: 31
- no_real_thrust_flag: 45

Top repeat tickers:
| ticker | count_10d | first_signal_date | last_signal_date |
|---|---|---|---|
| WSR | 7 | 2026-05-05 | 2026-06-09 |
| SILA | 6 | 2026-05-05 | 2026-06-26 |
| TWO | 6 | 2026-05-15 | 2026-06-16 |
| RAMP | 5 | 2026-05-27 | 2026-06-24 |
| TBRG | 5 | 2026-05-05 | 2026-06-26 |
| AVNS | 4 | 2026-05-05 | 2026-06-26 |
| CPRX | 4 | 2026-05-27 | 2026-06-26 |
| CCRN | 4 | 2026-05-27 | 2026-06-26 |
| OGN | 4 | 2026-05-27 | 2026-06-26 |
| ASRT | 4 | 2026-05-27 | 2026-06-16 |

Manual review queue (top 15 by priority; max 8 per class — full queue in CSV):
| priority | ticker | signal_date | class | reason |
|---|---|---|---|---|
| 1 | ACLX | 2026-04-29 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=77.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AIRG | 2026-05-27 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=21.1%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | ALOT | 2026-06-26 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APGE | 2026-06-26 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=46.7%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-12 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-15 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 2 | ASRT | 2026-06-08 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | ASRT | 2026-06-15 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | ASRT | 2026-06-16 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=4 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-08 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-15 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-16 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=4 (>=3 stale repeats in 10 trading sessions) |
| 2 | CPRX | 2026-06-23 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |

**Hypothesis state (v4.13.77):**
- `H_PAUSE_BC_INVERT` = REJECTED / NOT_CONFIRMED — outlier-driven, threshold-fragile.
- `H_PAUSE_FRESHNESS_COOLDOWN` = CANDIDATE — repeat PAUSE within 10 trading sessions without a fresh thrust underperforms first PAUSE signals. **No production rule shipped.**

## Council Effectiveness

_Diagnostic measurement only — run_date 2026-06-29, spec v1.0. No rule, skill, or schema changes._

Rows analyzed: 2786
Rows matched to council artifacts: 11
Rows with mature T+5: 2058
Rows immature / no-data: 728

### Council vs Actionability Matrix

| actionability | council | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | avg_t20 |
|---|---|---|---|---|---|---|---|
| REJECT | UNKNOWN | 297 | 198 | -0.01% | 43.88% | -6.25% | 0.17% |
| TAKE | UNKNOWN | 14 | 12 | -2.33% | 41.67% | -4.34% | -2.79% |
| WATCH | APPROVE | 6 | 6 | -0.16% | 50.00% | -0.80% | 1.80% |
| WATCH | REJECT | 5 | 5 | 1.03% | 60.00% | 10.92% | 10.16% |
| WATCH | UNKNOWN | 2464 | 1837 | 0.73% | 52.37% | -0.09% | 3.27% |

### TAKE Challenge Value

| group | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 | avg_t20 | win_rate_t20 |
|---|---|---|---|---|---|---|---|---|
| TAKE_APPROVED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_DOWNGRADED_OR_REJECTED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_NEUTRAL_OR_UNKNOWN_COUNCIL | 14 | 12 | -2.33% | 41.67% | -4.34% | 40.00% | -2.79% | 55.56% |

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
| RISK_REWARD_WEAK | 9 | 9 | -0.05% | 44.44% | 3.52% | 77.78% |

### Interpretation

- If council-downgraded TAKE rows underperform approved TAKE rows, council is adding value.
- If council-downgraded TAKE rows outperform, council is too conservative.
- Require n>=30 per comparison bucket before treating this as evidence.

### Operational Quality

- NOT_APPLICABLE rows: 0
- Join failures (NO_MATCH): 2775
- Rows missing trigger_price: 1455
- Rows missing invalidation_price: 1453

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
