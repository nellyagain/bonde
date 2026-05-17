# Active Learning Context

Generated: 2026-05-17
Status: AUTO_GENERATED_FROM_LEARNING_LOOP

## Current learning state

- Use weekly cohort reports for rule-change evidence.
- Do not change rules from immature T+5/T+10/T+20 data.
- Council rows remain calibration data only until outcome resolution matures.

## Executive digest excerpt

# Bonde Learning Loop Executive Digest — 2026-05-17

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-05-17 07:43 UTC_

## 1. Today's required action
1. **No rule changes.** (§9 hypothesis tracker / verdict gates — all monitoring-only, no SUPPORTED verdicts)
2. **Wait for SLINGSHOT future bars.** Earliest T+5 maturity: **2026-05-22**. (§13)
3. **Watch A1/A2 zero-TRADE issue.** Confirm whether A1 is intentionally rare or unreachable and whether clean A1/A2 rows are over-routed. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is now pre-registered and measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **0**. (§15)

## 2. Changed since last run — 2026-05-17 07:43 UTC → 2026-05-17 07:43 UTC
- Prior digest date: **2026-05-17**
- Current digest date: **2026-05-17**
- Comparison window: **2026-05-17 → 2026-05-17**

### Pipeline changes
- SLINGSHOT decision-log target/R:R backfill: no new backfilled rows detected in this run.
- Tiny-geometry hygiene audit active: no tiny-geometry rows flagged.
- Dedup diagnostics active: no full-plan+price rows yet.
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
- Master decision-log rows: **35**
- Decision-log source files: **1**
- Latest decision-log sources: `daily_decision_log_2026-05-15 (1).csv`
- 2026-05-15 decision log ingested: **YES**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     32 |
| COUNCIL              |      2 |
| REJECT               |      1 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     32 |
| COUNCIL              |      2 |
| REJECT               |      1 |

### Corpus reconciliation
- Candidate decision-log files discovered: **1**
- Included decision-log files: **1**
- Excluded decision-log files: **0** (0 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **35 → 35 → 35**
- Rows removed by final master de-duplication: **0**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Post-2026-05-15 rows have zero TRADE rows (n=35). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
2. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
3. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d   |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:----------------|----------------:|-------------------:|------------------:|
| SLINGSHOT      |       23 |                0 | PARTIAL_OUTCOME |         8.69565 |                nan |               nan |
| PAUSE          |        9 |                0 | PARTIAL_OUTCOME |        22.2222  |                nan |               nan |
| DELAYED_EP     |        2 |                0 | PARTIAL_OUTCOME |         0       |                nan |               nan |
| EP_ACTIVE      |        1 |                0 | PARTIAL_OUTCOME |       100       |                nan |               nan |

### Actionability slices to monitor

## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A1/A2          | NONE                 | ALL            |        0 |
| POST_V5_9_19   | A1/A2          | NONE                 | ALL            |        0 |
| LATEST_SESSION | A1/A2          | NONE                 | ALL            |        0 |

### Current interpretation
- A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
- Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
### Council A1/A2 reachability audit
- No `council_reachability_audit_*.csv` found yet. Run the patched Council skill (V1.3.1+) and rerun this learning loop to populate:
  - `A1_REACHABLE`
  - `A2_EXECUTABLE_REACHABLE`
  - `ZERO_TRADE_CAUSE`
  - top demotion reasons
### A1/A2 forward-return slices
- No A1/A2 performance slices surfaced in `actionability_performance_summary_v410.csv`.
### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- If A1 remains absent post-V5.9.19, test whether criteria are intentionally rare or unreachable.

## 7. EP9M overlay
- EP9M setup-family row unavailable in the current setup-family summary.
- Corpus audit EP9M setup-family rows raw → normalized → master: **0 → 0 → 0**.
- Corpus audit EP9M context rows in master: **2**.
- Interpretation: EP9M did not enter the current decision-log corpus as a setup-family row. If a prior digest showed EP9M, inspect `decision_log_discovery_audit_latest.md` for excluded files or changed source scope.

## 8. Action-label / reject-vs-watch inversion watchlist
- No adjacent-label inversion with both sides n>=20 and lower-label avg return > higher-label avg by at least 1 percentage point.

## 9. Hypothesis tracker / verdict gates
These are pre-registered monitoring slots, not a roadmap and not rule-change permission. They exist so July does not become passive waiting: the loop tracks OOS rows daily while preserving evidence discipline.
| hypothesis_id               | family                         | current_test                                                                               | method_note                                                                                                                                                          | regime_context   |   current_n_a |   current_avg_a |   current_n_b |   current_avg_b |   current_effect_size | oos_start_date   |   oos_n_a |   oos_n_b |   oos_effect_size | status                     |
|:----------------------------|:-------------------------------|:-------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|--------------:|----------------:|--------------:|----------------:|----------------------:|:-----------------|----------:|----------:|------------------:|:---------------------------|
