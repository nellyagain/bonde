# Bonde Learning Report — 2026-05-17

_v4.10 daily report. For evidence-grade rule-change conversations, use the weekly cohort report instead._

## Scope

- Rows in master decision log: 0
- Rows with evaluated / partial outcomes: 0
- Rows pending future bars or missing data: 0

## Reading this report

- Every metric has two views: `_all` (every row) and `_trig` (rows where the entry trigger fired or no trigger price was set).
- `confidence_5d` flags whether a row is evidence (`ACTIONABLE_SAMPLE` ≥ 20 evaluable, `BUILDING_SAMPLE` 10–19, `LOW_SAMPLE` < 10, `PARTIAL_OUTCOME` 0). Do not act on `LOW_SAMPLE` or `PARTIAL_OUTCOME` rows.
- `confidence_20d` flags whether the longer-window data is mature (≥ 30 evaluable rows at T+20).
- Rule-change discussions belong in the weekly cohort report, not here.
- `final_trade_status` is the executable decision field. `tier` is a source/dashboard focus tier and must not be read as trade permission.

## Watch Items

- No watch items met the threshold this run.

## Setup-Family Summary

_Whitelisted setup families only. Workflow/source classifications (EXCLUSION, DIAGNOSTIC, etc.) are in the source-bucket section below._

_No rows._

## Source-Bucket Summary

_For audit only. These are not setup families and should not be used to evaluate setup performance._

_No rows._

## Actionability Summary

_No rows._

## Catalyst × Setup-Family Summary

_Stratifies catalyst grade by setup family to prevent Simpson's-paradox readings (e.g., Grade C appearing better than Grade A only because Grade C names happen to be in stronger families)._

_No rows._

## Pre-Burst Conversion Summary

_No rows._

## Reject Audit Summary

_No rows._

## Catalyst Summary (un-stratified)

_Kept for backward compatibility. The catalyst × setup-family table above is the right view for decision-making._

_No rows._

## Notes

- Pre-burst rows are evaluated by trigger conversion, not day-zero P&L.
- Active-burst rows are evaluated over T+1/T+3/T+5; KK extension/monster rows over T+10/T+20 once mature.
- Win rate uses dropna() — pending rows do not count as losses (this is a v4.10 bug fix; prior versions understated win rate).
- Do not change rules from one day of data. Evidence for rule changes lives in the weekly cohort report.
