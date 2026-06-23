# Council Context Manifest

Generated: 2026-06-23
Packet date: 2026-06-23
Target folder: `bonde_files 3/`

Use this package as the current council context bundle. Do not scan stale root-level dated files as current context.

## Folder roles

- `current/` — daily packet: decision log, council queue, and skill pack.
- `active_context/` — stable current context files used by the council.
- `learning/` — weekly/base-rate/reference context used as advisory evidence only.

## Current daily packet

- `bonde_skill_pack_2026-05-15.csv` — LOADED
- `council_queue_2026-06-23.csv` — LOADED
- `daily_decision_log_2026-06-23.csv` — LOADED

## Active context files

- `latest_candidate_context.md` — LOADED — candidate context
- `latest_learning_context.md` — LOADED — learning context
- `latest_market_context.md` — LOADED — market context
- `latest_sugar_babies_context.md` — LOADED — Sugar Babies overlay context
- `latest_sugar_babies_ticker_context.csv` — LOADED — Sugar Babies overlay context

## Learning/reference files

- `actionability_performance_summary_v410.csv` — LOADED
- `active_burst_gate6_observational_watchlist_latest.md` — LOADED
- `active_burst_gate6_observational_watchlist_v41329.csv` — LOADED
- `active_burst_gate6_shadow_candidates_v41328.csv` — LOADED
- `bonde_learned_patterns.md` — LOADED
- `broker_export_normalization_audit_latest.md` — LOADED
- `broker_export_normalized_trades_latest.csv` — LOADED
- `catalyst_x_family_summary_v410.csv` — LOADED
- `council_disagreements_resolved.csv` — LOADED
- `council_resolver_report_2026-06-23.md` — LOADED
- `daily_learning_report_2026-06-23.md` — LOADED
- `day1_shape_coverage_v413.csv` — LOADED
- `day1_shape_verdicts_v413.csv` — LOADED
- `decision_log_corpus_reconciliation_history.csv` — LOADED
- `decision_log_corpus_reconciliation_summary_latest.csv` — LOADED
- `decision_log_discovery_audit_latest.csv` — LOADED
- `decision_log_discovery_audit_latest.md` — LOADED
- `hypothesis_tracker_latest.md` — LOADED
- `hypothesis_tracker_summary_v41328.csv` — LOADED
- `latest_sugar_babies_ticker_context.csv` — LOADED
- `learning_loop_executive_digest_2026-06-23.md` — LOADED
- `learning_loop_executive_digest_latest.md` — LOADED
- `probe_trade_experiment_events_2026-06-23.csv` — LOADED
- `probe_trade_experiment_summary_2026-06-23.csv` — LOADED
- `probe_trade_learning_loop_readiness_latest.json` — LOADED
- `realized_pnl_attribution_latest.md` — LOADED
- `realized_pnl_attribution_summary_latest.csv` — LOADED
- `realized_trades_master_latest.csv` — LOADED
- `rr_target_audit_report_v410.md` — LOADED
- `rr_target_audit_v410.csv` — LOADED
- `setup_family_performance_summary_v410.csv` — LOADED
- `skill_pack_performance_report_v410.md` — LOADED
- `slingshot_bucket_performance_v41314.csv` — LOADED
- `slingshot_diagnostics_report_v41314.md` — LOADED
- `slingshot_evaluability_audit_latest.csv` — LOADED
- `slingshot_evaluability_audit_latest.md` — LOADED
- `slingshot_evaluability_enhanced_latest.csv` — LOADED
- `slingshot_evaluability_scope_summary_latest.csv` — LOADED
- `slingshot_evaluability_setup_family_summary_latest.csv` — LOADED
- `slingshot_evaluability_signal_date_summary_latest.csv` — LOADED
- `slingshot_evaluability_stage_summary_latest.csv` — LOADED
- `slingshot_evaluability_summary_latest.csv` — LOADED
- `slingshot_scope_price_diagnostics_latest.md` — LOADED
- `source_health_corpus_metadata_latest.csv` — LOADED
- `sugar_babies_overlay_report_v410.md` — LOADED
- `sugar_babies_overlay_summary_v410.csv` — LOADED
- `weekly_cohort_summary_v410.csv` — LOADED
- `weekly_learning_report_2026-W26.md` — LOADED

## Current council candidate set

_No explicit council candidates found._

## Council use rules

1. `final_trade_status` is the executable/routing field.
2. `tier` is source/dashboard context only and is not trade authorization.
3. Market, regime, learning, and Sugar Babies context are advisory only.
4. Sugar Babies may raise review priority or confidence framing, but must not override R:R, DTE, hard rejects, failed EP, bag-holder, dilution/offering, data-quality, or `final_trade_status`.
5. If outcome/base-rate evidence is immature, state that verdicts are playbook-only and should be logged for calibration.
6. If candidates are promoted, include Portfolio Heat and order-duration guardrails.
7. `learning/learning_loop_executive_digest_latest.md` is the primary human-readable summary of latest learning-loop findings and caveats.
