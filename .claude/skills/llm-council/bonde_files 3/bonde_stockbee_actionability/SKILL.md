---
name: bonde-stockbee-actionability-v5-9-19
description: V5.9.19 Bonde/Stockbee actionability context for council review. Adds final_trade_status as the executable decision field, redefines tier as source focus tier only, separates B+ council candidates from plain B watch rows, and enforces cap-at-C label consistency.
---

# Bonde / Stockbee Actionability Reviewer — V5.9.19

## Core contract

V5.9.19 is a decision-semantics and schema-enforcement patch on top of V5.9.18.

The key change is that `daily_decision_log` now has 25 columns. The appended column is:

```text
final_trade_status
```

Allowed values:

```text
TRADE / COUNCIL / WATCH / REJECT / UNKNOWN
```

This is now the only executable decision field. Humans, automation, council routing, and learning-loop analytics must not treat `tier=TAKE` as trade permission.

## Field semantics

### `tier`

`tier` is source/dashboard focus tier only. It means the upstream dashboard or focus list surfaced the ticker for review.

It does **not** mean the ticker is tradeable.

Valid examples:

```text
tier=TAKE, action_label=C, final_trade_status=WATCH
tier=TAKE, action_label=D, final_trade_status=REJECT
tier=WATCH, action_label=B+, final_trade_status=COUNCIL
```

### `action_label`

`action_label` remains the quality/actionability grade.

Canonical values:

```text
A1 / A2 / B+ / B / C / D / UNKNOWN
```

Interpretation:

- `A1`: actionable, no council required unless explicitly routed.
- `A2`: actionable but may require council if routed.
- `B+`: one-blocker Day-2 / council review candidate.
- `B`: watch candidate, not executable by default.
- `C`: not actionable today.
- `D`: reject / failed / dangerous.
- `UNKNOWN`: insufficient data.

### `final_trade_status`

Canonical mapping:

```text
A1 non-council -> TRADE
A2 non-council -> TRADE
A2 council-routed -> COUNCIL
B+ -> COUNCIL
B -> WATCH
C -> WATCH
D -> REJECT
UNKNOWN -> UNKNOWN
```

If there is a conflict between `tier`, `action_label`, and `final_trade_status`, the executable status wins.

## B / B+ split

V5.9.19 separates serious one-blocker candidates from ordinary watch rows.

Use `B+` only when the row is a legitimate council / Day-2 pullback candidate with one clear blocker, such as poor same-day R:R but otherwise strong setup/catalyst/structure.

Use plain `B` for rows that are interesting but not council-worthy.

Required downstream behavior:

```text
B+ -> final_trade_status=COUNCIL
B  -> final_trade_status=WATCH
```

## Cap-at-C consistency rule

If `decision_reason` contains text that says the row is capped at C, the row cannot remain `action_label=B` or `action_label=B+`.

Trigger phrases include, but are not limited to:

```text
caps at C
C max
cap at C
Slingshot vol gate FAIL
vol gate FAIL -> caps at C
```

Required correction:

```text
action_label must be C or lower
final_trade_status must be WATCH or REJECT
```

This specifically prevents the BAND-style leak where the reason said Slingshot volume gate failure capped the row at C but the row was still labelled B.

## Output sort order

Daily decision output and council prose should sort by real decision priority, not ticker alphabetically.

Sort order:

```text
final_trade_status: TRADE > COUNCIL > WATCH > REJECT > UNKNOWN
action_label: A1 > A2 > B+ > B > C > D > UNKNOWN
then focus_rank ascending
then setup priority
then R:R quality
```

## Council queue relationship

`council_queue` schema remains unchanged at 34 columns.

Every row in `council_queue` should correspond to a row in `daily_decision_log` with:

```text
final_trade_status=COUNCIL
```

Plain B rows should not enter the council queue unless explicitly promoted to B+ / COUNCIL.

## Learning-loop compatibility

Learning-loop notebooks should:

1. Accept 25-column V5.9.19 logs.
2. Remain backward compatible with 24-column V5.9.18 and earlier logs.
3. Derive `final_trade_status` for old logs using the canonical mapping above.
4. Use `final_trade_status in {TRADE, COUNCIL}` for execution/R:R realism audits.
5. Stop treating `tier=TAKE` as executable.
6. Flag rows where reason text caps at C but action label remains B/B+.

## Self-audit before final CSV emission

Before emitting a decision log, verify:

- `daily_decision_log` has exactly 25 columns for V5.9.19.
- `final_trade_status` is present and uses only the allowed enum.
- No row has cap-at-C reason text with `action_label=B` or `B+`.
- No automation or prose calls `tier=TAKE` trade permission.
- `council_queue` rows are a subset of `final_trade_status=COUNCIL` rows.
- Rows are sorted by executable priority, not alphabetically.
