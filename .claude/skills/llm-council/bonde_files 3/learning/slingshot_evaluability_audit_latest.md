# SLINGSHOT Evaluability Audit — 2026-06-12

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |    2597 |
| rows_with_entry                 |    2413 |
| rows_with_stop                  |    2413 |
| rows_with_target                |    1324 |
| rows_with_planned_rr            |    2338 |
| rows_with_price_data            |    1301 |
| rows_with_enough_future_bars_5d |    2035 |
| rows_triggered_5d               |    2043 |
| rows_stopped_5d                 |     917 |
| rows_ok_evaluable               |     877 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| NO_PRICE_DATA            |   1090 |
| OK_EVALUABLE             |    877 |
| INSUFFICIENT_FUTURE_BARS |    263 |
| MISSING_ENTRY            |    184 |
| NEVER_TRIGGERED          |    108 |
| MISSING_TARGET           |     75 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| SLINGSHOT_DIAGNOSTIC |   2006 |
| DECISION_LOG         |    591 |

## Entry-source classification (v4.13.73)

Only `CAPTURED_AT_TRIGGER` rows pass `ok_evaluable` and are eligible for the H_SLINGSHOT_TARGET_BASIS official verdict. `BACKFILLED_FROM_SIGNAL_CLOSE` rows are robustness-panel only.

| _ss_entry_source             |   rows |
|:-----------------------------|-------:|
| CAPTURED_AT_TRIGGER          |   2413 |
| BACKFILLED_FROM_SIGNAL_CLOSE |    178 |
| MISSING_ENTRY_UNRECOVERABLE  |      6 |

### Entry-source x pack_version cross-tab

| pack_version      | _ss_entry_source             |   rows |
|:------------------|:-----------------------------|-------:|
| (no_pack_version) | CAPTURED_AT_TRIGGER          |    587 |
| (no_pack_version) | MISSING_ENTRY_UNRECOVERABLE  |      4 |
| v28.12-pack1      | CAPTURED_AT_TRIGGER          |    889 |
| v28.12-pack1      | MISSING_ENTRY_UNRECOVERABLE  |      1 |
| v28.16-pack1      | CAPTURED_AT_TRIGGER          |    298 |
| v28.19-pack1      | CAPTURED_AT_TRIGGER          |    378 |
| v28.19-pack1      | MISSING_ENTRY_UNRECOVERABLE  |      1 |
| v28.22-pack1      | CAPTURED_AT_TRIGGER          |     50 |
| v28.24-pack1      | CAPTURED_AT_TRIGGER          |    211 |
| v28.9-pack1       | BACKFILLED_FROM_SIGNAL_CLOSE |    178 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                2413 |   2597 |           92.9 |
| stop_price            |                2413 |   2597 |           92.9 |
| target_price          |                1324 |   2597 |           51   |
| planned_rr            |                2338 |   2597 |           90   |
| risk_pct              |                2412 |   2597 |           92.9 |
| has_price_data        |                1301 |   2597 |           50.1 |
| available_future_bars |                2597 |   2597 |          100   |
| trigger_hit_5d        |                2274 |   2597 |           87.6 |
| stop_hit_5d           |                2274 |   2597 |           87.6 |
| mfe_r                 |                   0 |   2597 |            0   |
| mae_r                 |                   0 |   2597 |            0   |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                                    |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:-------------------------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | OUST     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | KC       | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | CGEH     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | NBIS     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | WBTN     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | INTT     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | SILC     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | AOSL     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | ETOR     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | FN       | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | LUMN     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | CRNC     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | AVT      | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | VNET     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | OUST     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | NBIS     | 2026-05-13    | EP_ACTIVE      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | VEON     | 2026-05-13    | EP_ACTIVE      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | SRRK     | 2026-05-13    | DELAYED_EP     |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | PHVS     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | VEON     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | LION     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | TYRA     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | TAL      | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | MS       | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | SRRK     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | False            |                      21 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
