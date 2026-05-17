# SLINGSHOT Evaluability Audit — 2026-05-17

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |      46 |
| rows_with_entry                 |      42 |
| rows_with_stop                  |      42 |
| rows_with_target                |       0 |
| rows_with_planned_rr            |       0 |
| rows_with_price_data            |      46 |
| rows_with_enough_future_bars_5d |       0 |
| rows_triggered_5d               |       0 |
| rows_stopped_5d                 |       0 |
| rows_ok_evaluable               |       0 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| MISSING_TARGET           |     42 |
| MISSING_ENTRY            |      4 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| SLINGSHOT_DIAGNOSTIC |     23 |
| DECISION_LOG         |     23 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                  42 |     46 |           91.3 |
| stop_price            |                  42 |     46 |           91.3 |
| target_price          |                   0 |     46 |            0   |
| planned_rr            |                   0 |     46 |            0   |
| risk_pct              |                   0 |     46 |            0   |
| has_price_data        |                  46 |     46 |          100   |
| available_future_bars |                  46 |     46 |          100   |
| trigger_hit_5d        |                   0 |     46 |            0   |
| stop_hit_5d           |                   0 |     46 |            0   |
| mfe_r                 |                   0 |     46 |            0   |
| mae_r                 |                   0 |     46 |            0   |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                                               |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:------------------------------------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | ACLX     | 2026-05-15    | SLINGSHOT      | slingshot       |        nan    |       nan    |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | APA      | 2026-05-15    | SLINGSHOT      | slingshot       |         39.04 |        37.42 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | CB       | 2026-05-15    | SLINGSHOT      | slingshot       |        325.82 |       321.36 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | CRGY     | 2026-05-15    | SLINGSHOT      | slingshot       |         13.09 |        12.67 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | GTEN     | 2026-05-15    | SLINGSHOT      | slingshot       |        nan    |       nan    |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| SLINGSHOT_DIAGNOSTIC | HESM     | 2026-05-15    | SLINGSHOT      | slingshot       |         40.01 |        39.08 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | HP       | 2026-05-15    | SLINGSHOT      | slingshot       |         39.51 |        38.69 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | KW       | 2026-05-15    | SLINGSHOT      | slingshot       |         11.03 |        10.98 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | LYB      | 2026-05-15    | SLINGSHOT      | slingshot       |         75.28 |        73.7  |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | MET      | 2026-05-15    | SLINGSHOT      | slingshot       |         79.85 |        78.25 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | MPC      | 2026-05-15    | SLINGSHOT      | slingshot       |        255.39 |       250.64 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | ODFL     | 2026-05-15    | SLINGSHOT      | slingshot       |        204.41 |       195.44 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | OVV      | 2026-05-15    | SLINGSHOT      | slingshot       |         60.08 |        58.85 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | PR       | 2026-05-15    | SLINGSHOT      | slingshot       |         20.85 |        20.28 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | PSX      | 2026-05-15    | SLINGSHOT      | slingshot       |        176.53 |       173.12 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | RNGR     | 2026-05-15    | SLINGSHOT      | slingshot       |         16.53 |        16.11 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | SPIR     | 2026-05-15    | SLINGSHOT      | slingshot       |         20.45 |        17.74 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | STRZ     | 2026-05-15    | SLINGSHOT      | slingshot       |         23.99 |        21.86 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | TALK     | 2026-05-15    | SLINGSHOT      | slingshot       |          5.2  |         5.18 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | TALO     | 2026-05-15    | SLINGSHOT      | slingshot       |         16.4  |        15.67 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | UNF      | 2026-05-15    | SLINGSHOT      | slingshot       |        262.3  |       258.13 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | VLO      | 2026-05-15    | SLINGSHOT      | slingshot       |        251    |       246.73 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| SLINGSHOT_DIAGNOSTIC | VNOM     | 2026-05-15    | SLINGSHOT      | slingshot       |         49.01 |        47.81 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |
| DECISION_LOG         | ACLX     | 2026-05-15    | SLINGSHOT      | slingshot       |        nan    |       nan    |            nan |          nan | True             |                       0 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS |
| DECISION_LOG         | APA      | 2026-05-15    | SLINGSHOT      | slingshot       |         39.04 |        37.42 |            nan |          nan | True             |                       0 | <NA>             | MISSING_TARGET           | MISSING_TARGET|MISSING_RR|INSUFFICIENT_FUTURE_BARS                            |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
