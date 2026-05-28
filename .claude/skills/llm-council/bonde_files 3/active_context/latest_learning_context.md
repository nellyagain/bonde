# Active Learning Context

Generated: 2026-05-28
Status: AUTO_GENERATED_FROM_LEARNING_LOOP

## Current learning state

- Use weekly cohort reports for rule-change evidence.
- Do not change rules from immature T+5/T+10/T+20 data.
- Council rows remain calibration data only until outcome resolution matures.

## Executive digest excerpt

# Bonde Learning Loop Executive Digest — 2026-05-28

_Primary review artifact. Use the underlying CSVs only when a specific number needs audit._
_Run timestamp: 2026-05-28 14:29 UTC_
_Notebook: v4.14.11 — digest reconciliation + rule-readiness schema/zip/GitHub sync/source-selection hotfixes_

## 1. Today's required action
1. **No automatic rule changes.** Any READY/SUPPORTED item from the rule-readiness monitor still requires manual review before patching. (§9 hypothesis tracker / verdict gates)
2. **Review first SLINGSHOT OK-evaluable cohort under H_SLINGSHOT_TARGET_BASIS; no rule change yet.** OK_EVALUABLE rows: **5**; rows ≥5 future bars: **83**; unique full-plan+price ticker-date rows: **132**. (§13)
3. **A1 remains absent; TRADE path is now alive.** Monitor whether A1 is intentionally rare or unreachable. Post-V5.9.19 TRADE rows: **9**; A1 rows: **0**; A2 rows: **10**. (§6)
4. **Track KK confirmation.** H_KK_CONFIRMATION is pre-registered, no sample yet, measurement-only; do not hard-gate Bonde rows from KK yet. (§9)
5. **Track Sugar Babies OOS.** Current signal is context-only / overlay-not-rule-evidence. (§14)
6. **Check realized P&L once `n_with_realized_r >= 30`.** Current n = **0**. (§15)
7. **No rule-readiness item is ready.** Monitor candidates: H_EP_ACTIVE_FADE_RISK, H_MB_EXIT_DAY3_FILTER. Soft cautions: H_ACTIVE_BURST_MB_EXIT — manual-review-only. (§RR)
   _Rule-readiness source: rule_readiness_monitor_latest.csv; ID column: candidate_rule_id; rows: 3._

## 2. Changed since last run — 2026-05-28 14:13 UTC → 2026-05-28 14:29 UTC
Changed since last run: same-run-date prior snapshot detected; comparison suppressed. Showing current status only.

### Current pipeline status
- SLINGSHOT decision-log target/R:R backfill: no backfilled rows.
- Tiny-geometry hygiene flagged rows: **8**.
- Dedup diagnostics: **263** raw full-plan+price rows → **132** unique ticker-date rows.
- SLINGSHOT current state: **OK_EVALUABLE rows = 5** (non-zero; H_SLINGSHOT_TARGET_BASIS measurement live). Rows ≥5 future bars: 83.

### Current trading-state
- Post-V5.9.19 TRADE rows: **9**; A1: **0**; A2: **10**. TRADE path is alive.
- KK confirmation: pre-registered, no sample yet, measurement-only.
- KK funnel audit (`kk_gate_funnel_latest.*`): not present.
- PAUSE reconciliation: main tracker = **WATCHING_NOT_RULE_EVIDENCE**; diagnostic = **REJECTED / NOT_CONFIRMED**.
- Realized P&L: `n_with_realized_r` = **0** (threshold 30).

### Rule-readiness state
- No READY/SUPPORTED items. Candidates (2): H_EP_ACTIVE_FADE_RISK, H_MB_EXIT_DAY3_FILTER. Soft cautions (1): H_ACTIVE_BURST_MB_EXIT. Candidate/manual-review-only — no rule authorization.

### Open follow-ups carried forward
- ACLX 4-row diagnostic appearance: visible in dedup diagnostics; not a trading-rule issue.
- Float-precision drift in tiny-geometry flags across sources: known, low materiality; use tolerance-aware comparisons.

## 3. Operational status
- Master decision-log rows: **888**
- Decision-log source files: **7**
- Latest decision-log sources: `daily_decision_log_2026-05-09.csv`, `daily_decision_log_2026-05-12.csv`, `daily_decision_log_2026-05-13.csv`, `daily_decision_log_2026-05-27.csv`, `sample_daily_decision_log.csv`
- 2026-05-15 decision log ingested: **NO**

### final_trade_status distribution
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    738 |
| REJECT               |    110 |
| COUNCIL              |     30 |
| TRADE                |     10 |

### Post-V5.9.19 distribution check
| final_trade_status   |   rows |
|:---------------------|-------:|
| WATCH                |    152 |
| REJECT               |     14 |
| TRADE                |      9 |
| COUNCIL              |      2 |

### Corpus reconciliation
- Candidate decision-log files discovered: **9**
- Included decision-log files: **8**
- Excluded decision-log files: **1** (1 duplicate/lower-score files)
- Raw included rows → normalized rows → master rows: **937 → 912 → 888**
- Rows removed by final master de-duplication: **24**
- EP9M setup-family rows raw included → master: **0 → 0**
- File-level audit: `decision_log_discovery_audit_latest.md`
- Scope note: row-count drift versus prior digests should be interpreted through the file-level audit before drawing setup-performance conclusions.

