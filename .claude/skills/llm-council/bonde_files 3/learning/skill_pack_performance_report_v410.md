# Skill-Pack Performance Report — 2026-06-24

_v4.11 Session 2 patch. Outcome evaluation + slice-based performance summaries on skill-pack candidates and tickers. Cohort-aware confidence labels (Cell 20). No rule-change recommendations; no learned-pattern refresh._

## Summary

- Candidate-level rows evaluated: **11,267**
- Ticker-level rows evaluated: **9,966**
- Reviewed (joined to decision log): **2,146**
- Unreviewed: **7,820**
- Signal date range: **2026-04-24** → **2026-06-23**
- Latest cohort_end (ISO Sunday of latest signal_date): **2026-06-28**
- Cohort age (days since cohort_end): **-4**
- Cohort maturity: t5=False · t10=False · t20=False

### Outcome status (ticker-level)

- EVALUATED_FULL: **4278**
- EVALUATED_PARTIAL: **5341**
- PENDING_NO_FUTURE_BARS: **339**
- NO_PRICE_DATA: **8**

## A. Reviewed vs unreviewed (ticker-level)

_Reviewed = decision-log-matched on `(ticker, signal_date)`. Strict join, no pack_date fallback (Session 1 design)._

| decision_log_matched   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   n_with_trigger_price |   win_rate_5d_all |   avg_ret_5d_all |   win_rate_5d_trig |   avg_ret_5d_trig |
|:-----------------------|---------:|------------------:|:------------|-----------------:|:----------------|-----------------------:|------------------:|-----------------:|-------------------:|------------------:|
| False                  |     7820 |                -4 | False       |              nan | PARTIAL_OUTCOME |                      0 |               nan |              nan |                nan |               nan |
| True                   |     2146 |                -4 | False       |              nan | PARTIAL_OUTCOME |                    958 |               nan |              nan |                nan |               nan |

## B. Setup-family performance (candidate-level)

_All observed setup_family values from the V5.4+ scanner are included; no whitelist filter applied here. The decision-log workflow's whitelist is intentionally separate._

| setup_family   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d     |   win_rate_5d_all |   avg_ret_5d_all |   n_evaluable_20d | confidence_20d   |   win_rate_20d_all |   avg_ret_20d_all |
|:---------------|---------:|------------------:|:------------|-----------------:|:------------------|------------------:|-----------------:|------------------:|:-----------------|-------------------:|------------------:|
| EP9M           |     5405 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| SLINGSHOT      |     2086 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| ACTIVE_BURST   |     1531 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| PAUSE          |     1003 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| EP_ACTIVE      |      465 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| EP_SPIKE       |      340 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| DELAYED_EP     |      181 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| ANTICIPATION   |      156 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| PRE_BURST      |       74 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |               nan | IMMATURE_20D     |                nan |               nan |
| DIAGNOSTICS    |       26 |                17 | True        |               26 | ACTIONABLE_SAMPLE |             88.46 |             0.25 |               nan | IMMATURE_20D     |                nan |               nan |

## C. Source-type performance (ticker-level)

| source_type   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |
|:--------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|
| CANDIDATE     |     5042 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| EP9M_ONLY     |     4913 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| REFLEXIVE     |       11 |                 3 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |

## D. EP_SPIKE / EP_ACTIVE / ACTIVE_BURST cohort slices (candidate-level)

_Slice comparison, not paired head-to-head (per Q2 design decision). Use these confidence labels — and `n_with_trigger_price` — when interpreting differences._

| setup_family   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   n_evaluable_20d | confidence_20d   |   win_rate_20d_all |   avg_ret_20d_all |
|:---------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|------------------:|:-----------------|-------------------:|------------------:|
| ACTIVE_BURST   |     1531 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |               nan | IMMATURE_20D     |                nan |               nan |
| EP_ACTIVE      |      465 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |               nan | IMMATURE_20D     |                nan |               nan |
| EP_SPIKE       |      340 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |               nan | IMMATURE_20D     |                nan |               nan |

## E. EP_SPIKE by origin_family (candidate-level)

_Which precursor family produced this EP_SPIKE row?_

| origin_family   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |
|:----------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|
| EP_ACTIVE       |      141 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| ACTIVE_BURST    |      116 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| EP9M            |       59 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |
| SLINGSHOT       |       24 |                 3 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |

