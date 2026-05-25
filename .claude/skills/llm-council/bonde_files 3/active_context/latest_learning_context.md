# Active Learning Context

Generated: 2026-05-25
Status: AUTO_GENERATED_FROM_LEARNING_LOOP

## Current learning state

- Use weekly cohort reports for rule-change evidence.
- Do not change rules from immature T+5/T+10/T+20 data.
- Council rows remain calibration data only until outcome resolution matures.

## Executive digest excerpt

# Bonde Learning Loop Executive Digest — 2026-05-25

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-05-25 04:48 UTC_
_Notebook: v4.13.74 (digest surfaces entry-source classification)_

## 1. Today's required action
1. **No rule changes.** (§9 hypothesis tracker / verdict gates — all monitoring-only, no SUPPORTED verdicts)
2. **Wait for SLINGSHOT future bars.** Earliest T+5 maturity: **2026-05-22**. (§13)
3. **Watch A1/A2 zero-TRADE issue.** Confirm whether A1 is intentionally rare or unreachable and whether clean A1/A2 rows are over-routed. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is now pre-registered and measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **0**. (§15)

## 2. Changed since last run — prior run → 2026-05-25 04:48 UTC
- Prior digest date: **not available**
- Current digest date: **2026-05-25**
- Comparison window: **prior run → 2026-05-25**

### Pipeline changes
- SLINGSHOT decision-log target/R:R backfill: no new backfilled rows detected in this run.
- Tiny-geometry hygiene audit added / active: **2** rows flagged.
- Dedup diagnostics active: **7** raw full-plan+price rows → **4** unique ticker-date rows.
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
- Master decision-log rows: **738**
- Decision-log source files: **7**
- Latest decision-log sources: `daily_decision_log_2026-05-09.csv`, `daily_decision_log_2026-05-12.csv`, `daily_decision_log_2026-05-13.csv`, `daily_decision_log_2026-05-23.csv`, `sample_daily_decision_log.csv`
- 2026-05-15 decision log ingested: **NO**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    600 |
| REJECT               |    103 |
| COUNCIL              |     34 |
| TRADE                |      1 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |     14 |
| REJECT               |      7 |
| COUNCIL              |      6 |

### Corpus reconciliation
- Candidate decision-log files discovered: **9**
- Included decision-log files: **8**
- Excluded decision-log files: **1** (1 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **787 → 762 → 738**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
2. Post-2026-05-15 rows have zero TRADE rows (n=27). Confirm whether this is intended strictness or over-routing to COUNCIL/WATCH.
3. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable. Post-V5.9.19 rows have zero TRADE rows. Confirm whether clean A1/A2 rows are being over-routed to COUNCIL/WATCH.
4. Corpus reconciliation is now active: 1 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
5. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| ACTIVE_BURST   |       98 |               96 | ACTIONABLE_SAMPLE |         93.8776 |            34.0659 |        -1.23472   |
| PAUSE          |       53 |               44 | ACTIONABLE_SAMPLE |         94.3396 |            47.619  |         1.04069   |
| SLINGSHOT      |       42 |               41 | ACTIONABLE_SAMPLE |         97.619  |            26.8293 |        -2.44218   |
| EP_ACTIVE      |       38 |               33 | ACTIONABLE_SAMPLE |         89.4737 |            46.6667 |        -0.728472  |
| DELAYED_EP     |       21 |               17 | BUILDING_SAMPLE   |         95.2381 |            62.5    |        -0.37617   |
| ANTICIPATION   |        9 |                8 | LOW_SAMPLE        |        100      |            50      |        -0.0866923 |
| PRE_BURST      |        3 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |
| MOMENTUM_BURST |        1 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       20 |               18 | BUILDING_SAMPLE   |            66.6667 |          2.77643  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        6 |                6 | LOW_SAMPLE        |            50      |          1.25906  |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       23 |               22 | ACTIONABLE_SAMPLE |            40      |          1.1819   |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        6 |                5 | LOW_SAMPLE        |            25      |          0.210662 |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       33 |               26 | ACTIONABLE_SAMPLE |            33.3333 |         -0.261113 |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        5 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       10 |                8 | LOW_SAMPLE        |            62.5    |         -0.7628   |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |       34 |               34 | ACTIONABLE_SAMPLE |            29.4118 |         -1.89033  |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| SLINGSHOT      | REJECT          | D              | REJECT               |        5 |                5 | LOW_SAMPLE        |             0      |         -7.81828  |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |        8 |                7 | LOW_SAMPLE        |            40      |         -6.22877  |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       24 |               24 | ACTIONABLE_SAMPLE |            29.1667 |         -2.56178  |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       15 |               15 | BUILDING_SAMPLE   |            46.6667 |         -2.17819  |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       38 |               38 | ACTIONABLE_SAMPLE |            34.2105 |         -2.11297  |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |       34 |               34 | ACTIONABLE_SAMPLE |            29.4118 |         -1.89033  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       10 |                8 | LOW_SAMPLE        |            62.5    |         -0.7628   |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        5 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
### A1/A2 count and routing check
| scope          | action_label   | final_trade_status   | setup_family   |   n_rows |
|:---------------|:---------------|:---------------------|:---------------|---------:|
| ALL_ROWS       | A1             | TRADE                | ACTIVE_BURST   |        1 |