## 4. Executive interpretation
Current loop status: **operationally healthy, evidence still immature**. This digest is monitoring context, not rule-change permission.
1. Action-label inversion is the highest-priority systemic investigation: at least one lower-quality label is outperforming a higher-quality label within the same setup family.
2. A1/A2 executable-signal health needs direct tracking: A1 has zero post-V5.9.19 rows. Confirm whether A1 is intentionally rare or unreachable.
3. Corpus reconciliation is now active: 1 decision-log file(s) excluded and 24 row(s) removed by final de-duplication. Check the audit before comparing this digest to prior row counts.
4. No rule changes are authorized from this digest. Use it to prioritize investigations and council context only.

## 5. Key findings from current data
### Setup-family summary
| setup_family   |   n_rows |   n_evaluable_5d | confidence_5d     |   pct_triggered |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|---------:|-----------------:|:------------------|----------------:|-------------------:|------------------:|
| ACTIVE_BURST   |      116 |               96 | ACTIONABLE_SAMPLE |         88.7931 |            34.0659 |        -1.23472   |
| PAUSE          |       48 |               44 | ACTIONABLE_SAMPLE |         93.75   |            47.619  |         1.04069   |
| SLINGSHOT      |      170 |               41 | ACTIONABLE_SAMPLE |         81.1765 |            26.8293 |        -2.44218   |
| EP_ACTIVE      |       42 |               33 | ACTIONABLE_SAMPLE |         76.1905 |            46.6667 |        -0.728472  |
| DELAYED_EP     |       28 |               17 | BUILDING_SAMPLE   |         92.8571 |            62.5    |        -0.37617   |
| ANTICIPATION   |        8 |                8 | LOW_SAMPLE        |        100      |            50      |        -0.0866923 |
| MOMENTUM_BURST |        1 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |
| PRE_BURST      |        1 |                1 | LOW_SAMPLE        |          0      |           nan      |       nan         |
| EP_SPIKE       |        3 |                0 | PARTIAL_OUTCOME   |         66.6667 |           nan      |       nan         |

### Actionability slices to monitor
**Best current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| PAUSE          | WATCH_ONLY      | C              | WATCH                |       21 |               18 | BUILDING_SAMPLE   |            66.6667 |          2.77643  |
| ACTIVE_BURST   | ACTIONABLE      | A2             | COUNCIL              |        6 |                6 | LOW_SAMPLE        |            50      |          1.25906  |
| ACTIVE_BURST   | WATCH_ONLY      | B              | WATCH                |       24 |               22 | ACTIONABLE_SAMPLE |            40      |          1.1819   |
| ACTIVE_BURST   | WATCH_ONLY      | B              | COUNCIL              |        5 |                5 | LOW_SAMPLE        |            25      |          0.210662 |
| PAUSE          | WATCH_ONLY      | B              | WATCH                |       27 |               26 | ACTIONABLE_SAMPLE |            33.3333 |         -0.261113 |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        5 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       11 |                8 | LOW_SAMPLE        |            62.5    |         -0.7628   |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |      156 |               34 | ACTIONABLE_SAMPLE |            29.4118 |         -1.89033  |

**Weak current slices (monitoring only):**
| setup_family   | review_bucket   | action_label   | final_trade_status   |   n_rows |   n_evaluable_5d | confidence_5d     |   win_rate_5d_trig |   avg_ret_5d_trig |
|:---------------|:----------------|:---------------|:---------------------|---------:|-----------------:|:------------------|-------------------:|------------------:|
| SLINGSHOT      | REJECT          | D              | REJECT               |        5 |                5 | LOW_SAMPLE        |             0      |         -7.81828  |
| EP_ACTIVE      | WATCH_ONLY      | B              | COUNCIL              |        7 |                7 | LOW_SAMPLE        |            40      |         -6.22877  |
| ACTIVE_BURST   | WATCH_ONLY      | C              | WATCH                |       29 |               24 | ACTIONABLE_SAMPLE |            29.1667 |         -2.56178  |
| EP_ACTIVE      | WATCH_ONLY      | C              | WATCH                |       17 |               15 | BUILDING_SAMPLE   |            46.6667 |         -2.17819  |
| ACTIVE_BURST   | REJECT          | D              | REJECT               |       48 |               38 | ACTIONABLE_SAMPLE |            34.2105 |         -2.11297  |
| SLINGSHOT      | WATCH_ONLY      | C              | WATCH                |      156 |               34 | ACTIONABLE_SAMPLE |            29.4118 |         -1.89033  |
| DELAYED_EP     | WATCH_ONLY      | B              | WATCH                |       11 |                8 | LOW_SAMPLE        |            62.5    |         -0.7628   |
| ANTICIPATION   | WATCH_ONLY      | C              | WATCH                |        5 |                5 | LOW_SAMPLE        |            60      |         -0.268804 |


## 6. A1 / A2 executable-signal health
Purpose: check whether the actionability layer is producing true executable candidates or routing everything to council/watch.
