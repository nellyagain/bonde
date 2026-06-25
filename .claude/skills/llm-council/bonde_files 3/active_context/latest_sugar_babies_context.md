# Active Sugar Babies Context

Generated: 2026-06-25
Source: `sugar_babies_overlay_summary_v410.csv` / `sugar_babies_overlay_report_v410.md`
Status: SUGAR_BABIES_COUNCIL_CONTEXT_MONITORING_ONLY

## Instruction

Use Sugar Babies as an advisory context overlay only. It may raise review priority, confidence framing, and recurrence/context discussion. It must **not** override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering risk, data-quality rejects, severe extension rules, or `final_trade_status`.

## Current broad read

| Level | Sugar Baby | n_rows | T+5 evaluable | avg T+5 | win rate T+5 |
|---|---:|---:|---:|---:|---:|
| candidate | True | 7076 | 5930 | 0.32% | 48.45% |
| candidate | False | 4575 | 3737 | 0.03% | 51.62% |
| ticker | True | 6291 | 5268 | 0.55% | 48.99% |
| ticker | False | 4026 | 3313 | 0.18% | 52.25% |

Interpretation: if Sugar Baby cohorts outperform non-Sugar cohorts, treat that as recurrence/attention context. It is not trade permission.

## Recurrence buckets

| slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| 0             |     4026 |                3313 |           0.176547   |               52.2487 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 1             |      433 |                 341 |          -0.00767423 |               47.5073 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 2-3           |      359 |                 296 |           0.392751   |               51.0135 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 4-7           |      423 |                 346 |          -0.286957   |               47.3988 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 8+            |     5076 |                4285 |           0.676515   |               49.1015 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Setup-family interactions where Sugar Baby = True

| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     5572 |                4650 |             0.360371 |               48.2796 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      491 |                 431 |            -0.610211 |               41.9954 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |      368 |                 308 |             1.76927  |               56.8182 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      194 |                 182 |            -1.12557  |               42.3077 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |      227 |                 162 |             0.318273 |               60.4938 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |      148 |                 135 |             0.240572 |               43.7037 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       52 |                  39 |             0.772796 |               48.7179 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |       16 |                  15 |             2.00993  |               93.3333 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        7 |                   7 |            -1.28307  |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DIAGNOSTICS    |        1 |                   1 |             0.191814 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Council use rules

1. Use Sugar Baby status to raise review priority only.
2. Do not promote, size up, or rescue a candidate because it is a Sugar Baby.
3. If a council candidate is a Sugar Baby, state: `Sugar Baby overlay supports attention/recurrence context but does not override execution gates.`
4. If the candidate is B+ / C1, Sugar Baby status does not rescue the trade. A fresh valid bar and valid R:R are still required.
5. If a candidate is a repeated Sugar Baby, mention the recurrence bucket (`1`, `2-3`, `4-7`, `8+`).
6. If the candidate is absent from `latest_sugar_babies_ticker_context.csv`, state `Sugar Baby: not flagged / no overlay support`, not negative evidence.

## Candidate lookup file

Ticker-level lookup written to `latest_sugar_babies_ticker_context.csv`. Join by uppercase ticker. Missing tickers should be treated as not flagged, not as bearish evidence.
