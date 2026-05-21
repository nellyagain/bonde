# Active Sugar Babies Context

Generated: 2026-05-21
Source: `sugar_babies_overlay_summary_v410.csv` / `sugar_babies_overlay_report_v410.md`
Status: SUGAR_BABIES_COUNCIL_CONTEXT_MONITORING_ONLY

## Instruction

Use Sugar Babies as an advisory context overlay only. It may raise review priority, confidence framing, and recurrence/context discussion. It must **not** override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering risk, data-quality rejects, severe extension rules, or `final_trade_status`.

## Current broad read

| Level | Sugar Baby | n_rows | T+5 evaluable | avg T+5 | win rate T+5 |
|---|---:|---:|---:|---:|---:|
| candidate | True | 2593 | 1620 | -0.01% | 42.22% |
| candidate | False | 1632 | 914 | -1.79% | 40.37% |
| ticker | True | 2330 | 1455 | 0.10% | 42.47% |
| ticker | False | 1415 | 794 | -1.69% | 40.18% |

Interpretation: if Sugar Baby cohorts outperform non-Sugar cohorts, treat that as recurrence/attention context. It is not trade permission.

## Recurrence buckets

| slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| 0             |     1415 |                 794 |            -1.69265  |               40.1763 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 1             |      179 |                 130 |            -1.61767  |               38.4615 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 2-3           |      217 |                 134 |            -0.243946 |               39.5522 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 4-7           |      304 |                 188 |             0.993659 |               47.3404 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 8+            |     1630 |                1003 |             0.202826 |               42.4726 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Setup-family interactions where Sugar Baby = True

| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     2103 |                1308 |           -0.0401398 |               41.9725 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      171 |                 125 |            0.451312  |               41.6    | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      106 |                  88 |           -1.29196   |               40.9091 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |       59 |                  43 |            0.4395    |               39.5349 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |       71 |                  35 |            2.75313   |               62.8571 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       15 |                  11 |           -3.8476    |               36.3636 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |       63 |                   8 |            3.74069   |               37.5    | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        2 |                   2 |           -2.37558   |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        3 |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Council use rules

1. Use Sugar Baby status to raise review priority only.
2. Do not promote, size up, or rescue a candidate because it is a Sugar Baby.
3. If a council candidate is a Sugar Baby, state: `Sugar Baby overlay supports attention/recurrence context but does not override execution gates.`
4. If the candidate is B+ / C1, Sugar Baby status does not rescue the trade. A fresh valid bar and valid R:R are still required.
5. If a candidate is a repeated Sugar Baby, mention the recurrence bucket (`1`, `2-3`, `4-7`, `8+`).
6. If the candidate is absent from `latest_sugar_babies_ticker_context.csv`, state `Sugar Baby: not flagged / no overlay support`, not negative evidence.

## Candidate lookup file

Ticker-level lookup written to `latest_sugar_babies_ticker_context.csv`. Join by uppercase ticker. Missing tickers should be treated as not flagged, not as bearish evidence.
