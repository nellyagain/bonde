# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-05

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| ENTRY_STOP_NO_TARGET              |   1033 |
| MISSING_ENTRY                     |    221 |
| FULL_PLAN_NO_PRICE_DATA           |    199 |
| OK_EVALUABLE                      |    145 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    139 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |     23 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **698**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **349**
- From same-date universe plan rows: **349**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |   1074 |          952 |         952 |           226 |               947 |               374 |                   808 |            237 |                                         0 |                                  11 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    392 |          350 |         350 |           224 |               348 |               392 |                   333 |            262 |                                       348 |                                   8 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    235 |          235 |         235 |            54 |               222 |                95 |                   151 |             56 |                                         0 |                                   8 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                    57 |              0 |                                         0 |                                  16 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            2 |           2 |             2 |                 2 |                 2 |                     1 |              1 |                                         1 |                                  10 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   1459 |         1295 |        1295 |           450 |              1290 |               764 |                  1137 |            498 |                                       348 |                                11   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |    106 |          106 |         106 |            24 |               100 |                40 |                    69 |             27 |                                         0 |                                 8   |
| EP9M           | SLINGSHOT_OVERLAY               |     65 |           65 |          65 |            21 |                65 |                23 |                    41 |             13 |                                         0 |                                 8   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                    28 |              0 |                                         0 |                                16   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     23 |           23 |          23 |             3 |                21 |                17 |                    17 |              8 |                                         0 |                                 8   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     19 |           19 |          19 |             0 |                14 |                 4 |                    12 |              2 |                                         0 |                                 8   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                16   |
| PAUSE          | SLINGSHOT_OVERLAY               |     11 |           11 |          11 |             3 |                11 |                 6 |                     6 |              4 |                                         0 |                                 7   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                    11 |              0 |                                         0 |                                16   |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             2 |                 8 |                 5 |                     5 |              2 |                                         0 |                                 8   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      7 |            7 |           7 |             0 |                 5 |                 2 |                     4 |              1 |                                         0 |                                 7   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     4 |              0 |                                         0 |                                16.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      3 |            2 |           2 |             2 |                 2 |                 3 |                     2 |              1 |                                         1 |                                17   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      3 |            3 |           3 |             1 |                 3 |                 0 |                     1 |              0 |                                         0 |                                 5   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-06-03           | SLINGSHOT_DIAGNOSTIC    |     55 |           55 |          55 |            54 |                54 |                 0 |                     0 |              0 |                                         0 |                                   2 |
| 2026-06-02           | SLINGSHOT_DIAGNOSTIC    |    161 |          161 |         161 |           154 |               154 |                12 |                     0 |              0 |                                         0 |                                   3 |
| 2026-06-02           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     0 |              0 |                                         6 |                                   3 |
| 2026-06-01           | SLINGSHOT_DIAGNOSTIC    |     82 |           82 |          82 |            72 |                72 |                74 |                     0 |              0 |                                         0 |                                   4 |
| 2026-06-01           | DECISION_LOG            |     54 |           54 |          54 |            52 |                52 |                54 |                     0 |              0 |                                        54 |                                   4 |
| 2026-05-29           | SLINGSHOT_DIAGNOSTIC    |     52 |           52 |          52 |             0 |                52 |                 0 |                     0 |              0 |                                         0 |                                   5 |
| 2026-05-27           | DECISION_LOG            |     60 |           60 |          60 |            30 |                60 |                60 |                    60 |             54 |                                        60 |                                   7 |
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     39 |           39 |          39 |             0 |                39 |                39 |                    39 |             33 |                                         0 |                                   7 |
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |             0 |               169 |               164 |                   169 |            140 |                                         0 |                                   8 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                   129 |            110 |                                       129 |                                   8 |
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |             0 |                70 |                11 |                    70 |             11 |                                         0 |                                  10 |
| 2026-05-22           | DECISION_LOG            |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         1 |                                  10 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |             0 |               153 |                 9 |                   153 |              4 |                                         0 |                                  11 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |             0 |               248 |                12 |                   248 |              9 |                                         0 |                                  12 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             5 |                 6 |                 6 |                     6 |              5 |                                         6 |                                  12 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |             0 |                47 |                 0 |                    47 |              0 |                                         0 |                                  13 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |             0 |                84 |                83 |                    85 |             75 |                                         0 |                                  14 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |             0 |                72 |                73 |                    73 |             72 |                                        72 |                                  14 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |             0 |                27 |                24 |                    27 |             21 |                                         0 |                                  15 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |             0 |                21 |                24 |                    24 |             18 |                                        21 |                                  15 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                  16 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                    65 |              0 |                                         0 |                                  17 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                  17 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |    880 |
| PRICE_JOIN_MISS                         |    668 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    212 |

## Future-bar reason
| future_bar_reason   |   rows |
|:--------------------|-------:|
| HAS_5D_FUTURE_BARS  |   1350 |
| TOO_RECENT_FOR_5D   |    358 |
| PRICE_JOIN_MISS     |     52 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.