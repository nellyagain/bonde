# ACTIVE_BURST Gate-6 Observational Watchlist — 2026-06-24

Status: OBSERVATIONAL_ONLY — no actionability-rule change.

Purpose: surface rows in `H_ACTIVE_BURST_GATE6_SOFTEN` without changing the decision log.

Rules:
- Rows remain `final_trade_status = REJECT` in the source decision log.
- Rows keep their original `action_label` and `planned_size`; this report must not be used as trade permission.
- This watchlist is for manual tradeability review only: check trigger, invalidation, R:R, liquidity, DTE, and hard rejects.
- Do not install a live REJECT→WATCH softening rule from this file alone.
- Keep collecting OOS shadow rows and compare against realized-R attribution before changing the actionability skill.

## Counts

- Full shadow candidates: **1**
- Tradeability-review watchlist rows: **0**
- Context-only rows excluded for missing trigger/invalidation: **1**
- Source CSV: `active_burst_gate6_observational_watchlist_v41329.csv`
- Shadow CSV: `active_burst_gate6_shadow_candidates_v41328.csv`

## Candidate rows

_No tradeability-review rows found. Shadow candidates exist, but all are context-only because trigger and/or invalidation is missing._
