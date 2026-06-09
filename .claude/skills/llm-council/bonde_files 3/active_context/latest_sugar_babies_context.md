# Active Sugar Babies Context

Generated: 2026-06-09
Source: `sugar_babies_overlay_summary_v410.csv` / `sugar_babies_overlay_report_v410.md`
Status: SUGAR_BABIES_COUNCIL_CONTEXT_MONITORING_ONLY

## Instruction

Use Sugar Babies as an advisory context overlay only. It may raise review priority, confidence framing, and recurrence/context discussion. It must **not** override R:R, DTE, hard rejects, failed EP, bag-holder status, dilution/offering risk, data-quality rejects, severe extension rules, or `final_trade_status`.

## Current broad read

| Level | Sugar Baby | n_rows | T+5 evaluable | avg T+5 | win rate T+5 |
|---|---:|---:|---:|---:|---:|
| candidate | True | 4841 | 4022 | 1.01% | 48.16% |
| candidate | False | 3095 | 2613 | -0.49% | 48.41% |
| ticker | True | 4224 | 3595 | 1.11% | 48.51% |
| ticker | False | 2674 | 2299 | -0.37% | 48.50% |

Interpretation: if Sugar Baby cohorts outperform non-Sugar cohorts, treat that as recurrence/attention context. It is not trade permission.

## Recurrence buckets

| slice_value   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:--------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| 0             |     2674 |                2299 |            -0.374687 |               48.4993 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 1             |      297 |                 278 |            -0.15483  |               44.2446 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 2-3           |      260 |                 225 |             0.373603 |               48.4444 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 4-7           |      401 |                 342 |             0.765925 |               47.6608 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| 8+            |     3266 |                2750 |             1.33838  |               49.0545 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Setup-family interactions where Sugar Baby = True

| setup_family   |   n_rows |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:---------------|---------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| EP9M           |     3792 |                3115 |            1.19771   |               49.0209 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ACTIVE_BURST   |      374 |                 352 |           -0.0203213 |               41.4773 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| SLINGSHOT      |      201 |                 172 |            3.07311   |               55.2326 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_SPIKE       |      162 |                 146 |           -1.88938   |               36.9863 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| EP_ACTIVE      |      121 |                 110 |            0.380044  |               43.6364 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PAUSE          |      151 |                  94 |            0.367196  |               53.1915 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DELAYED_EP     |       24 |                  23 |           -0.879836  |               43.4783 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| PRE_BURST      |        7 |                   6 |           -1.74923   |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ANTICIPATION   |        8 |                   4 |            7.72868   |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| DIAGNOSTICS    |        1 |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |


## Council use rules

1. Use Sugar Baby status to raise review priority only.
2. Do not promote, size up, or rescue a candidate because it is a Sugar Baby.
3. If a council candidate is a Sugar Baby, state: `Sugar Baby overlay supports attention/recurrence context but does not override execution gates.`
4. If the candidate is B+ / C1, Sugar Baby status does not rescue the trade. A fresh valid bar and valid R:R are still required.
5. If a candidate is a repeated Sugar Baby, mention the recurrence bucket (`1`, `2-3`, `4-7`, `8+`).
6. If the candidate is absent from `latest_sugar_babies_ticker_context.csv`, state `Sugar Baby: not flagged / no overlay support`, not negative evidence.

## Candidate lookup file

Ticker-level lookup written to `latest_sugar_babies_ticker_context.csv`. Join by uppercase ticker. Missing tickers should be treated as not flagged, not as bearish evidence.
