# Bonde Learning Loop Executive Digest — 2026-05-23

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-05-23 16:39 UTC_
_Notebook: v4.13.74 (digest surfaces entry-source classification)_

## 1. Today's required action
1. **No rule changes.** (§9 hypothesis tracker / verdict gates — all monitoring-only, no SUPPORTED verdicts)
2. **Wait for SLINGSHOT future bars.** Earliest T+5 maturity: **2026-05-22**. (§13)
3. **Watch A1/A2 zero-TRADE issue.** Confirm whether A1 is intentionally rare or unreachable and whether clean A1/A2 rows are over-routed. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is now pre-registered and measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **0**. (§15)

## 2. Changed since last run — prior run → 2026-05-23 16:39 UTC
- Prior digest date: **not available**
- Current digest date: **2026-05-23**
- Comparison window: **prior run → 2026-05-23**

### Pipeline changes
- SLINGSHOT decision-log target/R:R backfill: no new backfilled rows detected in this run.
- Tiny-geometry hygiene audit active: no tiny-geometry rows flagged.
- Dedup diagnostics active: **5** raw full-plan+price rows → **3** unique ticker-date rows.
- Backfill source attribution simplified to `slingshot_backfill_source` enum.
- KK confirmation research layer added: `H_KK_CONFIRMATION` computes cohorts in the learning loop without changing upstream signals.

### Data changes
- No new hypothesis verdicts crossed a rule-change threshold.
- No Day-1 shape verdicts crossed threshold.
- Realized P&L remains sample-immature: `n_with_realized_r` = **0**.

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.
- SLINGSHOT `OK_EVALUABLE` rows remain 0 until future bars mature.

## 3. Operational status
- Master decision-log rows: **735**
- Decision-log source files: **7**
- Latest decision-log sources: `daily_decision_log_2026-05-09.csv`, `daily_decision_log_2026-05-12.csv`, `daily_decision_log_2026-05-13.csv`, `daily_decision_log_2026-05-22.csv`, `sample_daily_decision_log.csv`
- 2026-05-15 decision log ingested: **NO**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    605 |
| REJECT               |     97 |
| COUNCIL              |     32 |
| TRADE                |      1 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     19 |
| COUNCIL              |      4 |
| REJECT               |      1 |

