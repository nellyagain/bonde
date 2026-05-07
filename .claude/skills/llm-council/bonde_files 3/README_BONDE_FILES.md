# Bonde Council Context Files

Place this `bonde_files/` folder in the Claude Code repo/workspace.

## Key folders

### `bonde_stockbee_actionability/`

Core Bonde/Stockbee actionability playbook files. The LLM council should read these to understand the V5.9.x rules, gates, CSV contract, DTE rules, EP rules, burst gates, and catalyst checks.

### `latest_context/`

Latest daily files from the live workflow. This may include:

- `council_queue_*.csv`
- `daily_decision_log_*.csv`
- `bonde_skill_pack_*.csv`
- `skill_pack_performance_report*.md`
- `weekly_learning_report_*.md`
- `rule_diagnostics*.csv`
- `reviewed_vs_unreviewed_summary*.csv`
- `skill_pack_ticker_outcomes_enriched*.csv`
- `skill_pack_candidate_outcomes_enriched*.csv`
- `decision_log_join_diagnostics*.csv`

## Council usage

When running the council, ask it to inspect:

- `bonde_files/bonde_stockbee_actionability/`
- `bonde_files/latest_context/`

Outcome/base-rate data is an overlay only. It must not override hard rejects unless the main Bonde actionability skill has formally changed the rule.

## Minimum daily council workflow

1. Export this folder from Colab.
2. Upload or sync `bonde_files/` into the Claude Code repo/workspace.
3. Run the council on the relevant `council_queue_<SIG>.csv` row or prompt text.
4. Save the council report/transcript back into the repo or Drive for later learning-loop calibration.
