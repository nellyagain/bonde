# Active Sugar Babies Context

Generated: 2026-05-27
Source: `sugar_babies_overlay_summary_v410.csv` / `sugar_babies_overlay_report_v410.md`
Status: SUGAR_BABIES_COUNCIL_CONTEXT_MONITORING_ONLY

## Instruction

Use Sugar Babies as an advisory context overlay only. It may raise review priority, confidence framing, and recurrence/context discussion. It must **not** override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering risk, data-quality rejects, severe extension rules, or `final_trade_status`.

## Current broad read

| Level | Sugar Baby | n_rows | T+5 evaluable | avg T+5 | win rate T+5 |
|---|---:|---:|---:|---:|---:|
| candidate | True | 3148 | 2359 | 1.47% | 49.64% |
| candidate | False | 2137 | 1337 | -0.83% | 46.07% |
| ticker | True | 2798 | 2144 | 1.62% | 50.33% |
| ticker | False | 1858 | 1165 | -0.74% | 46.09% |

Interpretation: if Sugar Baby cohorts outperform non-Sugar cohorts, treat that as recurrence/attention context. It is not trade permission.

## Recurrence buckets

| slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| 0             |     1858 |                1165 |            -0.742436 |               46.0944 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 1             |      225 |                 156 |            -0.922904 |               41.0256 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 2-3           |      249 |                 181 |             1.59328  |               51.9337 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 4-7           |      321 |                 252 |             0.946075 |               48.8095 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 8+            |     2003 |                1555 |             1.99172  |               51.3183 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Setup-family interactions where Sugar Baby = True

| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     2471 |                1941 |              1.65979 |               50.3349 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      240 |                 162 |              1.07967 |               43.8272 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      120 |                 102 |             -2.49939 |               38.2353 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |       83 |                  55 |              2.66174 |               47.2727 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |       90 |                  45 |              2.43928 |               66.6667 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |      118 |                  36 |              1.88425 |               52.7778 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       19 |                  13 |             -1.33482 |               38.4615 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        3 |                   3 |              9.86674 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        4 |                   2 |             -2.37558 |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Council use rules

1. Use Sugar Baby status to raise review priority only.
2. Do not promote, size up, or rescue a candidate because it is a Sugar Baby.
3. If a council candidate is a Sugar Baby, state: `Sugar Baby overlay supports attention/recurrence context but does not override execution gates.`
4. If the candidate is B+ / C1, Sugar Baby status does not rescue the trade. A fresh valid bar and valid R:R are still required.
5. If a candidate is a repeated Sugar Baby, mention the recurrence bucket (`1`, `2-3`, `4-7`, `8+`).
6. If the candidate is absent from `latest_sugar_babies_ticker_context.csv`, state `Sugar Baby: not flagged / no overlay support`, not negative evidence.

## Candidate lookup file

Ticker-level lookup written to `latest_sugar_babies_ticker_context.csv`. Join by uppercase ticker. Missing tickers should be treated as not flagged, not as bearish evidence.
