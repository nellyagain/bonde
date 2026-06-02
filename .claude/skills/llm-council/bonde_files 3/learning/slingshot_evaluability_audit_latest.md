# SLINGSHOT Evaluability Audit — 2026-06-02

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |     143 |
| rows_with_entry                 |      65 |
| rows_with_stop                  |      65 |
| rows_with_target                |      65 |
| rows_with_planned_rr            |      65 |
| rows_with_price_data            |     143 |
| rows_with_enough_future_bars_5d |      83 |
| rows_triggered_5d               |      59 |
| rows_stopped_5d                 |      31 |
| rows_ok_evaluable               |       5 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_ENTRY            |     78 |
| INSUFFICIENT_FUTURE_BARS |     60 |
| OK_EVALUABLE             |      5 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| DECISION_LOG         |     72 |
| SLINGSHOT_DIAGNOSTIC |     71 |

## Entry-source classification (v4.13.73)

Only `CAPTURED_AT_TRIGGER` rows pass `ok_evaluable` and are eligible for the H_SLINGSHOT_TARGET_BASIS official verdict. `BACKFILLED_FROM_SIGNAL_CLOSE` rows are robustness-panel only.

| _ss_entry_source            |   rows |
|:----------------------------|-------:|
| MISSING_ENTRY_UNRECOVERABLE |     78 |
| CAPTURED_AT_TRIGGER         |     65 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                  65 |    143 |           45.5 |
| stop_price            |                  65 |    143 |           45.5 |
| target_price          |                  65 |    143 |           45.5 |
| planned_rr            |                  65 |    143 |           45.5 |
| risk_pct              |                   0 |    143 |            0   |
| has_price_data        |                 143 |    143 |          100   |
| available_future_bars |                 143 |    143 |          100   |
| trigger_hit_5d        |                  65 |    143 |           45.5 |
| stop_hit_5d           |                  65 |    143 |           45.5 |
| mfe_r                 |                   0 |    143 |            0   |
| mae_r                 |                   0 |    143 |            0   |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                      |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:-----------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | ACHC     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | AGX      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ALAB     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | AOSL     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ARM      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ATI      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | AVT      | 2026-05-13    | SLINGSHOT      | slingshot       |          86.5 |        83.26 |             95 |      2.62346 | True             |                      12 | True             | OK_EVALUABLE             | OK_EVALUABLE                                         |
| SLINGSHOT_DIAGNOSTIC | CHD      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | CORZ     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | CW       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | DY       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ETON     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | ETOR     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | FN       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | GVA      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | HLX      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | INTT     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | IONS     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | KC       | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LFST     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LION     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LLYVA    | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LUMN     | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | LYV      | 2026-05-13    | SLINGSHOT      | slingshot       |         nan   |       nan    |            nan |    nan       | True             |                      12 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR |
| SLINGSHOT_DIAGNOSTIC | MRVL     | 2026-05-13    | SLINGSHOT      | slingshot       |         178.5 |       168.91 |            195 |      1.72054 | True             |                      12 | True             | OK_EVALUABLE             | OK_EVALUABLE                                         |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
