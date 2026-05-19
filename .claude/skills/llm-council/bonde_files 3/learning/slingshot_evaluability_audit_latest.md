# SLINGSHOT Evaluability Audit — 2026-05-19

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |     146 |
| rows_with_entry                 |       0 |
| rows_with_stop                  |       0 |
| rows_with_target                |       0 |
| rows_with_planned_rr            |       0 |
| rows_with_price_data            |     146 |
| rows_with_enough_future_bars_5d |       0 |
| rows_triggered_5d               |       0 |
| rows_stopped_5d                 |       0 |
| rows_ok_evaluable               |       0 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_ENTRY            |    146 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| SLINGSHOT_DIAGNOSTIC |     73 |
| DECISION_LOG         |     73 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                   0 |    146 |              0 |
| stop_price            |                   0 |    146 |              0 |
| target_price          |                   0 |    146 |              0 |
| planned_rr            |                   0 |    146 |              0 |
| risk_pct              |                   0 |    146 |              0 |
| has_price_data        |                 146 |    146 |            100 |
| available_future_bars |                 146 |    146 |            100 |
| trigger_hit_5d        |                   0 |    146 |              0 |
| stop_hit_5d           |                   0 |    146 |              0 |
| mfe_r                 |                   0 |    146 |              0 |
| mae_r                 |                   0 |    146 |              0 |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                                               |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:------------------------------------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | ACEL     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | AHRT     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | AIG      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | ALF      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | APLE     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | ASH      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | BCAL     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | BKR      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | BKSY     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | BNL      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | BRC      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | BRX      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CFR      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CHCT     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CHRW     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CLMT     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CPAY     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CTO      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | CWAN     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | D        | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | DEA      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | DRH      | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | EFSC     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | EW       | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | FCPT     | 2026-05-18    | SLINGSHOT      | slingshot       |           nan |          nan |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
