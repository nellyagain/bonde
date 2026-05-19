# Active Learning Context

Generated: 2026-05-19
Status: AUTO_GENERATED_FROM_LEARNING_LOOP

## Current learning state

- Use weekly cohort reports for rule-change evidence.
- Do not change rules from immature T+5/T+10/T+20 data.
- Council rows remain calibration data only until outcome resolution matures.

## Executive digest excerpt

# Bonde Learning Loop Executive Digest — 2026-05-19

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-05-19 05:37 UTC_
_Notebook: v4.13.63 (Section 11 inline determinism audit)_

## 1. Today's required action
1. **No rule changes.** (§9 hypothesis tracker / verdict gates — all monitoring-only, no SUPPORTED verdicts)
2. **Wait for SLINGSHOT future bars.** Earliest T+5 maturity: **2026-05-22**. (§13)
3. **Watch A1/A2 zero-TRADE issue.** Confirm whether A1 is intentionally rare or unreachable and whether clean A1/A2 rows are over-routed. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is now pre-registered and measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **0**. (§15)

## 2. Changed since last run — prior run → 2026-05-19 05:37 UTC
- Prior digest date: **not available**
- Current digest date: **2026-05-19**
- Comparison window: **prior run → 2026-05-19**

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
- Master decision-log rows: **90**
- Decision-log source files: **1**
- Latest decision-log sources: `daily_decision_log_2026-05-18.csv`
- 2026-05-15 decision log ingested: **NO**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     87 |
| COUNCIL              |      3 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     87 |
| COUNCIL              |      3 |

### Corpus reconciliation
- Candidate decision-log files discovered: **1**
- Included decision-log files: **1**
- Excluded decision-log files: **0** (0 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **90 → 90 → 90**
- Rows removed by final master de-duplication: **0**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Post-2026-05-15 rows have zero TRADE rows (n=90). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
2. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
3. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d   |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:----------------|----------------:|-------------------:|------------------:|
| SLINGSHOT      |       73 |                0 | PARTIAL_OUTCOME |        100      |                nan |               nan |
| PAUSE          |        5 |                0 | PARTIAL_OUTCOME |        100      |                nan |               nan |
| EP_ACTIVE      |        4 |                0 | PARTIAL_OUTCOME |        100      |                nan |               nan |
| DELAYED_EP     |        4 |                0 | PARTIAL_OUTCOME |         50      |                nan |               nan |
| ACTIVE_BURST   |        3 |                0 | PARTIAL_OUTCOME |         66.6667 |                nan |               nan |
| PRE_BURST      |        1 |                0 | PARTIAL_OUTCOME |          0      |                nan |               nan |

### Actionability slices to monitor

## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A2             | COUNCIL              | DELAYED_EP     |        1 |
| POST_V5_9_19   | A2             | COUNCIL              | DELAYED_EP     |        1 |
| LATEST_SESSION | A2             | COUNCIL              | DELAYED_EP     |        1 |

### Current interpretation
- A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
- Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
- All visible A2 rows route to COUNCIL. Treat A2 performance as marginal-A2 performance, not clean executable-A2 performance.
### Council A1/A2 reachability audit
- Source: `council_reachability_audit_*.csv` from the Council skill. Diagnostic only; does not change labels or trading rules.
| A1_REACHABLE   | A2_EXECUTABLE_REACHABLE   | ZERO_TRADE_CAUSE        |   n_A1 |   n_A2 |   n_TRADE |   n_A2_to_COUNCIL |
|:---------------|:--------------------------|:------------------------|-------:|-------:|----------:|------------------:|
| NOT_EVALUABLE  | NOT_EVALUABLE             | INSUFFICIENT_CLEAN_ROWS |      0 |      0 |         0 |                 0 |

- Latest reachability audit source: `/content/bonde_repo/bonde_screener_cache/council_queues/council_reachability_audit_2026-05-15-spir-wrby-r4.csv`
- Top Council demotion reasons from latest audit:
| demotion_reason   |   rows |
|:------------------|-------:|
| rr_floor_fail     |      2 |
| UNKNOWN           |      1 |

- Interpretation: zero-TRADE appears driven by candidate quality/availability, not necessarily a Council routing bug.
### A1/A2 forward-return slices
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d   |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:----------------|-------------------:|------------------:|
| DELAYED_EP     | ACTIONABLE      | A2             | COUNCIL              |        1 |                0 | PARTIAL_OUTCOME |                nan |               nan |

### Caveats
- T+5 forward return is ticker-path evidence, not Kevin's realized P&L.
- Stops, skipped trades, council deferrals, and actual user execution are not reflected in raw T+5 close-to-close returns.
- A2 rows routed to COUNCIL are marginal by design; they should not be treated as clean executable A2 evidence.
- If A1 remains absent post-V5.9.19, test whether criteria are intentionally rare or unreachable.
