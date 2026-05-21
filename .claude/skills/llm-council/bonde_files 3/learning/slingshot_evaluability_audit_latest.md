# SLINGSHOT Evaluability Audit — 2026-05-21

Measurement-only audit. No SLINGSHOT rule, gate, ranking, status, or trade-permission logic changed.

## Summary
| metric                          |   value |
|:--------------------------------|--------:|
| diagnostic_rows                 |     729 |
| rows_with_entry                 |     508 |
| rows_with_stop                  |     508 |
| rows_with_target                |     508 |
| rows_with_planned_rr            |     508 |
| rows_with_price_data            |     321 |
| rows_with_enough_future_bars_5d |     106 |
| rows_triggered_5d               |     155 |
| rows_stopped_5d                 |      55 |
| rows_ok_evaluable               |       3 |

## Top missing reasons
| primary_missing_reason   |   rows |
|:-------------------------|-------:|
| NO_PRICE_DATA            |    288 |
| MISSING_ENTRY            |    221 |
| INSUFFICIENT_FUTURE_BARS |    217 |
| OK_EVALUABLE             |      3 |

## Source scope
| source_scope         |   rows |
|:---------------------|-------:|
| SLINGSHOT_DIAGNOSTIC |    585 |
| DECISION_LOG         |    144 |

## Entry-source classification (v4.13.73)

Only `CAPTURED_AT_TRIGGER` rows pass `ok_evaluable` and are eligible for the H_SLINGSHOT_TARGET_BASIS official verdict. `BACKFILLED_FROM_SIGNAL_CLOSE` rows are robustness-panel only.

| _ss_entry_source             |   rows |
|:-----------------------------|-------:|
| CAPTURED_AT_TRIGGER          |    508 |
| BACKFILLED_FROM_SIGNAL_CLOSE |    178 |
| MISSING_ENTRY_UNRECOVERABLE  |     43 |

### Entry-source x pack_version cross-tab

| pack_version      | _ss_entry_source             |   rows |
|:------------------|:-----------------------------|-------:|
| (no_pack_version) | CAPTURED_AT_TRIGGER          |    102 |
| (no_pack_version) | MISSING_ENTRY_UNRECOVERABLE  |     42 |
| v28.12-pack1      | CAPTURED_AT_TRIGGER          |    406 |
| v28.12-pack1      | MISSING_ENTRY_UNRECOVERABLE  |      1 |
| v28.9-pack1       | BACKFILLED_FROM_SIGNAL_CLOSE |    178 |

## Field coverage
| field                 |   populated_or_true |   rows |   coverage_pct |
|:----------------------|--------------------:|-------:|---------------:|
| entry_price           |                 508 |    729 |           69.7 |
| stop_price            |                 508 |    729 |           69.7 |
| target_price          |                 508 |    729 |           69.7 |
| planned_rr            |                 508 |    729 |           69.7 |
| risk_pct              |                 505 |    729 |           69.3 |
| has_price_data        |                 321 |    729 |           44   |
| available_future_bars |                 729 |    729 |          100   |
| trigger_hit_5d        |                 188 |    729 |           25.8 |
| stop_hit_5d           |                 188 |    729 |           25.8 |
| mfe_r                 |                   0 |    729 |            0   |
| mae_r                 |                   0 |    729 |            0   |

## Sample rows
| _ss_source_scope     | ticker   | signal_date   | setup_family   | primary_setup   |   entry_price |   stop_price |   target_price |   planned_rr | has_price_data   |   available_future_bars | trigger_hit_5d   | primary_missing_reason   | missing_reasons                                                    |
|:---------------------|:---------|:--------------|:---------------|:----------------|--------------:|-------------:|---------------:|-------------:|:-----------------|------------------------:|:-----------------|:-------------------------|:-------------------------------------------------------------------|
| SLINGSHOT_DIAGNOSTIC | OUST     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | KC       | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | CGEH     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | NBIS     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | WBTN     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | INTT     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | SILC     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | AOSL     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | ETOR     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | FN       | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | LUMN     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | CRNC     | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | False            |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | AVT      | 2026-05-13    | ACTIVE_BURST   |                 |           nan |          nan |            nan |          nan | True             |                       5 | True             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | VNET     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | OUST     | 2026-05-13    | EP_SPIKE       |                 |           nan |          nan |            nan |          nan | False            |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR|NO_PRICE_DATA |
| SLINGSHOT_DIAGNOSTIC | NBIS     | 2026-05-13    | EP_ACTIVE      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | VEON     | 2026-05-13    | EP_ACTIVE      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | SRRK     | 2026-05-13    | DELAYED_EP     |                 |           nan |          nan |            nan |          nan | True             |                       5 | True             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | PHVS     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | VEON     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | LION     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | TYRA     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | TAL      | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | MS       | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | <NA>             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |
| SLINGSHOT_DIAGNOSTIC | SRRK     | 2026-05-13    | SLINGSHOT      |                 |           nan |          nan |            nan |          nan | True             |                       5 | True             | MISSING_ENTRY            | MISSING_ENTRY|MISSING_STOP|MISSING_TARGET|MISSING_RR               |

## Interpretation
- `MISSING_ENTRY`, `MISSING_STOP`, `MISSING_TARGET`, and `MISSING_RR` are upstream/field-mapping issues, not SLINGSHOT expectancy evidence.
- `NO_PRICE_DATA` or `INSUFFICIENT_FUTURE_BARS` are outcome-resolution issues.
- `NEVER_TRIGGERED` means the setup did not reach the planned entry within the evaluability window.
- Only `OK_EVALUABLE` rows should be used for SLINGSHOT expectancy or gate calibration.
