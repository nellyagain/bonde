# Council Context Manifest

Generated: 2026-05-15
Target folder: `.claude/skills/llm-council/bonde_files 3/active_context/`

Use only the active files listed below as current council context. Historical files, dated files, and root-level files are not current instructions unless explicitly referenced by the user.

| File | Role | Status | Notes |
|---|---|---|---|
| `latest_candidate_context.md` | Candidate context | EXPECTED | Current candidate/council packet context when generated. Missing should be stated in the council report. |
| `latest_learning_context.md` | Learning context | EXPECTED | Current learning-loop summary when generated. Missing should be stated in the council report. |
| `latest_market_context.md` | Market context | LOADED | Nasdaq extension / market regime context. Advisory only; not a hard actionability gate. Current read: risk-on but tactically extended. |
| `council_context_manifest.md` | Context manifest | LOADED | This file. Tells the council which active context files are current. |

## Optional context files not required by default

These files are optional and should not be treated as missing-required unless this manifest is changed to require them:

- `latest_regime_context.md`
- `latest_accountability_context.md`
- `latest_skill_context.md`

## Council use rules

1. Use files in `active_context/` as current context.
2. Use files in `current/` as the current daily decision packet.
3. Use files in `learning/` as historical/base-rate context.
4. Do not scan loose root-level dated files as current context.
5. `latest_market_context.md` is advisory market context. It can affect execution posture, order type, and portfolio heat, but it does not override candidate-level `final_trade_status` or hard rejects.
6. The council report must include a `Context Files Loaded` section and state whether each expected file was loaded, missing, optional, or stale.