### Corpus reconciliation
- Candidate decision-log files discovered: **9**
- Included decision-log files: **8**
- Excluded decision-log files: **1** (1 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **784 → 759 → 735**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
2. Post-2026-05-15 rows have zero TRADE rows (n=24). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
3. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
4. Corpus reconciliation is now active: 1 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
5. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| ACTIVE_BURST   |       99 |               96 | ACTIONABLE_SAMPLE |         94.9495 |            34.0659 |        -1.23472   |
| PAUSE          |       59 |               44 | ACTIONABLE_SAMPLE |         96.6102 |            47.619  |         1.04069   |
| SLINGSHOT      |       41 |               41 | ACTIONABLE_SAMPLE |        100      |            26.8293 |        -2.44218   |
| EP_ACTIVE      |       37 |               33 | ACTIONABLE_SAMPLE |         86.4865 |            46.6667 |        -0.728472  |
| DELAYED_EP     |       18 |               17 | BUILDING_SAMPLE   |         94.4444 |            62.5    |        -0.37617   |
| ANTICIPATION   |        8 |                8 | LOW_SAMPLE        |        100      |            50      |        -0.0866923 |
| MOMENTUM_BURST |        1 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |
| PRE_BURST      |        1 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       20 |               18 | BUILDING_SAMPLE   |            66.6667 |          2.77643  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        6 |                6 | LOW_SAMPLE        |            50      |          1.25906  |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       25 |               22 | ACTIONABLE_SAMPLE |            40      |          1.1819   |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        5 |                5 | LOW_SAMPLE        |            25      |          0.210662 |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       39 |               26 | ACTIONABLE_SAMPLE |            33.3333 |         -0.261113 |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        5 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |        9 |                8 | LOW_SAMPLE        |            62.5    |         -0.7628   |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |       34 |               34 | ACTIONABLE_SAMPLE |            29.4118 |         -1.89033  |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| SLINGSHOT      | REJECT          | D              | REJECT               |        5 |                5 | LOW_SAMPLE        |             0      |         -7.81828  |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |        8 |                7 | LOW_SAMPLE        |            40      |         -6.22877  |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       24 |               24 | ACTIONABLE_SAMPLE |            29.1667 |         -2.56178  |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       17 |               15 | BUILDING_SAMPLE   |            46.6667 |         -2.17819  |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       38 |               38 | ACTIONABLE_SAMPLE |            34.2105 |         -2.11297  |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |       34 |               34 | ACTIONABLE_SAMPLE |            29.4118 |         -1.89033  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |        9 |                8 | LOW_SAMPLE        |            62.5    |         -0.7628   |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        5 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A1             | TRADE                | ACTIVE_BURST   |        1 |
| ALL_ROWS       | A2             | COUNCIL              | ACTIVE_BURST   |        6 |
| ALL_ROWS       | A2             | COUNCIL              | DELAYED_EP     |        4 |
| ALL_ROWS       | A2             | COUNCIL              | EP_ACTIVE      |        5 |
| POST_V5_9_19   | A2             | COUNCIL              | DELAYED_EP     |        1 |
| POST_V5_9_19   | A2             | COUNCIL              | EP_ACTIVE      |        1 |
| LATEST_SESSION | A2             | COUNCIL              | EP_ACTIVE      |        1 |

### Current interpretation
- A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
- Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
- All visible A2 rows route to COUNCIL. Treat A2 performance as marginal-A2 performance, not clean executable-A2 performance.
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
| DELAYED_EP     | ACTIONABLE      | A2             | COUNCIL              |        4 |                4 | LOW_SAMPLE      |            66.6667 |          1.10798  |
| EP_ACTIVE      | ACTIONABLE      | A2             | COUNCIL              |        5 |                4 | LOW_SAMPLE      |             0      |         -6.19864  |

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
| PAUSE          | B              |              26 |       -0.261113 |        33.3333 | C             |             18 |        2.77643 |       66.6667 |                      3.03754 |

Potential explanations to test: 5-day window too short, extension/streak gate rejecting legitimate continuation, or backward-looking quality labels over-penalizing names already working.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family                         | current_test                                                                               | method_note                                                                                                                                                          | regime_context   |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------------------------|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN | ACTIVE_BURST                   | ACTIVE_BURST D/REJECT minus ACTIVE_BURST C/WATCH avg T+5                                   | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-On          |            38 |        -2.11297 |            24 |       -2.56178  |              0.448813 | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_EP_ACTIVE_COUNCIL_TIGHTEN | EP_ACTIVE                      | EP_ACTIVE final_trade_status=COUNCIL combined avg T+5                                      | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-On          |            11 |        -6.21781 |           nan |      nan        |             -6.21781  | 2026-05-16       |         0 |       nan |               nan | WATCHING_LOW_SAMPLE        |
| H_PAUSE_BC_INVERT           | PAUSE                          | PAUSE C/WATCH minus PAUSE B/WATCH avg T+5                                                  | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-On          |            18 |         2.77643 |            26 |       -0.261113 |              3.03754  | 2026-05-16       |         0 |         0 |               nan | WATCHING_NOT_RULE_EVIDENCE |
| H_KK_CONFIRMATION           | ANTICIPATION / KK_CONFIRMATION | Bonde anticipation WITH KK confirmation minus WITHOUT KK confirmation avg T+5 alpha vs SPY | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-On          |             0 |       nan       |             0 |      nan        |            nan        | 2026-05-17       |         0 |         0 |               nan | WATCHING_NOT_YET_WIRED     |

- Hypothesis tracker report: `hypothesis_tracker_latest.md`
- ACTIVE_BURST Gate6 shadow candidates: **0** rows in `active_burst_gate6_shadow_candidates_v41328.csv`
- Guardrail: shadow candidates are review/tradeability audit rows only. They do not change `final_trade_status`, action label, ranking, R:R, or hard-reject behavior.
### Pre-registered verdict gates
These gates are binding review criteria. A rule patch should not ship unless its hypothesis has a pre-registered SUPPORTED verdict or a separate explicitly documented emergency bug rationale.
| hypothesis_id                  | method_note                                                                                                                                                          | regime_context   | current_state                                                                                                  | required_sample                                                                                                                                      | oos_window                                      | earliest_review                                                                                                       | pre_registered_prediction                                                                                              | supported_if                                                                                                                                                 | rejected_if                                                                                          | ambiguous_if                                                                                                                                             | if_supported                                                                                                                          | if_rejected                                                                         |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:---------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| H_ACTIVE_BURST_GATE6_SOFTEN    | Compare ACTIVE_BURST D/REJECT vs ACTIVE_BURST C/WATCH on mature T+5; verdict uses strict OOS rows only.                                                              | Risk-On          | current effect 0.45; n_a=38; n_b=24; status=WATCHING_NOT_RULE_EVIDENCE                                         | OOS n_C >= 30 and n_D >= 30, with mature T+5/T+10/T+20 windows.                                                                                      | 2026-05-16 onward                               | When both OOS slices meet sample and maturity gates.                                                                  | D/REJECT minus C/WATCH spread remains >= +1.5% OOS.                                                                    | OOS spread >= +1.5% and confidence interval / robustness check does not collapse to zero.                                                                    | OOS spread < +0.5% or direction inverts.                                                             | OOS spread is +0.5% to +1.5% or sample composition is unstable.                                                                                          | Draft V5.9.21-G6-SOFTEN spec; do not ship until patch text is reviewed.                                                               | File hypothesis; no Gate6 softening.                                                |
| H_EP_ACTIVE_COUNCIL_TIGHTEN    | Measure EP_ACTIVE rows routed to COUNCIL on mature T+5; verdict uses strict OOS rows only.                                                                           | Risk-On          | current effect -6.22; n_a=11; status=WATCHING_LOW_SAMPLE                                                       | OOS EP_ACTIVE COUNCIL n >= 30 with mature T+5 and at least 10 T+20 rows.                                                                             | 2026-05-16 onward                               | When OOS council-routed EP_ACTIVE rows reach n>=30.                                                                   | EP_ACTIVE COUNCIL average T+5 remains <= -3.0% OOS.                                                                    | OOS avg T+5 <= -3.0% and win rate <= 35% without one-stock distortion.                                                                                       | OOS avg T+5 >= 0% or win rate normalizes above 45%.                                                  | OOS avg T+5 is -3.0% to 0% or driven by one outlier.                                                                                                     | Draft V5.9.21-EPACTIVE-COUNCIL-TIGHTEN review spec.                                                                                   | Keep EP_ACTIVE council routing unchanged.                                           |
| H_PAUSE_BC_INVERT              | Compare PAUSE C/WATCH vs PAUSE B/WATCH on mature T+5; verdict uses strict OOS rows only.                                                                             | Risk-On          | current effect 3.04; n_a=18; n_b=26; status=WATCHING_NOT_RULE_EVIDENCE                                         | OOS PAUSE B/WATCH n >= 30 and PAUSE C/WATCH n >= 30.                                                                                                 | 2026-05-16 onward                               | When both OOS PAUSE slices hit n>=30 and T+5 is mature.                                                               | PAUSE C/WATCH minus B/WATCH spread remains >= +1.5% OOS.                                                               | OOS spread >= +1.5% and persists after removing tiny/liquidity outliers.                                                                                     | OOS spread < +0.5% or B resumes leadership.                                                          | OOS spread is +0.5% to +1.5% or sample is too concentrated.                                                                                              | Draft V5.9.21-PAUSE-RANK-REVIEW spec; do not change B/C labels before review.                                                         | Keep PAUSE B/C rank mapping unchanged.                                              |
| H_KK_CONFIRMATION              | Compare Bonde anticipation rows WITH vs WITHOUT KK research confirmation on T+5 alpha vs SPY; KK definition excludes only kk_pause_too_long from hard disqualifiers. | Risk-On          | n_a=0; n_b=0; status=WATCHING_NOT_YET_WIRED                                                                    | OOS n >= 30 confirmed AND n >= 30 unconfirmed Bonde anticipation rows with mature T+5 outcomes; both cohorts must satisfy signal_date >= 2026-05-17. | 2026-05-17 onward                               | When both confirmed and unconfirmed cohorts reach n>=30 with mature T+5; component regression only at n>=100 KK rows. | Confirmed cohort T+5 alpha vs SPY exceeds unconfirmed cohort by at least +0.50 percentage points.                      | T+5 alpha spread >= +0.50 pp, T+10 or T+20 confirms direction, no single ticker >40% of spread, weekly consistency >=60%, and bootstrap_supported_pct >=80%. | T+5 alpha spread <= 0 or unconfirmed cohort outperforms after sample gates.                          | T+5 alpha spread is 0 to +0.50 pp, multi-horizon direction is mixed, ticker/week concentration is excessive, or bootstrap robustness is below threshold. | Use KK confirmation as Layer 5 priority/confidence signal only; do not hard-reject unconfirmed Bonde rows.                            | Deprecate KK confirmation in Layer 5 decisions; keep KK fields as diagnostics only. |
| H_SLINGSHOT_TARGET_BASIS       | Measure SLINGSHOT_PRIMARY full-plan unique ticker-date rows for R:R>=2.0 and later T+5 expectancy after evaluability gates pass.                                     | Risk-On          | 5 raw full-plan+price rows; 3 unique full-plan+price ticker-date rows; 3 unique OK_EVALUABLE ticker-date rows. | unique_ok_evaluable_ticker_date_rows >= 30 and at least 10 OOS rows after 2026-05-22.                                                                | Starts 2026-05-22                               | When unique OK_EVALUABLE ticker-date rows reach n>=30.                                                                | >=40% of SLINGSHOT_PRIMARY full-plan unique ticker-date rows clear V5.9 R:R floor >= 2.0.                              | R:R>=2.0 pass rate >=40% and T+5 expectancy is not worse than ACTIVE_BURST baseline.                                                                         | R:R>=2.0 pass rate <30% or T+5 expectancy materially underperforms ACTIVE_BURST.                     | R:R pass rate is 30–40% or expectancy is positive but under-sampled.                                                                                     | Keep SLINGSHOT measurement path live; consider later context/ranking overlay only after 100+ unique OK_EVALUABLE rows.                | Do not promote SLINGSHOT; review target-basis and detection criteria.               |
| H_SUGAR_BABIES_CONTEXT_OVERLAY | Compare Sugar Baby=True vs False rows by mature T+5, then require OOS and family-level confirmation before any ranking-context boost.                                | Risk-On          | Sugar Babies overlay active; OOS spread not yet validated.                                                     | OOS >= 100 evaluated Sugar=True and >= 100 Sugar=False rows, plus at least two setup families with n>=30.                                            | Next mature weekly cohorts after current digest | When OOS rows and family spread requirements are met.                                                                 | Sugar=True retains >= +1.0% avg T+5 spread over Sugar=False without worsening win-rate materially.                     | OOS avg spread >= +1.0% and at least two families have non-negative confirmation.                                                                            | OOS spread < +0.25% or driven by one family only.                                                    | OOS spread +0.25% to +1.0% or family split is mixed.                                                                                                     | Draft Sugar Babies ranking_context_score proposal; cannot override R:R, DTE, hard rejects, failed EP, dilution/offering, or bad data. | Keep Sugar Babies as monitoring-only context.                                       |
| H_REALIZED_PNL_CORRELATION     | Compare actual broker realized R/P&L against system setup/action/final-status slices once n_with_realized_r >= 30.                                                   | Risk-On          | 0 realized-R rows; threshold not met.                                                                          | n_with_realized_r >= 30 total, then >=10 per major setup/action slice before slice-level claims.                                                     | Broker-export rows as they arrive               | When realized-R count reaches n>=30.                                                                                  | Layer 5 realized-R selection should outperform raw WATCH/COUNCIL forward-return expectancy on comparable setup slices. | Realized R is positive overall and aligns with the strongest forward-return slices.                                                                          | Realized R is negative despite positive forward-return slices, implying execution/selection failure. | Positive P&L but too concentrated in one trade or mismatch between broker rows and system rows.                                                          | Use realized-R weighting in weekly system review; do not change signal rules solely from P&L.                                         | Prioritize execution/selection review before signal-rule changes.                   |

### KK confirmation study
Research-only: tests whether Bonde anticipation rows with KK leadership-quality confirmation outperform Bonde anticipation rows without KK confirmation. This does not alter trading labels, ranking, R:R, or hard gates.
**Operational definition:** `kk_research_confirmation = kk_extend_score >= 70 AND (kk_leadership_score >= 70 OR kk_group_strength_score >= 50) AND all KK hard-disqualifier flags are false except kk_pause_too_long. kk_low_price_for_extension remains a disqualifier.`
**OOS semantics:** current counts are cumulative mature evidence; OOS counts are strict `signal_date >= 2026-05-17` mature evidence.
**Realistic review timing:** earliest likely verdict review is late July–mid September 2026, depending on confirmed-row accumulation and T+5/T+10/T+20 maturity.
- KK confirmation tracker did not run or found no base cohort. Put `bonde_kk_final_decision_*.csv` and the canonical skill-pack/anticipation files into the one-inbox or inputs folder, then rerun.
- Pre-registered action: if SUPPORTED, use KK only as a Layer 5 priority/confidence signal; if REJECTED, keep KK diagnostics but stop using it for Layer 5 confirmation.
### Hypothesis discipline meta-rules
- Maximum active WATCHING hypotheses: **7**. Current pre-registered hypotheses: **7**.
- New hypotheses should not be added unless one existing hypothesis closes as `SUPPORTED`, `REJECTED`, or `AMBIGUOUS`, or unless there is a separately documented emergency/data-capture rationale. KK confirmation is the documented data-capture exception: without capturing cohorts now, the next 8–12 weeks would not answer the question.
- After a `SUPPORTED` hypothesis ships a patch, no new hypothesis from the same family should be opened for **90 days** unless there is an emergency bug rationale.
- If `H_REALIZED_PNL_CORRELATION` returns `REJECTED`, all signal-rule patches pause until execution / selection quality is reviewed.
- These meta-rules are designed to prevent hypothesis creep and post-hoc rule changes while OOS evidence matures.

## 10. ACTIVE_BURST Gate-6 Observational Watchlist
Rows in this section remain `REJECT` in the decision log. This is an observational research/watchlist section only; it does not alter `final_trade_status`, action labels, ranking, R:R, or hard-reject behavior.
- Full shadow candidates: **0**
- Tradeability-review watchlist rows: **0**
- Context-only rows excluded for missing trigger/invalidation: **0**
- Output file: `active_burst_gate6_observational_watchlist_latest.md`
- Source shadow CSV: `active_burst_gate6_shadow_candidates_v41328.csv`
- Required manual check: only consider these for live attention if they have a defensible trigger, invalidation, R:R, liquidity, DTE safety, and no hard reject.
_No Gate6 observational rows found in this run._

## 11. Council resolver status
- Council/disagreement resolver rows: **21**
| outcome_status   |   rows |
|:-----------------|-------:|
| NOT_APPLICABLE   |     21 |

| ticker   | setup_family   | council_verdict   | outcome_status   | outcome_class   | council_outcome_alignment   | resolution_notes                    |
|:---------|:---------------|:------------------|:-----------------|:----------------|:----------------------------|:------------------------------------|
| PGNY     | DELAYED_EP     | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| DBX      | ACTIVE_BURST   | CANCEL            | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| SEZL     | DELAYED_EP     | CANCEL            | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| LOCO     | DELAYED_EP     | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| SEZL     | DELAYED_EP     | CANCEL            | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| CLSK     | SLINGSHOT      | CANCEL            | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| IFS      | SLINGSHOT      | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| CGCT     | SLINGSHOT      | CANCEL            | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| LLY      | SLINGSHOT      | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| KGS      | PAUSE          | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| EFC      | PAUSE          | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |
| KEX      | PAUSE          | DEFER             | NOT_APPLICABLE   | NOT_APPLICABLE  | NOT_APPLICABLE              | MISSING_SOURCE_FIELD: trigger_price |


**Council resolver determinism audit (v4.13.61+ source-priority + round-aware):**
- Raw Council resolver rows loaded: **21.0**
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
- Source-capable coverage minimum: **100.0%**
- All-row coverage minimum, legacy rows included: **14.7%**
- Source-capable field statuses:
| field                   |   coverage_pct | status   |
|:------------------------|---------------:|:---------|
| day1_close_pct_in_range |            100 | OK       |
| day1_move_pct           |            100 | OK       |
| day1_vol_ratio          |            100 | OK       |

- Day-1 verdict summary:
| verdict                      |   rows |
|:-----------------------------|-------:|
| INSUFFICIENT_RESOLVED_SAMPLE |      4 |


## 13. SLINGSHOT diagnostics / evaluability audit
- Status: **detected but evaluability-gated**. Measurement only; no SLINGSHOT rule-change evidence yet.
- Rows: **83**; full-plan proxy rows: **5**; rows with ≥5 future bars: **83**; OK-evaluable rows: **5**.
- DECISION_LOG rows target/R:R enriched inside learning loop from universe planning fields: **0**
- Entry-source classification (v4.13.73): **CAPTURED_AT_TRIGGER=5** (verdict-eligible pool, gated on T+5 maturity); BACKFILLED_FROM_SIGNAL_CLOSE=0 (robustness panel only, excluded from verdict); MISSING_ENTRY_UNRECOVERABLE=78 (excluded).
- **WARNING (v4.13.73 tripwire):** Latest pack_date `2026-05-15` has **2 rows but ZERO CAPTURED_AT_TRIGGER.** The actionability skill may have regressed on entry capture. Investigate before trusting H_SLINGSHOT_TARGET_BASIS verdict from this run.
- Top missing/evaluability reasons:
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_ENTRY            |     78 |
| OK_EVALUABLE             |      5 |

- Full detail retained in: `slingshot_evaluability_audit_latest.md/csv`, `slingshot_scope_price_diagnostics_latest.md`, `slingshot_hygiene_diagnostics_latest.md`, and the corresponding summary CSVs.
- Interpretation: missing R:R is a field/evaluability issue, not zero R:R or negative SLINGSHOT expectancy.
- Bucket-distribution snapshot available in SLINGSHOT diagnostics exports; omitted here for compactness.

## 14. Sugar Babies overlay
- Sugar Babies overlay summary unavailable. Confirm `sugar_babies.csv` is visible to Colab.

## 15. Realized P&L attribution
- Status: **wired but no realized trade data ingested yet**.
- Drop a raw IBKR/broker CSV into `bonde_learning/_inbox/` using a name like `ibkr_trades_YYYY-MM-DD.csv`, `broker_trades_YYYY-MM-DD.csv`, or `executions_YYYY-MM-DD.csv`. The notebook will infer signal date, join system context, and compute realized R where stop/risk is available. No manual R sheet is required.
- This is the next major validation step if the system is already making money: connect signal quality to actual realized R/P&L.

## 16. Investigation queue
### New this run
- None auto-detected.
### Carried forward
| priority   | item                                         | why                                                                                                                                                                          |
|:-----------|:---------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P0         | Add realized-P&L attribution file            | Upload `realized_trades_YYYY-MM-DD.csv` to `_inbox/` so the loop can validate actual realized R against signal/council/context slices.                                       |
| P1         | A1/A2 executable-signal health check         | Confirm A1 count, A2 routing, and whether zero clean TRADE rows is intended strictness or over-routing.                                                                      |
| P1         | Confirm zero-TRADE root cause                | Post-2026-05-15 rows have zero TRADE rows (n=24). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.                                              |
| P1         | Investigate reject/watch and B/C/D inversion | Lower labels are outperforming higher labels in at least one ACTIONABLE_SAMPLE family; investigate gates before adding new ranking overlays.                                 |
| P1         | Track pre-registered rule-change hypotheses  | Monitor H_ACTIVE_BURST_GATE6_SOFTEN, H_EP_ACTIVE_COUNCIL_TIGHTEN, H_PAUSE_BC_INVERT, and H_KK_CONFIRMATION daily with OOS and realized-R gates before any rule patch.        |
| P2         | SLINGSHOT hygiene verification               | Before first OK_EVALUABLE rows mature, review tiny-geometry flags, duplicate ticker-date rows, and backfill-source attribution in `slingshot_hygiene_diagnostics_latest.md`. |

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

Rows analyzed: 59
Data issue rows: 12
Repeat stale rows: 6
Valid 20-bar thrust rows: 21
Valid longer-lookback thrust rows: 6
Weak-thrust-only rows: 7
No-real-thrust rows: 6
Insufficient-price-data rows: 1

Raw flag counts:
- data_issue_flag: 12
- repeat_pause_signal_10d_ge2: 13
- repeat_pause_signal_10d_ge3: 7
- valid_longer_lookback_thrust_flag: 16
- weak_thrust_only_flag: 7
- no_real_thrust_flag: 6

Top repeat tickers:
| ticker | count_10d | first_signal_date | last_signal_date |
|---|---|---|---|
| WSR | 5 | 2026-05-05 | 2026-05-21 |
| SILA | 4 | 2026-05-05 | 2026-05-13 |
| TALK | 3 | 2026-05-05 | 2026-05-11 |
| CSX | 2 | 2026-05-11 | 2026-05-13 |
| FBP | 2 | 2026-05-06 | 2026-05-08 |
| WAFD | 2 | 2026-05-06 | 2026-05-11 |
| ACDC | 1 | 2026-05-05 | 2026-05-05 |
| ACLX | 1 | 2026-04-29 | 2026-04-29 |
| APLS | 1 | 2026-05-05 | 2026-05-05 |
| ARW | 1 | 2026-05-21 | 2026-05-21 |

Manual review queue (top 15 by priority):
| priority | ticker | signal_date | class | reason |
|---|---|---|---|---|
| 1 | ACLX | 2026-04-29 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=77.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | APLS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=135.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | AVNS | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=69.5%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | DAWN | 2026-04-24 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=65.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | HTCO | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=239.7%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | KALV | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=38.6%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | NAVN | 2026-05-21 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=43.3%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | PSFE | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=20.1%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TALK | 2026-05-05 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TALK | 2026-05-08 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TALK | 2026-05-11 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 1 | TH | 2026-05-08 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=36.4%. Possible corporate action, split-adjustment issue, merger, or bad price data. |
| 2 | SILA | 2026-05-11 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=3 (>=3 stale repeats in 10 trading sessions) |
| 2 | SILA | 2026-05-13 | REPEAT_STALE_SIGNAL | same_ticker_pause_count_10d=4 (>=3 stale repeats in 10 trading sessions) |
| 2 | TALK | 2026-05-11 | DATA_ISSUE | Extreme close-to-close move detected: max_abs_c2c_80d=22.9%. Possible corporate action, split-adjustment issue, merger, or bad price data. |

**Hypothesis state (v4.13.77):**
- `H_PAUSE_BC_INVERT` = REJECTED / NOT_CONFIRMED — outlier-driven, threshold-fragile.
- `H_PAUSE_FRESHNESS_COOLDOWN` = CANDIDATE — repeat PAUSE within 10 trading sessions without a fresh thrust underperforms first PAUSE signals. **No production rule shipped.**

## Council Effectiveness

_Diagnostic measurement only — run_date 2026-05-23, spec v1.0. No rule, skill, or schema changes._

Rows analyzed: 735
Rows matched to council artifacts: 2
Rows with mature T+5: 715
Rows immature / no-data: 20

### Council vs Actionability Matrix

| actionability | council | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | avg_t20 |
|---|---|---|---|---|---|---|---|
| REJECT | UNKNOWN | 97 | 97 | -1.15% | 42.27% | -5.28% | n/a |
| TAKE | UNKNOWN | 1 | 1 | -0.10% | 0.00% | n/a | n/a |
| WATCH | APPROVE | 2 | 0 | n/a | n/a | n/a | n/a |
| WATCH | UNKNOWN | 635 | 617 | -0.12% | 40.33% | -1.11% | n/a |

### TAKE Challenge Value

| group | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 | avg_t20 | win_rate_t20 |
|---|---|---|---|---|---|---|---|---|
| TAKE_APPROVED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_DOWNGRADED_OR_REJECTED_BY_COUNCIL | 0 | 0 | n/a | n/a | n/a | n/a | n/a | n/a |
| TAKE_NEUTRAL_OR_UNKNOWN_COUNCIL | 1 | 1 | -0.10% | 0.00% | n/a | n/a | n/a | n/a |

### Council Flags (T+5 mature)

| metric | n | rate |
|---|---|---|
| saved_loss_count | 0 | n/a |
| cut_winner_count | 0 | n/a |
| found_winner_count | 0 | n/a |
| missed_loser_count | 0 | n/a |
| saved_loss_rate_among_downgrades | 0 | n/a |
| cut_winner_rate_among_downgrades | 0 | n/a |
| found_winner_rate_among_upgrades | 0 | n/a |
| missed_loser_rate_among_approvals | 0 | n/a |

### Reason-Category Performance (council-opined rows, T+5 mature)

| reason_category | n | n_mature_t5 | avg_t5 | win_rate_t5 | avg_t10 | win_rate_t10 |
|---|---|---|---|---|---|---|
| OTHER | 1 | 0 | n/a | n/a | n/a | n/a |
| RISK_REWARD_WEAK | 1 | 0 | n/a | n/a | n/a | n/a |

### Interpretation

- If council-downgraded TAKE rows underperform approved TAKE rows, council is adding value.
- If council-downgraded TAKE rows outperform, council is too conservative.
- Require n>=30 per comparison bucket before treating this as evidence.

### Operational Quality

- NOT_APPLICABLE rows: 0
- Join failures (NO_MATCH): 733
- Rows missing trigger_price: 635
- Rows missing invalidation_price: 635
