# V5.9.19 Deployment Notes — Bonde Council Context

This repo now contains the V5.9.19 Bonde/Stockbee actionability context files in:

```text
.claude/skills/llm-council/bonde_files 3/bonde_stockbee_actionability/
```

## Files added

```text
bonde_stockbee_actionability/SKILL.md
bonde_stockbee_actionability/README.md
bonde_stockbee_actionability/resources/daily_decision_log_schema.csv
bonde_stockbee_actionability/resources/sample_daily_decision_log.csv
```

## Required council instruction

When running the LLM council, point it to:

```text
.claude/skills/llm-council/bonde_files 3/bonde_stockbee_actionability/
```

and apply these V5.9.19 semantics:

```text
final_trade_status is executable
tier is source/dashboard focus tier only
B+ routes to COUNCIL
plain B routes to WATCH
cap-at-C reason text cannot remain action_label=B or B+
daily_decision_log has 25 columns ending with final_trade_status
```

## Learning-loop compatibility

The matching learning-loop notebook version is:

```text
bonde_learning_loop_v4_13_15_v5_9_19_final_status.ipynb
```

Expected behavior:

- accepts new 25-column V5.9.19 daily decision logs;
- remains backward-compatible with old 24-column logs;
- derives `final_trade_status` for old logs;
- uses `final_trade_status in {TRADE, COUNCIL}` for execution/R:R realism audits;
- stops treating `tier=TAKE` as executable;
- flags cap-at-C reason text if action_label remains B/B+.

## Post-run checks

After the next daily run, verify:

```text
1. daily_decision_log has 25 columns.
2. final column is final_trade_status.
3. allowed values are only TRADE / COUNCIL / WATCH / REJECT / UNKNOWN.
4. council_queue rows correspond to daily_decision_log rows where final_trade_status=COUNCIL.
5. no row has cap-at-C reason text while action_label is B or B+.
```

## Current practical note

The `.skill` zip artifact is not required for this Bonde repo-context workflow. The council should read the unpacked context files above.