## F. EP9M-only ticker performance (ticker-level)

_Only rows where `source_type == "EP9M_ONLY"` (i.e. the ticker has only EP9M setup family in the skill pack and is not Reflexive/Thin Tape)._

| primary_setup   | extended_run_flag   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   avg_mfe_5d_all |   avg_mae_5d_all |
|:----------------|:--------------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|-----------------:|-----------------:|
| EP9M            | False               |     4541 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |
| EP9M            | True                |      372 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |

## G. extended_run_flag performance (ticker-level)

| extended_run_flag   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   avg_mfe_5d_all |   avg_mae_5d_all |
|:--------------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|-----------------:|-----------------:|
| False               |     8417 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |
| True                |     1549 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |

## H. bag_holder_flag performance (ticker-level)

| bag_holder_flag   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d   |   win_rate_5d_all |   avg_ret_5d_all |   avg_mfe_5d_all |   avg_mae_5d_all |
|:------------------|---------:|------------------:|:------------|-----------------:|:----------------|------------------:|-----------------:|-----------------:|-----------------:|
| False             |     9265 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |
| True              |      701 |                -4 | False       |              nan | PARTIAL_OUTCOME |               nan |              nan |              nan |              nan |

## I. catalyst_grade performance (ticker-level, matched only)

_Filtered to rows that joined the decision log; catalyst_grade is a decision-log field._

| catalyst_grade   |   n_rows |   cohort_age_days | mature_t5   |   n_evaluable_5d | confidence_5d     |   win_rate_5d_all |   avg_ret_5d_all |
|:-----------------|---------:|------------------:|:------------|-----------------:|:------------------|------------------:|-----------------:|
| C                |      929 |                -4 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| UNKNOWN          |      873 |                 3 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| D                |      180 |                 3 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| UNGRADED         |       88 |                10 | True        |               87 | ACTIONABLE_SAMPLE |             77.01 |             2.73 |
| B                |       58 |                 3 | False       |              nan | PARTIAL_OUTCOME   |            nan    |           nan    |
| A                |       18 |                24 | True        |               18 | BUILDING_SAMPLE   |             27.78 |            -2.99 |

## J. Observations

- Reviewed vs unreviewed comparison present but at least one cohort is not ACTIONABLE_SAMPLE (reviewed: PARTIAL_OUTCOME, unreviewed: PARTIAL_OUTCOME). Insufficient evidence; monitor only.
- bag_holder_flag impact: at least one cohort not ACTIONABLE_SAMPLE; monitor only / immature cohort.
- extended_run_flag impact: at least one cohort not ACTIONABLE_SAMPLE; monitor only / immature cohort.
- EP_SPIKE vs ACTIVE_BURST: at least one cohort not ACTIONABLE_SAMPLE; monitor only.

## Join Diagnostics

_v4.12 patch — diagnostics only. Strict `(ticker, signal_date)` join is preserved. Pack-date matches are diagnostic only and are not used for attribution._

**Decision-log schema:**

- decision_log_rows_loaded: **2170**
- decision_log_date_semantics: **MIXED_V5_9_AND_LEGACY**
- has explicit `signal_date` column: **True**
- has explicit `review_date` column: **True**

**Join outcomes (decision-log perspective):**

- decision_log_rows_matched_on_signal_date: **2146**
- decision_log_rows_unmatched: **24**
- unmatched_due_to_date_mismatch (ticker is in skill pack, date differs): **20**
- unmatched_due_to_ticker_absent (ticker not in any skill pack): **4**
- candidate_rows_with_same_ticker_but_different_date: **7334**
- decision rows with pack_date match but no signal_date match: **0**

Pack-date matches are diagnostic only and are not used for attribution.

See `decision_log_join_diagnostics_v410.csv` for per-row classification (one row per skill-pack ticker × signal_date plus one row per DECISION_ONLY decision-log entry).

## K. Rule-change recommendations

**No rule changes recommended in Session 2.** Per the session-start agreement: Session 2 is performance reporting only; no rules are modified. Even when cohorts mature and patterns appear, rule changes require ≥2 consecutive ACTIONABLE cohorts agreeing (Cell 20 §K convention) and explicit manual evaluation. No `learned_patterns` refresh is performed in this session.
