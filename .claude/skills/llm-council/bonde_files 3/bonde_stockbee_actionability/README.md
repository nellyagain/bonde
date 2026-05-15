# Bonde Stockbee Actionability Context — V5.9.19

This folder contains the council-facing Bonde/Stockbee actionability context used by the LLM council inside the `nellyagain/bonde` repo.

## V5.9.19 purpose

V5.9.19 fixes decision semantics introduced by the distinction between source focus tiers and executable trade decisions.

The important rule:

```text
final_trade_status is executable.
tier is not executable.
```

## Files

- `SKILL.md` — council-facing rule summary for V5.9.19.
- `resources/daily_decision_log_schema.csv` — 25-column daily decision log contract.

## New daily_decision_log contract

V5.9.19 appends one column to the prior 24-column V5.9.x decision log:

```text
final_trade_status
```

Allowed enum:

```text
TRADE / COUNCIL / WATCH / REJECT / UNKNOWN
```

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

## Learning loop compatibility

The learning loop should accept both:

- old 24-column logs, deriving `final_trade_status`; and
- new 25-column V5.9.19 logs with `final_trade_status` already present.

The learning loop should use `final_trade_status in {TRADE, COUNCIL}` for execution/R:R realism audits.
