# SLINGSHOT Evaluability Audit — 2026-05-28

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |     341 |
| rows_with_entry                 |     263 |
| rows_with_stop                  |     263 |
| rows_with_target                |     263 |
| rows_with_planned_rr            |     263 |
| rows_with_price_data            |     341 |
| rows_with_enough_future_bars_5d |      83 |
| rows_triggered_5d               |     199 |
| rows_stopped_5d                 |     113 |
| rows_ok_evaluable               |       5 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| INSUFFICIENT_FUTURE_BARS |    258 |
| MISSING_ENTRY            |     78 |
| OK_EVALUABLE             |      5 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| DECISION_LOG         |    171 |
| SLINGSHOT_DIAGNOSTIC |    170 |

## Entry-source classification (v4.13.73)

Only `CAPTURED_AT_TRIGGER` rows pass `ok_evaluable` and are eligible for the H_SLINGSHOT_TARGET_BASIS official verdict. `BACKFILLED_FROM_SIGNAL_CLOSE` rows are robustness-panel only.

| _ss_entry_source            |   rows |
|:----------------------------|-------:|
| CAPTURED_AT_TRIGGER         |    263 |
| MISSING_ENTRY_UNRECOVERABLE |     78 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                 263 |    341 |           77.1 |
| stop_price            |                 263 |    341 |           77.1 |
| target_price          |                 263 |    341 |           77.1 |
| planned_rr            |                 263 |    341 |           77.1 |
| risk_pct              |                   0 |    341 |            0   |
| has_price_data        |                 341 |    341 |          100   |
| available_future_bars |                 341 |    341 |          100   |
| trigger_hit_5d        |                 263 |    341 |           77.1 |
| stop_hit_5d           |                 263 |    341 |           77.1 |
| mfe_r                 |                   0 |    341 |            0   |
| mae_r                 |                   0 |    341 |            0   |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                      |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:-----------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | ACHC     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | AGX      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ALAB     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | AOSL     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ARM      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ATI      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | AVT      | 2026-05-13    | SLINGSHOT      | slingshot       |          86.5 |        83.26 |             95 |      2.62346 | True             |                      10 | True             | OK_EVALUABLE             | OK_EVALUABLE                                         |
| SLINGSHOT_DIAGNOSTIC | CHD      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | CORZ     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | CW       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | DY       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ETON     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ETOR     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | FN       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | GVA      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | HLX      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | INTT     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | IONS     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | KC       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LFST     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LION     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LLYVA    | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LUMN     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LYV      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      10 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | MRVL     | 2026-05-13    | SLINGSHOT      | slingshot       |         178.5 |       168.91 |            195 |      1.72054 | True             |                      10 | True             | OK_EVALUABLE             | OK_EVALUABLE                                         |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
