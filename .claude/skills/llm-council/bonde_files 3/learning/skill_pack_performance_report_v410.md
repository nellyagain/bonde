# Skill-Pack Performance Report — 2026-06-14

_v4.11 Session 2 patch. Outcome evaluation + slice-based performance summaries on skill-pack candidates and tickers. Cohort-aware confidence labels (Cell 20). No rule-change recommendations; no learned-pattern refresh._

## Summary

- Candidate-level rows evaluated: **9,333**
- Ticker-level rows evaluated: **8,177**
- Reviewed (joined to decision log): **1,714**
- Unreviewed: **6,463**
- Signal date range: **2026-04-24** → **2026-06-12**
- Latest cohort_end (ISO Sunday of latest signal_date): **2026-06-14**
- Cohort age (days since cohort_end): **0**
- Cohort maturity: t5=False · t10=False · t20=False

### Outcome status (ticker-level)

- EVALUATED_FULL: **2579**
- EVALUATED_PARTIAL: **5298**
- PENDING_NO_FUTURE_BARS: **298**
- NO_PRICE_DATA: **2**

## A. Reviewed vs unreviewed (ticker-level)

_Reviewed = decision-log-matched on `(ticker, signal_date)`. Strict join, no pack_date fallback (Session 1 design)._

| decision_log_matched   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   n_with_trigger_price |   win_rate_5d_all |   avg_ret_5d_all |   win_rate_5d_trig |   avg_ret_5d_trig |
|:-----------------------|---------:|------------------:|:------------|-----------------:|:----------------|-----------------------:|------------------:|-----------------:|-------------------:|------------------:|
| False                  |     6463 |                 0 | False       |              nan | PARTIAL_OUTCOME |                      0 |               nan |              nan |                nan |               nan |
| True                   |     1714 |                 0 | False       |              nan | PARTIAL_OUTCOME |                    758 |               nan |              nan |                nan |               nan |

## B. Setup-family performance (candidate-level)

_All observed setup_family values from the V5.4+ scanner are included; no whitelist filter applied here. The decision-log workflow's whitelist is intentionally separate._

| setup_family   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d     |   win_rate_5d_all |   avg_ret_5d_all |   n_evaluable_20d | confidence_20d   |   win_rate_20d_all |   avg_ret_20d_all |
|:---------------|---------:|------------------:|:------------|-----------------:|:------------------|------------------:|-----------------:|------------------:|:-----------------|-------------------:|------------------:|
| EP9M           |     4412 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| SLINGSHOT      |     1711 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| ACTIVE_BURST   |     1320 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| PAUSE          |      819 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| EP_ACTIVE      |      399 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| EP_SPIKE       |      307 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| DELAYED_EP     |      147 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| ANTICIPATION   |      132 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| PRE_BURST      |       60 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| DIAGNOSTICS    |       26 |                 7 | True        |               26 | ACTIONABLE_SAMPLE |             88.46 |             0.25 |               nan | IMMATURE_20D     |                nan |               nan |

## C. Source-type performance (ticker-level)

| source_type   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |
|:--------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|
| CANDIDATE     |     4191 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| EP9M_ONLY     |     3977 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| REFLEXIVE     |        9 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |

## D. EP_SPIKE / EP_ACTIVE / ACTIVE_BURST cohort slices (candidate-level)

_Slice comparison, not paired head-to-head (per Q2 design decision). Use these confidence labels — and `n_with_trigger_price` — when interpreting differences._

| setup_family   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   n_evaluable_20d | confidence_20d   |   win_rate_20d_all |   avg_ret_20d_all |
|:---------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|------------------:|:-----------------|-------------------:|------------------:|
| ACTIVE_BURST   |     1320 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |               nan | IMMATURE_20D     |                nan |               nan |
| EP_ACTIVE      |      399 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |               nan | IMMATURE_20D     |                nan |               nan |
| EP_SPIKE       |      307 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |               nan | IMMATURE_20D     |                nan |               nan |

## E. EP_SPIKE by origin_family (candidate-level)

