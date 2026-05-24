# Bonde Learning Loop Executive Digest — 2026-05-24

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-05-24 10:24 UTC_
_Notebook: v4.13.74 (digest surfaces entry-source classification)_

## 1. Today's required action
1. **No rule changes.** (§9 hypothesis tracker / verdict gates — all monitoring-only, no SUPPORTED verdicts)
2. **Wait for SLINGSHOT future bars.** Earliest T+5 maturity: **2026-05-22**. (§13)
3. **Watch A1/A2 zero-TRADE issue.** Confirm whether A1 is intentionally rare or unreachable and whether clean A1/A2 rows are over-routed. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is now pre-registered and measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **2**. (§15)

## 2. Changed since last run — 2026-05-24 06:13 UTC → 2026-05-24 10:24 UTC
- Prior digest date: **2026-05-24**
- Current digest date: **2026-05-24**
- Comparison window: **2026-05-24 → 2026-05-24**

### Pipeline changes
- SLINGSHOT decision-log target/R:R backfilled inside the learning loop: **151** rows.
- Tiny-geometry hygiene audit added / active: **30** rows flagged.
- Dedup diagnostics active: **343** raw full-plan+price rows → **157** unique ticker-date rows.
- Backfill source attribution simplified to `slingshot_backfill_source` enum.
- KK confirmation research layer added: `H_KK_CONFIRMATION` computes cohorts in the learning loop without changing upstream signals.

### Data changes
- No new hypothesis verdicts crossed a rule-change threshold.
- No Day-1 shape verdicts crossed threshold.
- Realized P&L remains sample-immature: `n_with_realized_r` = **2**.

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.
- SLINGSHOT `OK_EVALUABLE` rows remain 0 until future bars mature.

