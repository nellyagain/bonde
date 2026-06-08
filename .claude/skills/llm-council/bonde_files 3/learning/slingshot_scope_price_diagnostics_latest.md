# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-08

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| ENTRY_STOP_NO_TARGET              |   1043 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    385 |
| FULL_PLAN_NO_PRICE_DATA           |    214 |
| OK_EVALUABLE                      |    199 |
| MISSING_ENTRY                     |    182 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |     87 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **1056**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **528**
- From same-date universe plan rows: **528**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |   1265 |         1143 |        1143 |           413 |              1134 |               512 |                   899 |            281 |                                         0 |                                  11 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    531 |          528 |         528 |           398 |               523 |               531 |                   346 |            311 |                                       527 |                                   8 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    256 |          256 |         256 |            73 |               241 |               112 |                   194 |             67 |                                         0 |                                   9 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                 0 |                    57 |              0 |                                         0 |                                  17 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     0 |              0 |                                         1 |                                   4 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   1789 |         1664 |        1664 |           811 |              1652 |              1041 |                  1239 |            591 |                                       527 |                                 9   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |    113 |          113 |         113 |            31 |               107 |                45 |                    86 |             29 |                                         0 |                                 9   |
| EP9M           | SLINGSHOT_OVERLAY               |     77 |           77 |          77 |            32 |                76 |                34 |                    52 |             20 |                                         0 |                                 8   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                 0 |                    28 |              0 |                                         0 |                                17   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     24 |           24 |          24 |             4 |                22 |                17 |                    21 |              8 |                                         0 |                                 9   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     19 |           19 |          19 |             0 |                14 |                 4 |                    17 |              2 |                                         0 |                                 9   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                17   |
| PAUSE          | SLINGSHOT_OVERLAY               |     12 |           12 |          12 |             3 |                11 |                 7 |                     9 |              5 |                                         0 |                                 7   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 0 |                    11 |              0 |                                         0 |                                17   |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             2 |                 8 |                 5 |                     7 |              3 |                                         0 |                                 9   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      7 |            7 |           7 |             0 |                 5 |                 2 |                     6 |              1 |                                         0 |                                 8   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 0 |                     4 |              0 |                                         0 |                                17.5 |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      3 |            3 |           3 |             1 |                 3 |                 0 |                     2 |              0 |                                         0 |                                 6   |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              0 |                                         1 |                                11   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-06-05           | SLINGSHOT_DIAGNOSTIC    |     77 |           77 |          77 |            77 |                77 |                77 |                     0 |              0 |                                         0 |                                   1 |
| 2026-06-05           | DECISION_LOG            |     75 |           75 |          75 |            75 |                75 |                75 |                     0 |              0 |                                        75 |                                   1 |
| 2026-06-04           | SLINGSHOT_DIAGNOSTIC    |    119 |          119 |         119 |           114 |               114 |               119 |                     0 |              0 |                                         0 |                                   2 |
| 2026-06-04           | DECISION_LOG            |    105 |          105 |         105 |           101 |               102 |               105 |                     0 |              0 |                                       104 |                                   2 |
| 2026-06-03           | SLINGSHOT_DIAGNOSTIC    |     71 |           71 |          71 |            69 |                69 |                 0 |                     0 |              0 |                                         0 |                                   3 |
| 2026-06-02           | SLINGSHOT_DIAGNOSTIC    |    161 |          161 |         161 |           154 |               154 |                12 |                     0 |              0 |                                         0 |                                   4 |
| 2026-06-02           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     0 |              0 |                                         6 |                                   4 |
| 2026-06-01           | SLINGSHOT_DIAGNOSTIC    |     82 |           82 |          82 |            72 |                72 |                74 |                    82 |             55 |                                         0 |                                   5 |
| 2026-06-01           | DECISION_LOG            |     54 |           54 |          54 |            52 |                52 |                54 |                    54 |             51 |                                        54 |                                   5 |
| 2026-05-29           | SLINGSHOT_DIAGNOSTIC    |     52 |           52 |          52 |             0 |                52 |                 0 |                    52 |              0 |                                         0 |                                   6 |
| 2026-05-27           | DECISION_LOG            |     60 |           60 |          60 |            30 |                60 |                60 |                    60 |             54 |                                        60 |                                   8 |
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     39 |           39 |          39 |             0 |                39 |                39 |                    39 |             33 |                                         0 |                                   8 |
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |             0 |               169 |               164 |                   169 |            140 |                                         0 |                                   9 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                   129 |            110 |                                       129 |                                   9 |
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |             0 |                70 |                11 |                    70 |             11 |                                         0 |                                  11 |
| 2026-05-22           | DECISION_LOG            |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         1 |                                  11 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |             0 |               153 |                 9 |                   153 |              4 |                                         0 |                                  12 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |             0 |               248 |                12 |                   248 |              9 |                                         0 |                                  13 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             5 |                 6 |                 6 |                     6 |              5 |                                         6 |                                  13 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |             0 |                47 |                 0 |                    47 |              0 |                                         0 |                                  14 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |             0 |                84 |                83 |                    85 |             75 |                                         0 |                                  15 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |             0 |                72 |                73 |                    73 |             72 |                                        72 |                                  15 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |             0 |                27 |                24 |                    27 |             21 |                                         0 |                                  16 |
| 2026-05-15           | DECISION_LOG            |     23 |           21 |          21 |             0 |                21 |                23 |                    23 |             18 |                                        21 |                                  16 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                  17 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                 0 |                    65 |              0 |                                         0 |                                  18 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |   1156 |
| PRICE_JOIN_MISS                         |    734 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    220 |

## Future-bar reason
| future_bar_reason   |   rows |
|:--------------------|-------:|
| HAS_5D_FUTURE_BARS  |   1496 |
| TOO_RECENT_FOR_5D   |    614 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.