_Which precursor family produced this EP_SPIKE row?_

| origin_family   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |
|:----------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|
| EP_ACTIVE       |      127 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| ACTIVE_BURST    |      105 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| EP9M            |       55 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| SLINGSHOT       |       20 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |

## F. EP9M-only ticker performance (ticker-level)

_Only rows where `source_type == "EP9M_ONLY"` (i.e. the ticker has only EP9M setup family in the skill pack and is not Reflexive/Thin Tape)._

| primary_setup   | extended_run_flag   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   avg_mfe_5d_all |   avg_mae_5d_all |
|:----------------|:--------------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|-----------------:|-----------------:|
| EP9M            | False               |     3638 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |
| EP9M            | True                |      339 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |

## G. extended_run_flag performance (ticker-level)

| extended_run_flag   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   avg_mfe_5d_all |   avg_mae_5d_all |
|:--------------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|-----------------:|-----------------:|
| False               |     6813 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |
| True                |     1364 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |

## H. bag_holder_flag performance (ticker-level)

| bag_holder_flag   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   avg_mfe_5d_all |   avg_mae_5d_all |
|:------------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|-----------------:|-----------------:|
| False             |     7572 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |
| True              |      605 |                 0 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |

## I. catalyst_grade performance (ticker-level, matched only)

_Filtered to rows that joined the decision log; catalyst_grade is a decision-log field._

| catalyst_grade   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d     |   win_rate_5d_all |   avg_ret_5d_all |
|:-----------------|---------:|------------------:|:------------|-----------------:|:------------------|------------------:|-----------------:|
| UNKNOWN          |      836 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| C                |      540 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| D                |      177 |                14 | True        |              177 | ACTIONABLE_SAMPLE |             44.07 |             0.75 |
| UNGRADED         |       88 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| B                |       55 |                 0 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| A                |       18 |                14 | True        |               18 | BUILDING_SAMPLE   |             27.78 |            -2.99 |

## J. Observations

- Reviewed vs unreviewed comparison present but at least one cohort is not ACTIONABLE_SAMPLE (reviewed: PARTIAL_OUTCOME, unreviewed: PARTIAL_OUTCOME). Insufficient evidence; monitor only.
- bag_holder_flag impact: at least one cohort not ACTIONABLE_SAMPLE; monitor only / immature cohort.
- extended_run_flag impact: at least one cohort not ACTIONABLE_SAMPLE; monitor only / immature cohort.
- EP_SPIKE vs ACTIVE_BURST: at least one cohort not ACTIONABLE_SAMPLE; monitor only.

## Join Diagnostics

_v4.12 patch — diagnostics only. Strict `(ticker, signal_date)` join is preserved. Pack-date matches are diagnostic only and are not used for attribution._

**Decision-log schema:**

- decision_log_rows_loaded: **1738**
- decision_log_date_semantics: **MIXED_V5_9_AND_LEGACY**
- has explicit `signal_date` column: **True**
- has explicit `review_date` column: **True**

**Join outcomes (decision-log perspective):**

- decision_log_rows_matched_on_signal_date: **1714**
- decision_log_rows_unmatched: **24**
- unmatched_due_to_date_mismatch (ticker is in skill pack, date differs): **17**
- unmatched_due_to_ticker_absent (ticker not in any skill pack): **7**
- candidate_rows_with_same_ticker_but_different_date: **5682**
- decision rows with pack_date match but no signal_date match: **0**

Pack-date matches are diagnostic only and are not used for attribution.

See `decision_log_join_diagnostics_v410.csv` for per-row classification (one row per skill-pack ticker × signal_date plus one row per DECISION_ONLY decision-log entry).

## K. Rule-change recommendations

**No rule changes recommended in Session 2.** Per the session-start agreement: Session 2 is performance reporting only; no rules are modified. Even when cohorts mature and patterns appear, rule changes require ≥2 consecutive ACTIONABLE cohorts agreeing (Cell 20 §K convention) and explicit manual evaluation. No `learned_patterns` refresh is performed in this session.
