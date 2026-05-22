# Active Sugar Babies Context

Generated: 2026-05-22
Source: `sugar_babies_overlay_summary_v410.csv` / `sugar_babies_overlay_report_v410.md`
Status: SUGAR_BABIES_COUNCIL_CONTEXT_MONITORING_ONLY

## Instruction

Use Sugar Babies as an advisory context overlay only. It may raise review priority, confidence framing, and recurrence/context discussion. It must **not** override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering risk, data-quality rejects, severe extension rules, or `final_trade_status`.

## Current broad read

| Level | Sugar Baby | n_rows | T+5 evaluable | avg T+5 | win rate T+5 |
|---|---:|---:|---:|---:|---:|
| candidate | True | 2796 | 1828 | -0.04% | 42.67% |
| candidate | False | 1790 | 1076 | -1.49% | 41.36% |
| ticker | True | 2491 | 1633 | 0.10% | 42.99% |
| ticker | False | 1558 | 932 | -1.43% | 40.88% |

Interpretation: if Sugar Baby cohorts outperform non-Sugar cohorts, treat that as recurrence/attention context. It is not trade permission.

## Recurrence buckets

| slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| 0             |     1558 |                 932 |           -1.4326    |               40.8798 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 1             |      193 |                 138 |           -1.59785   |               38.4058 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 2-3           |      229 |                 145 |            0.23249   |               42.7586 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 4-7           |      301 |                 203 |           -0.0696611 |               43.8424 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 8+            |     1768 |                1147 |            0.312708  |               43.4176 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Setup-family interactions where Sugar Baby = True

| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     2235 |                1465 |           0.00641653 |               42.5939 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      189 |                 144 |           0.462215   |               40.9722 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      117 |                 102 |          -2.49939    |               38.2353 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |       65 |                  48 |           0.918183   |               43.75   | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |       76 |                  38 |           2.56849    |               65.7895 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |       92 |                  18 |           0.626686   |               38.8889 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       15 |                  11 |          -3.8476     |               36.3636 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        4 |                   2 |          -2.37558    |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        3 |                   0 |         nan          |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Council use rules

1. Use Sugar Baby status to raise review priority only.
2. Do not promote, size up, or rescue a candidate because it is a Sugar Baby.
3. If a council candidate is a Sugar Baby, state: `Sugar Baby overlay supports attention/recurrence context but does not override execution gates.`
4. If the candidate is B+ / C1, Sugar Baby status does not rescue the trade. A fresh valid bar and valid R:R are still required.
5. If a candidate is a repeated Sugar Baby, mention the recurrence bucket (`1`, `2-3`, `4-7`, `8+`).
6. If the candidate is absent from `latest_sugar_babies_ticker_context.csv`, state `Sugar Baby: not flagged / no overlay support`, not negative evidence.

## Candidate lookup file

Ticker-level lookup written to `latest_sugar_babies_ticker_context.csv`. Join by uppercase ticker. Missing tickers should be treated as not flagged, not as bearish evidence.
