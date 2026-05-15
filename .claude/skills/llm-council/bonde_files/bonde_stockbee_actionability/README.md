# Bonde Stockbee Actionability Context — V5.9.19

This folder contains the council-facing Bonde/Stockbee actionability context.

## V5.9.19 purpose

V5.9.19 fixes decision semantics by separating source focus tier from executable trade decision.

The important rule:

```text
final_trade_status is executable.
tier is not executable.
```

## Files

- `SKILL.md` — council-facing V5.9.19 rule summary.
- `resources/daily_decision_log_schema.csv` — 25-column daily decision log contract.
- `resources/sample_daily_decision_log.csv` — small sample showing valid statuses.

## Required interpretation

| Field | Meaning |
|---|---|
| `tier` | Source/dashboard focus tier only |
| `action_label` | Quality/actionability grade |
| `final_trade_status` | Final executable decision |

`tier=TAKE` may legitimately map to `WATCH` or `REJECT`.

## Council queue relationship

The council queue schema remains unchanged. Council rows should correspond to daily decision log rows where:

```text
final_trade_status=COUNCIL
```

## Daily workflow

Each day, the council should read this folder as the rule context, plus the latest daily files in `latest_context/`.
