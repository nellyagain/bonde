# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-05-31

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| FULL_PLAN_NO_PRICE_DATA           |    548 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    404 |
| MISSING_ENTRY                     |    221 |
| OK_EVALUABLE                      |    135 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |     94 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **578**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **289**
- From same-date universe plan rows: **289**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    843 |          721 |         721 |           721 |               721 |               313 |                   592 |             92 |                                         0 |                                   8 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    333 |          291 |         291 |           291 |               291 |               333 |                   143 |             97 |                                       289 |                                   4 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    168 |          168 |         168 |           168 |               168 |                70 |                    89 |             17 |                                         0 |                                   7 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                    57 |              0 |                                         0 |                                  12 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                  13 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   1171 |         1007 |        1007 |          1007 |              1007 |               644 |                   733 |            189 |                                       289 |                                 8   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |     76 |           76 |          76 |            76 |                76 |                30 |                    37 |             12 |                                         0 |                                 6   |
| EP9M           | SLINGSHOT_OVERLAY               |     44 |           44 |          44 |            44 |                44 |                15 |                    31 |              3 |                                         0 |                                 7   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                    28 |              0 |                                         0 |                                12   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     18 |           18 |          18 |            18 |                18 |                14 |                     8 |              2 |                                         0 |                                 6   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     14 |           14 |          14 |            14 |                14 |                 4 |                     8 |              0 |                                         0 |                                 7   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                12   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                    11 |              0 |                                         0 |                                12   |
| PAUSE          | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             8 |                 8 |                 4 |                     2 |              0 |                                         0 |                                 5   |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      6 |            6 |           6 |             6 |                 6 |                 3 |                     2 |              0 |                                         0 |                                 4   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      5 |            5 |           5 |             5 |                 5 |                 2 |                     2 |              0 |                                         0 |                                 4   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     4 |              0 |                                         0 |                                12.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 2 |                     2 |              1 |                                         0 |                                13   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     1 |              0 |                                         0 |                                 4.5 |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-29           | SLINGSHOT_DIAGNOSTIC    |     52 |           52 |          52 |            52 |                52 |                 0 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-27           | DECISION_LOG            |     60 |           60 |          60 |            60 |                60 |                60 |                     0 |              0 |                                        60 |                                   3 |
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     39 |           39 |          39 |            39 |                39 |                39 |                     0 |              0 |                                         0 |                                   3 |
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |           169 |               169 |               164 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                     0 |              0 |                                       129 |                                   4 |
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |            70 |                70 |                11 |                     0 |              0 |                                         0 |                                   6 |
| 2026-05-22           | DECISION_LOG            |      1 |            1 |           1 |             1 |                 1 |                 1 |                     0 |              0 |                                         1 |                                   6 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |           153 |               153 |                 9 |                   153 |              4 |                                         0 |                                   7 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |           248 |               248 |                12 |                   248 |              9 |                                         0 |                                   8 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     6 |              5 |                                         6 |                                   8 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |            47 |                47 |                 0 |                    47 |              0 |                                         0 |                                   9 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |            84 |                84 |                83 |                    85 |             75 |                                         0 |                                  10 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |            72 |                72 |                73 |                    73 |             72 |                                        72 |                                  10 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |            27 |                27 |                24 |                    27 |             21 |                                         0 |                                  11 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |            21 |                21 |                24 |                    24 |             18 |                                        21 |                                  11 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                  12 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                    65 |              0 |                                         0 |                                  13 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                  13 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |    734 |
| PRICE_JOIN_MISS                         |    611 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |     57 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| HAS_5D_FUTURE_BARS                  |    882 |
| TOO_RECENT_FOR_5D                   |    449 |
| PRICE_JOIN_MISS                     |     59 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |     12 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.