# Bonde Learned Patterns

Generated: 2026-05-07

## Status

No ACTIVE learned patterns yet.

## Current operating rule

No learned-pattern overrides are active until evidence is mature and repeated.

The Bonde/Stockbee actionability skill and LLM council should treat this file as a null-pattern file:

- Do not apply any learned-pattern promotion.
- Do not apply any learned-pattern demotion.
- Leave `learned_pattern_matches` blank or use `NONE`.
- Do not change trading rules from immature cohorts.

## Evidence state

Current learning-loop evidence is still immature.

Use the following files for monitoring only when available:

- `weekly_learning_report_*.md`
- `skill_pack_performance_report_v410.md`
- `weekly_cohort_summary_v410.csv`
- `actionability_performance_summary_v410.csv`
- `setup_family_performance_summary_v410.csv`
- `decision_log_join_diagnostics_v410.csv`

## Rule-change policy

A pattern may become ACTIVE only when all are true:

1. The relevant cohort is mature.
2. The effect repeats across multiple cohorts.
3. Sample size is sufficient for the setup family / blocker type.
4. The proposed rule change does not violate hard-risk rules.
5. The user explicitly approves incorporating the pattern into the playbook.

## Hard-risk rules cannot be overridden by learned patterns

Do not override:

- Bag-holder / overhead-supply hard rejection.
- Failed EP hard rejection.
- DTE UNKNOWN non-promotion.
- Imminent earnings hard reject unless the main playbook formally adds a tactical exception.
- Dilution / offering hard reject.
- Deal-pinned / merger-arb hard reject.
- Severe extension without reset.
- EP_SPIKE overriding bag-holder.
- A1/A2 without valid trigger, invalidation, and R:R.

## Pattern table

| pattern_id | status | setup_family | condition | action | evidence_summary | first_seen | last_reviewed |
|---|---|---|---|---|---|---|---|
| NONE | INACTIVE | ALL | No mature repeated evidence yet | No learned-pattern action | Current cohorts immature; monitor only | 2026-05-07 | 2026-05-07 |

## Notes for Claude / Council

If this file is uploaded or present in `bonde_files/latest_context/`, explicitly state:

“Loaded `bonde_learned_patterns.md`: no ACTIVE learned patterns. Proceeding with base V5.9.x rules only.”
