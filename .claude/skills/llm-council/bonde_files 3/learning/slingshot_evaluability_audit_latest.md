# SLINGSHOT Evaluability Audit — 2026-05-17

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |     228 |
| rows_with_entry                 |      48 |
| rows_with_stop                  |      48 |
| rows_with_target                |      48 |
| rows_with_planned_rr            |      48 |
| rows_with_price_data            |      47 |
| rows_with_enough_future_bars_5d |       0 |
| rows_triggered_5d               |       0 |
| rows_stopped_5d                 |       0 |
| rows_ok_evaluable               |       0 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_ENTRY            |    180 |
| INSUFFICIENT_FUTURE_BARS |     45 |
| NO_PRICE_DATA            |      3 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| SLINGSHOT_DIAGNOSTIC |    205 |
| DECISION_LOG         |     23 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                  48 |    228 |           21.1 |
| stop_price            |                  48 |    228 |           21.1 |
| target_price          |                  48 |    228 |           21.1 |
| planned_rr            |                  48 |    228 |           21.1 |
| risk_pct              |                  48 |    228 |           21.1 |
| has_price_data        |                  47 |    228 |           20.6 |
| available_future_bars |                 228 |    228 |          100   |
| trigger_hit_5d        |                   0 |    228 |            0   |
| stop_hit_5d           |                   0 |    228 |            0   |
| mfe_r                 |                   0 |    228 |            0   |
| mae_r                 |                   0 |    228 |            0   |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                                    |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:-------------------------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | OUST     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | KC       | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | CGEH     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | NBIS     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | WBTN     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | INTT     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | SILC     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | AOSL     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | ETOR     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | FN       | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | LUMN     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | CRNC     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | AVT      | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | VNET     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | OUST     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | NBIS     | 2026-05-13    | EP_ACTIVE      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | VEON     | 2026-05-13    | EP_ACTIVE      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | SRRK     | 2026-05-13    | DELAYED_EP     |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | PHVS     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | VEON     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | LION     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | TYRA     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | TAL      | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | MS       | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | SRRK     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                       2 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
