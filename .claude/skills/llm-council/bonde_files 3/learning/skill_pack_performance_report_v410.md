# Skill-Pack Performance Report — 2026-05-19

_v4.11 Session 2 patch. Outcome evaluation + slice-based performance summaries on skill-pack candidates and tickers. Cohort-aware confidence labels (Cell 20). No rule-change recommendations; no learned-pattern refresh._

## Summary

- Candidate-level rows evaluated: **0**
- Ticker-level rows evaluated: **0**
- Reviewed (joined to decision log): **0**
- Unreviewed: **0**
- Signal date range: **(none)** → **(none)**
- Latest cohort_end (ISO Sunday of latest signal_date): **(none)**
- Cohort age (days since cohort_end): **nan**
- Cohort maturity: t5=False · t10=False · t20=False

### Outcome status (ticker-level)

- EVALUATED_FULL: **0**
- EVALUATED_PARTIAL: **0**
- PENDING_NO_FUTURE_BARS: **0**
- NO_PRICE_DATA: **0**

## A. Reviewed vs unreviewed (ticker-level)

_Reviewed = decision-log-matched on `(ticker, signal_date)`. Strict join, no pack_date fallback (Session 1 design)._

_No rows._

## B. Setup-family performance (candidate-level)

_All observed setup_family values from the V5.4+ scanner are included; no whitelist filter applied here. The decision-log workflow's whitelist is intentionally separate._

_No rows._

## C. Source-type performance (ticker-level)

_No rows._

## D. EP_SPIKE / EP_ACTIVE / ACTIVE_BURST cohort slices (candidate-level)

_Slice comparison, not paired head-to-head (per Q2 design decision). Use these confidence labels — and `n_with_trigger_price` — when interpreting differences._

_No rows._

## E. EP_SPIKE by origin_family (candidate-level)

_Which precursor family produced this EP_SPIKE row?_

_No rows._

## F. EP9M-only ticker performance (ticker-level)

_Only rows where `source_type == "EP9M_ONLY"` (i.e. the ticker has only EP9M setup family in the skill pack and is not Reflexive/Thin Tape)._

_No rows._

## G. extended_run_flag performance (ticker-level)

_No rows._

## H. bag_holder_flag performance (ticker-level)

_No rows._

## I. catalyst_grade performance (ticker-level, matched only)

_Filtered to rows that joined the decision log; catalyst_grade is a decision-log field._

_No rows._

## J. Observations

- No mature, ACTIONABLE_SAMPLE cohort observations available this run.

## Join Diagnostics

_v4.12 patch — diagnostics only. Strict `(ticker, signal_date)` join is preserved. Pack-date matches are diagnostic only and are not used for attribution._

**Decision-log schema:**

- decision_log_rows_loaded: **90**
- decision_log_date_semantics: **EXPLICIT_V5_9**
- has explicit `signal_date` column: **True**
- has explicit `review_date` column: **True**

**Join outcomes (decision-log perspective):**

- decision_log_rows_matched_on_signal_date: **0**
- decision_log_rows_unmatched: **90**
- unmatched_due_to_date_mismatch (ticker is in skill pack, date differs): **0**
- unmatched_due_to_ticker_absent (ticker not in any skill pack): **90**
- candidate_rows_with_same_ticker_but_different_date: **0**
- decision rows with pack_date match but no signal_date match: **0**

Pack-date matches are diagnostic only and are not used for attribution.

See `decision_log_join_diagnostics_v410.csv` for per-row classification (one row per skill-pack ticker × signal_date plus one row per DECISION_ONLY decision-log entry).

## K. Rule-change recommendations

**No rule changes recommended in Session 2.** Per the session-start agreement: Session 2 is performance reporting only; no rules are modified. Even when cohorts mature and patterns appear, rule changes require ≥2 consecutive ACTIONABLE cohorts agreeing (Cell 20 §K convention) and explicit manual evaluation. No `learned_patterns` refresh is performed in this session.