## 3. Operational status
- Master decision-log rows: **971**
- Decision-log source files: **12**
- Latest decision-log sources: `daily_decision_log_2026-05-18.csv`, `daily_decision_log_2026-05-21 (2).csv`, `daily_decision_log_2026-05-22.csv`, `daily_decision_log_2026-05-23.csv`, `sample_daily_decision_log.csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    819 |
| REJECT               |    105 |
| COUNCIL              |     45 |
| TRADE                |      2 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    219 |
| COUNCIL              |     16 |
| REJECT               |      5 |
| TRADE                |      1 |

### Corpus reconciliation
- Candidate decision-log files discovered: **20**
- Included decision-log files: **13**
- Excluded decision-log files: **7** (7 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **1,020 → 995 → 971**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Sugar Baby=True candidates show 0.33% avg T+5 versus -1.37% for non-Sugar Baby candidates (evaluated n=2020 vs 1137). This is currently the stronger candidate for a future ranking overlay than EP9M, but still needs out-of-sample/weekly validation.
2. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
3. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
4. Realized P&L attribution is live but sample-immature: 2 closed realized rows and 2 with realized R. Use it as plumbing proof only until n_with_realized_r >= 30; do not use it for calibration yet.
5. Corpus reconciliation is now active: 7 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
6. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| ACTIVE_BURST   |      113 |              103 | ACTIONABLE_SAMPLE |         94.6903 |            37.7551 |        -1.0739    |
| SLINGSHOT      |      196 |               63 | ACTIONABLE_SAMPLE |         96.9388 |            35      |        -1.53152   |
| PAUSE          |       88 |               56 | ACTIONABLE_SAMPLE |         89.7727 |            50      |         1.163     |
| EP_ACTIVE      |       49 |               36 | ACTIONABLE_SAMPLE |         89.7959 |            48.4848 |        -0.46265   |
| DELAYED_EP     |       33 |               19 | BUILDING_SAMPLE   |         90.9091 |            58.8235 |        -1.09932   |
| ANTICIPATION   |       11 |                8 | LOW_SAMPLE        |        100      |            50      |        -0.0866923 |
| PRE_BURST      |        5 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |
| MOMENTUM_BURST |        1 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| EP_ACTIVE      | WATCH_ONLY      | B              | WATCH                |       10 |                5 | LOW_SAMPLE        |            60      |          7.58384  |
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       31 |               18 | BUILDING_SAMPLE   |            66.6667 |          2.77643  |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       31 |               26 | ACTIONABLE_SAMPLE |            50      |          2.67481  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        6 |                6 | LOW_SAMPLE        |            50      |          1.25906  |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       56 |               37 | ACTIONABLE_SAMPLE |            39.3939 |          0.313392 |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        7 |                5 | LOW_SAMPLE        |            25      |          0.210662 |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        7 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       15 |                9 | LOW_SAMPLE        |            62.5    |         -0.7628   |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| SLINGSHOT      | REJECT          | D              | REJECT               |        5 |                5 | LOW_SAMPLE        |             0      |          -7.81828 |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        6 |                5 | LOW_SAMPLE        |             0      |          -7.29049 |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |        8 |                7 | LOW_SAMPLE        |            40      |          -6.22877 |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       29 |               26 | ACTIONABLE_SAMPLE |            30.7692 |          -4.09441 |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       19 |               16 | BUILDING_SAMPLE   |            50      |          -1.76348 |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       39 |               39 | ACTIONABLE_SAMPLE |            35.8974 |          -1.7631  |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |       92 |               53 | ACTIONABLE_SAMPLE |            34      |          -1.29779 |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       15 |                9 | LOW_SAMPLE        |            62.5    |          -0.7628  |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A1             | TRADE                | ACTIVE_BURST   |        1 |
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        6 |
| ALL_ROWS       | A2             | COUNCIL              | DELAYED_EP     |        5 |
| ALL_ROWS       | A2             | COUNCIL              | EP_ACTIVE      |        6 |
| ALL_ROWS       | A2             | TRADE                | DELAYED_EP     |        1 |
| POST_V5_9_19   | A2             | COUNCIL              | DELAYED_EP     |        2 |
| POST_V5_9_19   | A2             | COUNCIL              | EP_ACTIVE      |        1 |
| POST_V5_9_19   | A2             | TRADE                | DELAYED_EP     |        1 |
| LATEST_SESSION | A2             | TRADE                | DELAYED_EP     |        1 |

### Current interpretation
- A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
### Council A1/A2 reachability audit
- Source: `council_reachability_audit_*.csv` from the Council skill. Diagnostic only; does not change labels or trading rules.
| A1_REACHABLE   | A2_EXECUTABLE_REACHABLE   | ZERO_TRADE_CAUSE   |   n_A1 |   n_A2 |   n_TRADE |   n_A2_to_COUNCIL |
|:---------------|:--------------------------|:-------------------|-------:|-------:|----------:|------------------:|
| NOT_EVALUABLE  | NOT_EVALUABLE             | NOT_EVALUABLE      |      0 |      1 |         0 |                 1 |

- Latest reachability audit source: `/content/bonde_repo/bonde_screener_cache/council_queues/council_reachability_audit_2026-05-22.csv`
- Top Council demotion reasons from latest audit:
| demotion_reason                                                                      |   rows |
|:-------------------------------------------------------------------------------------|-------:|
| UNKNOWN                                                                              |      1 |
| A2_COUNCIL_REQUEST explicit council route (Trigger 1)                                |      1 |
| rr_floor_fail static R:R 0.58 vs 2.0 floor; B+/C1 wide Day-1 range capped ATH target |      1 |

### A1/A2 forward-return slices
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d   |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:----------------|-------------------:|------------------:|
| ACTIVE_BURST   | ACTIONABLE      | A1             | TRADE                |        1 |                1 | LOW_SAMPLE      |             0      |         -0.101009 |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        6 |                6 | LOW_SAMPLE      |            50      |          1.25906  |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        6 |                5 | LOW_SAMPLE      |             0      |         -7.29049  |
| DELAYED_EP     | ACTIONABLE      | A2             | COUNCIL              |        5 |                4 | LOW_SAMPLE      |            66.6667 |          1.10798  |
| DELAYED_EP     | ACTIONABLE      | A2             | TRADE                |        1 |                0 | PARTIAL_OUTCOME |           nan      |        nan        |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- If A1 remains absent post-V5.9.19, test whether criteria are intentionally rare or unreachable.

## 7. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **160**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 8. Action-label / reject-vs-watch inversion watchlist
Lower-quality labels outperforming higher-quality labels within the same family are investigation triggers, not rule-change evidence.
| setup_family   | higher_label   |   higher_n_eval |   higher_avg_5d |   higher_wr_5d | lower_label   |   lower_n_eval |   lower_avg_5d |   lower_wr_5d |   avg_gap_lower_minus_higher |
|:---------------|:---------------|----------------:|----------------:|---------------:|:--------------|---------------:|---------------:|--------------:|-----------------------------:|
| PAUSE          | B              |              37 |        0.313392 |        39.3939 | C             |             18 |        2.77643 |       66.6667 |                      2.46304 |
| ACTIVE_BURST   | C              |              26 |       -4.09441  |        30.7692 | D             |             39 |       -1.7631  |       35.8974 |                      2.33131 |

Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family                         | current_test                                                                               | method_note                                                                                                                                                          | regime_context   |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------------------------|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST                   | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5                                   | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-On          |            39 |       -1.7631   |            26 |       -4.09441  |               2.33131 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE                      | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5                                      | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-On          |            12 |       -6.67115  |           nan |      nan        |              -6.67115 | 2026-05-16       |         0 |       nan |               nan | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE                          | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                                                  | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-On          |            18 |        2.77643  |            37 |        0.313392 |               2.46304 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_KK_CONFIRMATION           | ANTICIPATION / KK_CONFIRMATION | Bonde anticipation WITH KK confirmation minus WITHOUT KK confirmation avg T+5 alpha vs SPY | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-On          |             1 |        0.368891 |            42 |       -0.960518 |               1.32941 | 2026-05-17       |         0 |         0 |               nan | WATCHING_LOW_SAMPLE        |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **1** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.
### Pre-registered verdict gates
These gates are binding review criteria. A rule patch should not ship unless its hypothesis has a pre-registered SUPPORTED verdict or a separate explicitly documented emergency bug rationale.
| hypothesis_id                  | method_note                                                                                                                                                          | regime_context   | current_state                                                                                                         | required_sample                                                                                                                                      | oos_window                                      | earliest_review                                                                                                       | pre_registered_prediction                                                                                              | supported_if                                                                                                                                                 | rejected_if                                                                                          | ambiguous_if                                                                                                                                             | if_supported                                                                                                                          | if_rejected                                                                         |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN    | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-On          | current effect 2.33; n_a=39; n_b=26; status=WATCHING_NOT_RULE_EVIDENCE                                                | OOS n_C >= 30 and n_D >= 30, with mature T+5/T+10/T+20 windows.                                                                                      | 2026-05-16 onward                               | When both OOS slices meet sample and maturity gates.                                                                  | D/REJECT minus C/WATCH spread remains >= +1.5% OOS.                                                                    | OOS spread >= +1.5% and confidence interval / robustness check does not collapse to zero.                                                                    | OOS spread < +0.5% or direction inverts.                                                             | OOS spread is +0.5% to +1.5% or sample composition is unstable.                                                                                          | Draft V5.9.21-G6-SOFTEN spec; do not ship until patch text is reviewed.                                                               | File hypothesis; no Gate6 softening.                                                |
| H_EP_ACTIVE_COUNCIL_TIGHTEN    | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-On          | current effect -6.67; n_a=12; status=WATCHING_LOW_SAMPLE                                                              | OOS EP_ACTIVE COUNCIL n >= 30 with mature T+5 and at least 10 T+20 rows.                                                                             | 2026-05-16 onward                               | When OOS council-routed EP_ACTIVE rows reach n>=30.                                                                   | EP_ACTIVE COUNCIL average T+5 remains <= -3.0% OOS.                                                                    | OOS avg T+5 <= -3.0% and win rate <= 35% without one-stock distortion.                                                                                       | OOS avg T+5 >= 0% or win rate normalizes above 45%.                                                  | OOS avg T+5 is -3.0% to 0% or driven by one outlier.                                                                                                     | Draft V5.9.21-EPACTIVE-COUNCIL-TIGHTEN review spec.                                                                                   | Keep EP_ACTIVE council routing unchanged.                                           |
| H_PAUSE_BC_INVERT              | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-On          | current effect 2.46; n_a=18; n_b=37; status=WATCHING_NOT_RULE_EVIDENCE                                                | OOS PAUSE B/WATCH n >= 30 and PAUSE C/WATCH n >= 30.                                                                                                 | 2026-05-16 onward                               | When both OOS PAUSE slices hit n>=30 and T+5 is mature.                                                               | PAUSE C/WATCH minus B/WATCH spread remains >= +1.5% OOS.                                                               | OOS spread >= +1.5% and persists after removing tiny/liquidity outliers.                                                                                     | OOS spread < +0.5% or B resumes leadership.                                                          | OOS spread is +0.5% to +1.5% or sample is too concentrated.                                                                                              | Draft V5.9.21-PAUSE-RANK-REVIEW spec; do not change B/C labels before review.                                                         | Keep PAUSE B/C rank mapping unchanged.                                              |
| H_KK_CONFIRMATION              | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-On          | current effect 1.33; n_a=1; n_b=42; status=WATCHING_LOW_SAMPLE                                                        | OOS n >= 30 confirmed AND n >= 30 unconfirmed Bonde anticipation rows with mature T+5 outcomes; both cohorts must satisfy signal_date >= 2026-05-17. | 2026-05-17 onward                               | When both confirmed and unconfirmed cohorts reach n>=30 with mature T+5; component regression only at n>=100 KK rows. | Confirmed cohort T+5 alpha vs SPY exceeds unconfirmed cohort by at least +0.50 percentage points.                      | T+5 alpha spread >= +0.50 pp, T+10 or T+20 confirms direction, no single ticker >40% of spread, weekly consistency >=60%, and bootstrap_supported_pct >=80%. | T+5 alpha spread <= 0 or unconfirmed cohort outperforms after sample gates.                          | T+5 alpha spread is 0 to +0.50 pp, multi-horizon direction is mixed, ticker/week concentration is excessive, or bootstrap robustness is below threshold. | Use KK confirmation as Layer 5 priority/confidence signal only; do not hard-reject unconfirmed Bonde rows.                            | Deprecate KK confirmation in Layer 5 decisions; keep KK fields as diagnostics only. |
| H_SLINGSHOT_TARGET_BASIS       | Measure SLINGSHOT_PRIMARY full-plan unique ticker-date rows for R:R>=2.0 and later T+5 expectancy after evaluability gates pass.                                     | Risk-On          | 343 raw full-plan+price rows; 157 unique full-plan+price ticker-date rows; 22 unique OK_EVALUABLE ticker-date rows.   | unique_ok_evaluable_ticker_date_rows >= 30 and at least 10 OOS rows after 2026-05-22.                                                                | Starts 2026-05-22                               | When unique OK_EVALUABLE ticker-date rows reach n>=30.                                                                | >=40% of SLINGSHOT_PRIMARY full-plan unique ticker-date rows clear V5.9 R:R floor >= 2.0.                              | R:R>=2.0 pass rate >=40% and T+5 expectancy is not worse than ACTIVE_BURST baseline.                                                                         | R:R>=2.0 pass rate <30% or T+5 expectancy materially underperforms ACTIVE_BURST.                     | R:R pass rate is 30–40% or expectancy is positive but under-sampled.                                                                                     | Keep SLINGSHOT measurement path live; consider later context/ranking overlay only after 100+ unique OK_EVALUABLE rows.                | Do not promote SLINGSHOT; review target-basis and detection criteria.               |
| H_SUGAR_BABIES_CONTEXT_OVERLAY | Compare Sugar Baby=True vs False rows by mature T+5, then require OOS and family-level confirmation before any ranking-context boost.                                | Risk-On          | Sugar Baby=True candidates show 0.33% avg T+5 versus -1.37% for non-Sugar Baby candidates (evaluated n=2020 vs 1137). | OOS >= 100 evaluated Sugar=True and >= 100 Sugar=False rows, plus at least two setup families with n>=30.                                            | Next mature weekly cohorts after current digest | When OOS rows and family spread requirements are met.                                                                 | Sugar=True retains >= +1.0% avg T+5 spread over Sugar=False without worsening win-rate materially.                     | OOS avg spread >= +1.0% and at least two families have non-negative confirmation.                                                                            | OOS spread < +0.25% or driven by one family only.                                                    | OOS spread +0.25% to +1.0% or family split is mixed.                                                                                                     | Draft Sugar Babies ranking_context_score proposal; cannot override R:R, DTE, hard rejects, failed EP, dilution/offering, or bad data. | Keep Sugar Babies as monitoring-only context.                                       |
| H_REALIZED_PNL_CORRELATION     | Compare actual broker realized R/P&L against system setup/action/final-status slices once n_with_realized_r >= 30.                                                   | Risk-On          | 2 realized-R rows; threshold not met.                                                                                 | n_with_realized_r >= 30 total, then >=10 per major setup/action slice before slice-level claims.                                                     | Broker-export rows as they arrive               | When realized-R count reaches n>=30.                                                                                  | Layer 5 realized-R selection should outperform raw WATCH/COUNCIL forward-return expectancy on comparable setup slices. | Realized R is positive overall and aligns with the strongest forward-return slices.                                                                          | Realized R is negative despite positive forward-return slices, implying execution/selection failure. | Positive P&L but too concentrated in one trade or mismatch between broker rows and system rows.                                                          | Use realized-R weighting in weekly system review; do not change signal rules solely from P&L.                                         | Prioritize execution/selection review before signal-rule changes.                   |

### KK confirmation study
Research-only: tests whether Bonde anticipation rows with KK leadership-quality confirmation outperform Bonde anticipation rows without KK confirmation. This does not alter trading labels, ranking, R:R, or hard gates.
**Operational definition:** `kk_research_confirmation = kk_extend_score >= 70 AND (kk_leadership_score >= 70 OR kk_group_strength_score >= 50) AND all KK hard-disqualifier flags are false except kk_pause_too_long. kk_low_price_for_extension remains a disqualifier.`
**OOS semantics:** current counts are cumulative mature evidence; OOS counts are strict `signal_date >= 2026-05-17` mature evidence.
**Realistic review timing:** earliest likely verdict review is late July–mid September 2026, depending on confirmed-row accumulation and T+5/T+10/T+20 maturity.
| hypothesis_id     | status              | baseline_available   |   confirmed_n_5d |   unconfirmed_n_5d |   spread_alpha_vs_spy_5d_pp |   supported_threshold_t5_alpha_spread_pp |   bootstrap_supported_pct |   supported_bootstrap_threshold_pct |   weekly_consistency_pct |   single_ticker_spread_share_pct |   invalid_signal_date_rows_dropped |
|:------------------|:--------------------|:---------------------|-----------------:|-------------------:|----------------------------:|-----------------------------------------:|--------------------------:|------------------------------------:|-------------------------:|---------------------------------:|-----------------------------------:|
| H_KK_CONFIRMATION | WATCHING_LOW_SAMPLE | True                 |                1 |                 42 |                     1.32941 |                                      0.5 |                       nan |                                  80 |                      nan |                              nan |                                  0 |

**Current cohort split (cumulative, in-sample baseline):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |       66 |               42 |        0.0592019 |             -0.960518 |                22 |          0.817542 |                 0 |               nan |
| BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    |        1 |                1 |        1.2442    |              0.368891 |                 0 |        nan        |                 0 |               nan |

**Strict OOS cohort split (signal_date >= 2026-05-17; drives verdict):**
| kk_confirmation_cohort                     |   n_rows |   n_evaluable_5d |   avg_ret_5d_all |   avg_alpha_vs_spy_5d |   n_evaluable_10d |   avg_ret_10d_all |   n_evaluable_20d |   avg_ret_20d_all |
|:-------------------------------------------|---------:|-----------------:|-----------------:|----------------------:|------------------:|------------------:|------------------:|------------------:|
| BONDE_ANTICIPATION_WITHOUT_KK_CONFIRMATION |       22 |                0 |              nan |                   nan |                 0 |               nan |                 0 |               nan |

**KK classification audit sample:**
| ticker   | signal_date   | kk_research_confirmation   |   kk_extend_score |   kk_leadership_score |   kk_group_strength_score | kk_low_price_for_extension   | kk_pause_too_long   | kk_risk_too_wide   | kk_weak_liquidity   | kk_too_far_from_highs   | kk_major_breakdown   | kk_late_stage_proxy   | kk_bag_holder   | kk_weak_bonde_score   |
|:---------|:--------------|:---------------------------|------------------:|----------------------:|--------------------------:|:-----------------------------|:--------------------|:-------------------|:--------------------|:------------------------|:---------------------|:----------------------|:----------------|:----------------------|
| AVNS     | 2026-05-15    | False                      |           73.2439 |               92.4792 |                   8.00745 | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| GSAT     | 2026-05-15    | True                       |           72.0487 |               88.3498 |                  16.5736  | False                        | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-18    | False                      |           73.3579 |               92.5688 |                  16.0741  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| SILA     | 2026-05-18    | False                      |           71.589  |               83.8692 |                  29.3464  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| SILA     | 2026-05-19    | False                      |           70.9557 |               83.4916 |                  28.2179  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-20    | False                      |           72.3139 |               92.5688 |                  14.4052  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| TBRG     | 2026-05-21    | False                      |           72.0825 |               89.3302 |                   7.44879 | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-21    | False                      |           71.7059 |               92.2271 |                  13.2879  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| TBRG     | 2026-05-22    | False                      |           73.9513 |               87.8889 |                   7.44879 | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |
| AVNS     | 2026-05-22    | False                      |           69.4722 |               91.2918 |                  13.6603  | True                         | True                | False              | False               | False                   | False                | False                 | False           | False                 |

**KK confirmed cohort rows plus unconfirmed sample:**
| ticker   | signal_date   | kk_research_confirmation   | kk_confirmation_cohort                     | kk_base_source                | source_kk_file                         | _kk_trade_key   |   _kk_duplicate_key_count | kept_for_hypothesis   |   kk_extend_score |   kk_low_price_for_extension |   kk_pause_too_long |
|:---------|:--------------|:---------------------------|:-------------------------------------------|:------------------------------|:---------------------------------------|:----------------|--------------------------:|:----------------------|------------------:|-----------------------------:|--------------------:|
| GSAT     | 2026-05-15    | True                       | BONDE_ANTICIPATION_WITH_KK_CONFIRMATION    | skill_pack_candidate_outcomes | bonde_kk_final_decision_2026-05-15.csv | GSAT|2026-05-15 |                         1 | True                  |           72.0487 |                            0 |                   1 |
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
- Council/disagreement resolver rows: **21**
| outcome_status   |   rows |
|:-----------------|-------:|
| PENDING          |     19 |
| RESOLVED         |      2 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                                                  |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:------------------------------------------------------------------|
| PGNY     | DELAYED_EP     | DEFER             | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=4 |
| DBX      | ACTIVE_BURST   | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=4 |
| SEZL     | DELAYED_EP     | CANCEL            | PENDING          | PENDING         | PENDING                     | OUTCOME_PENDING_INSUFFICIENT_FUTURE_BARS: available_future_bars=4 |
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
- Raw Council resolver rows loaded: **23.0**
- Rows after latest-run dedup: **21.0**
- Latest source per ticker:
| ticker   | signal_date   | setup_family   | council_verdict   | source_file                                       |   source_priority |   run_round |
|:---------|:--------------|:---------------|:------------------|:--------------------------------------------------|------------------:|------------:|
| PGNY     | 2026-05-18    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-19.csv              |               100 |           0 |
| DBX      | 2026-05-18    | ACTIVE_BURST   | CANCEL            | council_disagreements_2026-05-19.csv              |               100 |           0 |
| SEZL     | 2026-05-18    | DELAYED_EP     | CANCEL            | council_disagreements_2026-05-19.csv              |               100 |           0 |
| LOCO     | 2026-05-19    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| SEZL     | 2026-05-19    | DELAYED_EP     | CANCEL            | council_disagreements_2026-05-20.csv              |               100 |           0 |
| CLSK     | 2026-05-19    | SLINGSHOT      | CANCEL            | council_disagreements_2026-05-20.csv              |               100 |           0 |
| IFS      | 2026-05-19    | SLINGSHOT      | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| CGCT     | 2026-05-19    | SLINGSHOT      | CANCEL            | council_disagreements_2026-05-20.csv              |               100 |           0 |
| LLY      | 2026-05-19    | SLINGSHOT      | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| KGS      | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| EFC      | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| KEX      | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| CDNA     | 2026-05-19    | PAUSE          | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| ARM      | 2026-05-19    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| TTMI     | 2026-05-19    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| ALAB     | 2026-05-19    | ACTIVE_BURST   | DEFER             | council_disagreements_2026-05-20.csv              |               100 |           0 |
| RLAY     | 2026-05-19    | EP_ACTIVE      | CANCEL            | council_disagreements_2026-05-20.csv              |               100 |           0 |
| AAP      | 2026-05-21    | EP_ACTIVE      | DEFER             | council_disagreements_2026-05-22.csv              |               100 |           0 |
| GFS      | 2026-05-21    | EP_ACTIVE      | DEFER             | council_disagreements_2026-05-22.csv              |               100 |           0 |
| WRBY     | 2026-05-15    | DELAYED_EP     | DEFER             | council_disagreements_2026-05-15-spir-wrby-r4.csv |               100 |           4 |


## 12. Day-1 shape diagnostics
Compact executive view. Full coverage/verdict tables remain in the Day-1 audit CSV/markdown outputs.
- Source-capable coverage minimum: **87.4%**
- All-row coverage minimum, legacy rows included: **29.2%**
- Source-capable field statuses:
| field                   |   coverage_pct | status            |
|:------------------------|---------------:|:------------------|
| day1_close_pct_in_range |          100   | OK                |
| day1_move_pct           |           87.4 | WARN_LOW_COVERAGE |
| day1_vol_ratio          |           87.4 | WARN_LOW_COVERAGE |

- Day-1 verdict summary:
| verdict                      |   rows |
|:-----------------------------|-------:|
| INSUFFICIENT_RESOLVED_SAMPLE |      4 |


## 13. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. Measurement only; no SLINGSHOT rule-change evidence yet.
- Rows: **1,005**; full-plan proxy rows: **783**; rows with ≥5 future bars: **270**; OK-evaluable rows: **42**.
- DECISION_LOG rows target/R:R enriched inside learning loop from universe planning fields: **151**
- Entry-source classification (v4.13.73): **CAPTURED_AT_TRIGGER=783** (verdict-eligible pool, gated on T+5 maturity); BACKFILLED_FROM_SIGNAL_CLOSE=178 (robustness panel only, excluded from verdict); MISSING_ENTRY_UNRECOVERABLE=44 (excluded).
- Latest pack health: `2026-05-22` **123/124** rows CAPTURED_AT_TRIGGER (partial capture, investigate).
- Top missing/evaluability reasons:
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| NO_PRICE_DATA            |    440 |
| INSUFFICIENT_FUTURE_BARS |    295 |
| MISSING_ENTRY            |    222 |
| OK_EVALUABLE             |     42 |
| NEVER_TRIGGERED          |      6 |

- Full detail retained in: `slingshot_evaluability_audit_latest.md/csv`, `slingshot_scope_price_diagnostics_latest.md`, `slingshot_hygiene_diagnostics_latest.md`, and the corresponding summary CSVs.
- Interpretation: missing R:R is a field/evaluability issue, not zero R:R or negative SLINGSHOT expectancy.
- Bucket-distribution snapshot available in SLINGSHOT diagnostics exports; omitted here for compactness.

## 14. Sugar Babies overlay
- Status: **monitoring-only context overlay, not a trade signal.**
- Current read: Sugar Baby=True candidates show 0.33% avg T+5 versus -1.37% for non-Sugar Baby candidates (evaluated n=2020 vs 1137).
- Interpretation: Sugar Babies currently has broader sample support than EP9M for a future `ranking_context_score` contribution, but still needs out-of-sample / mature-week validation before any non-zero boost.
- Sugar Babies ticker lookup rows: **432**
### Sugar Baby vs non-Sugar Baby
| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     2937 |                2020 |             0.334138 |               45.0495 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     2620 |                1822 |             0.497967 |               45.6092 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     1913 |                1137 |            -1.37054  |               41.8646 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     1663 |                 985 |            -1.27667  |               41.5228 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Recurrence buckets
| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 0             |     1663 |                 985 |           -1.27667   |               41.5228 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      207 |                 140 |           -1.70691   |               37.8571 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      241 |                 160 |            0.745746  |               46.25   | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      310 |                 228 |            0.0793333 |               46.9298 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 8+            |     1862 |                1294 |            0.779641  |               46.136  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

### Setup-family × Sugar Baby=True
| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     2329 |                1643 |             0.431446 |               45.3439 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      211 |                 150 |             0.806639 |               42.6667 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      118 |                 102 |            -2.49939  |               38.2353 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |       71 |                  49 |             0.880746 |               42.8571 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |       86 |                  40 |             2.45208  |               67.5    | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |       97 |                  21 |             0.482199 |               38.0952 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       18 |                  12 |            -4.58277  |               33.3333 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        4 |                   2 |            -2.37558  |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        3 |                   1 |             8.4152   |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

- Council context export: `latest_sugar_babies_context.md` + `latest_sugar_babies_ticker_context.csv`.

## 15. Realized P&L attribution
- Status: **available but sample-immature**. This is trading-layer attribution, not just signal-date forward return.
- Maturity: **2** closed realized rows; **2** with realized R. Calibration threshold: **30+ realized-R rows**.
### Overall realized P&L / R
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| OVERALL      | ALL           |        2 |               2 |                   2 |           0.586044 |         0.293022 |            0.293022 |          100 |      0.586044 |              0 |               nan |     237.919 |   118.959 |

### By setup_family
| slice_name   | slice_value   |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:-------------|:--------------|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| setup_family | ACTIVE_BURST  |        1 |                   1 |          0.545434  |        0.545434  |          100 |               nan |    218.446  |
| setup_family | DELAYED_EP    |        1 |                   1 |          0.0406097 |        0.0406097 |          100 |               nan |     19.4723 |

### By action_label
| slice_name   | slice_value   |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:-------------|:--------------|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| action_label | A2            |        2 |                   2 |           0.586044 |         0.293022 |          100 |               nan |     237.919 |

### By final_trade_status
| slice_name         | slice_value   |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:-------------------|:--------------|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| final_trade_status | COUNCIL       |        2 |                   2 |           0.586044 |         0.293022 |          100 |               nan |     237.919 |

### By council_verdict
| slice_name      |   slice_value |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:----------------|--------------:|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| council_verdict |           nan |        2 |                   2 |           0.586044 |         0.293022 |          100 |               nan |     237.919 |

### By sugar_baby_flag
| slice_name      |   slice_value |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:----------------|--------------:|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| sugar_baby_flag |           nan |        2 |                   2 |           0.586044 |         0.293022 |          100 |               nan |     237.919 |

### By ep9m_context_type
| slice_name        |   slice_value |   n_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   win_rate_r |   profit_factor_r |   total_pnl |
|:------------------|--------------:|---------:|--------------------:|-------------------:|-----------------:|-------------:|------------------:|------------:|
| ep9m_context_type |           nan |        2 |                   2 |           0.586044 |         0.293022 |          100 |               nan |     237.919 |

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
| P1         | Keep SLINGSHOT target/R:R enrichment in learning loop | Learning loop backfilled 151 DECISION_LOG row(s) from diagnostic/skill-pack planning fields. Actionability skill remains stable; continue measurement-layer enrichment from universe outputs until the raw decision-log schema is intentionally revised. |
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

Rows analyzed: 88
Data issue rows: 15
Repeat stale rows: 14
Valid 20-bar thrust rows: 28
Valid longer-lookback thrust rows: 14
Weak-thrust-only rows: 8
No-real-thrust rows: 8
Insufficient-price-data rows: 1

Raw flag counts:
- data_issue_flag: 15
- repeat_pause_signal_10d_ge2: 25
- repeat_pause_signal_10d_ge3: 15
- valid_longer_lookback_thrust_flag: 30
- weak_thrust_only_flag: 9
- no_real_thrust_flag: 8

Top repeat tickers:
| ticker | count_10d | first_signal_date | last_signal_date |
|---|---|---|---|
| WSR | 7 | 2026-05-05 | 2026-05-21 |
| SILA | 6 | 2026-05-05 | 2026-05-18 |
| TWO | 4 | 2026-05-15 | 2026-05-22 |
| CSX | 3 | 2026-05-11 | 2026-05-20 |
| TALK | 3 | 2026-05-05 | 2026-05-11 |
| APLS | 2 | 2026-05-05 | 2026-05-15 |
| FBP | 2 | 2026-05-06 | 2026-05-08 |
| SLB | 2 | 2026-05-21 | 2026-05-22 |
| TERN | 2 | 2026-05-04 | 2026-05-15 |
| WAFD | 2 | 2026-05-06 | 2026-05-11 |

Manual review queue (top 15 by priority):
| priority | ticker | signal_date | class | reason |
|---|---|---|---|---|
| 1 | ACLX | 2026-04-29 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=77.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-15 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | DAWN | 2026-04-24 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=65.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | FLYW | 2026-05-22 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=20.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | HTCO | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=239.7%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | KALV | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=38.6%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | NAVN | 2026-05-21 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=43.3%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | PSFE | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=20.1%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | RELY | 2026-05-22 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=25.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TALK | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TALK | 2026-05-08 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TALK | 2026-05-11 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TH | 2026-05-08 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=36.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |

**Hypothesis state (v4.13.77):**
- `H_PAUSE_BC_INVERT` = REJECTED / NOT_CONFIRMED — outlier-driven, threshold-fragile.
- `H_PAUSE_FRESHNESS_COOLDOWN` = CANDIDATE — repeat PAUSE within 10 trading sessions without a fresh thrust underperforms first PAUSE signals. **No production rule shipped.**

## Council Effectiveness

_Diagnostic measurement only — run_date 2026-05-24, spec v1.0. No rule, skill, or schema changes._

Rows analyzed: 971
Rows matched to council artifacts: 7
Rows with mature T+5: 769
Rows immature / no-data: 202

### Council vs Actionability Matrix

| actionability | council | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | avg_t20 |
|---|---|---|---|---|---|---|---|
| REJECT | UNKNOWN | 105 | 102 | -1.11% | 42.57% | -4.93% | n/a |
| TAKE | UNKNOWN | 2 | 1 | -0.10% | 0.00% | n/a | n/a |
| WATCH | APPROVE | 4 | 1 | -12.67% | 0.00% | n/a | n/a |
| WATCH | REJECT | 3 | 1 | 5.75% | 100.00% | n/a | n/a |
| WATCH | UNKNOWN | 857 | 664 | -0.05% | 41.13% | -0.38% | n/a |

### TAKE Challenge Value

| group | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 | avg_t20 | win_rate_t20 |
|---|---|---|---|---|---|---|---|---|
| TAKE_APPROVED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_DOWNGRADED_OR_REJECTED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_NEUTRAL_OR_UNKNOWN_COUNCIL | 2 | 1 | -0.10% | 0.00% | n/a | n/a | n/a | n/a |

### Council Flags (T+5 mature)

| metric | n | rate |
|---|---|---|
| saved_loss_count | 0 | n/a |
| cut_winner_count | 1 | n/a |
| found_winner_count | 0 | n/a |
| missed_loser_count | 0 | n/a |
| saved_loss_rate_among_downgrades | 0 | 0.00% |
| cut_winner_rate_among_downgrades | 1 | 100.00% |
| found_winner_rate_among_upgrades | 0 | n/a |
| missed_loser_rate_among_approvals | 0 | n/a |

### Reason-Category Performance (council-opined rows, T+5 mature)

| reason_category | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 |
|---|---|---|---|---|---|---|
| OTHER | 1 | 0 | n/a | n/a | n/a | n/a |
| RISK_REWARD_WEAK | 6 | 2 | -3.46% | 50.00% | n/a | n/a |

### Interpretation

- If council-downgraded TAKE rows underperform approved TAKE rows, council is adding value.
- If council-downgraded TAKE rows outperform, council is too conservative.
- Require n>=30 per comparison bucket before treating this as evidence.

### Operational Quality

- NOT_APPLICABLE rows: 0
- Join failures (NO_MATCH): 964
- Rows missing trigger_price: 821
- Rows missing invalidation_price: 813
