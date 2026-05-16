# Council Context Manifest

Generated: 2026-05-16
Target folder: `.claude/skills/llm-council/bonde_files 3/active_context/`

Use only the active files listed below as current council context. Historical files, dated files, and root-level files are not current instructions unless explicitly referenced by the user.

| File | Role | Status | Notes |
|---|---|---|---|
| `latest_candidate_context.md` | Candidate context | LOADED | Current 2026-05-15 council packet context. Candidates: SPIR and WRBY, both `final_trade_status=COUNCIL`. |
| `latest_learning_context.md` | Learning context | LOADED | Current learning state. No active learned-pattern overrides; W20 cohort is immature. |
| `latest_market_context.md` | Market context | LOADED | Nasdaq extension / tactical market context. Advisory only; not a hard actionability gate. Current read: risk-on but tactically extended. |
| `latest_regime_context.md` | Regime context | LOADED | Market regime module says Risk-On, high confidence, normal sizing hint. Advisory facts only. |
| `council_context_manifest.md` | Context manifest | LOADED | This file. Tells the council which active context files are current. |

## Optional context files not required by default

These files are optional and should not be treated as missing-required unless this manifest is changed to require them:

- `latest_accountability_context.md`
- `latest_skill_context.md`

## Current daily packet expected

Use files in `../current/` as the current daily decision packet:

- `daily_decision_log_2026-05-15_council_subset.csv` — LOADED, V5.9.19-compatible subset, includes `final_trade_status` for council-routed rows.
- `council_queue_2026-05-15.csv` — LOADED, derived from rows where `final_trade_status=COUNCIL`.
- `bonde_skill_pack_2026-05-15_council_subset.csv` — LOADED, current candidate evidence subset for council tickers.

## Current council candidate set

The current run should review only:

- SPIR
- WRBY

Do not use old WCC/JBHT/NVMI/WERN files or old root-level dated files as the current packet.

## Council use rules

1. Use files in `active_context/` as current context.
2. Use files in `current/` as the current daily decision packet.
3. Use files in `learning/` as historical/base-rate context.
4. Do not scan loose root-level dated files as current context.
5. Market and regime context are advisory. They can affect execution posture, order type, and portfolio heat, but must not override candidate-level `final_trade_status` or hard rejects.
6. The council report must include a `Context Files Loaded` section and state whether each expected file was loaded, missing, optional, or stale.
7. If outcome/base-rate evidence is immature, state that the verdict is playbook-only and should be logged for calibration.
