# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-02

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| ENTRY_STOP_NO_TARGET              |   1025 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    280 |
| MISSING_ENTRY                     |    221 |
| OK_EVALUABLE                      |      8 |
| FULL_PLAN_NO_PRICE_DATA           |      3 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |      1 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **686**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **343**
- From same-date universe plan rows: **343**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    899 |          777 |         777 |            53 |               774 |               368 |                   644 |             97 |                                         0 |                                   9 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    387 |          345 |         345 |           219 |               343 |               387 |                   144 |             98 |                                       343 |                                   5 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    194 |          194 |         194 |            19 |               187 |                89 |                   107 |             23 |                                         0 |                                   7 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                    57 |              0 |                                         0 |                                  13 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                  14 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   1280 |         1116 |        1116 |           272 |              1112 |               753 |                   786 |            195 |                                       343 |                                 8   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |     86 |           86 |          86 |             7 |                83 |                36 |                    50 |             14 |                                         0 |                                 7   |
| EP9M           | SLINGSHOT_OVERLAY               |     52 |           52 |          52 |             8 |                52 |                23 |                    31 |              3 |                                         0 |                                 8   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                    28 |              0 |                                         0 |                                13   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     21 |           21 |          21 |             2 |                20 |                17 |                    11 |              4 |                                         0 |                                 7   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     17 |           17 |          17 |             0 |                14 |                 4 |                     8 |              0 |                                         0 |                                 5   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                13   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                    11 |              0 |                                         0 |                                13   |
| PAUSE          | SLINGSHOT_OVERLAY               |      9 |            9 |           9 |             1 |                 9 |                 5 |                     4 |              2 |                                         0 |                                 5   |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      7 |            7 |           7 |             1 |                 7 |                 4 |                     2 |              0 |                                         0 |                                 5   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      6 |            6 |           6 |             0 |                 5 |                 2 |                     2 |              0 |                                         0 |                                 4.5 |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     4 |              0 |                                         0 |                                13.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 2 |                     2 |              1 |                                         0 |                                14   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             0 |                 2 |                 0 |                     1 |              0 |                                         0 |                                 5.5 |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-06-01           | SLINGSHOT_DIAGNOSTIC    |     82 |           82 |          82 |            72 |                72 |                74 |                     0 |              0 |                                         0 |                                   1 |
| 2026-06-01           | DECISION_LOG            |     54 |           54 |          54 |            52 |                52 |                54 |                     0 |              0 |                                        54 |                                   1 |
| 2026-05-29           | SLINGSHOT_DIAGNOSTIC    |     52 |           52 |          52 |             0 |                52 |                 0 |                     0 |              0 |                                         0 |                                   2 |
| 2026-05-27           | DECISION_LOG            |     60 |           60 |          60 |            30 |                60 |                60 |                     0 |              0 |                                        60 |                                   4 |
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     39 |           39 |          39 |             0 |                39 |                39 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |             0 |               169 |               164 |                     0 |              0 |                                         0 |                                   5 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                     0 |              0 |                                       129 |                                   5 |
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |             0 |                70 |                11 |                    70 |             11 |                                         0 |                                   7 |
| 2026-05-22           | DECISION_LOG            |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         1 |                                   7 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |             0 |               153 |                 9 |                   153 |              4 |                                         0 |                                   8 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |             0 |               248 |                12 |                   248 |              9 |                                         0 |                                   9 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             5 |                 6 |                 6 |                     6 |              5 |                                         6 |                                   9 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |             0 |                47 |                 0 |                    47 |              0 |                                         0 |                                  10 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |             0 |                84 |                83 |                    85 |             75 |                                         0 |                                  11 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |             0 |                72 |                73 |                    73 |             72 |                                        72 |                                  11 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |             0 |                27 |                24 |                    27 |             21 |                                         0 |                                  12 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |             0 |                21 |                24 |                    24 |             18 |                                        21 |                                  12 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                  13 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                    65 |              0 |                                         0 |                                  14 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                  14 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |    862 |
| PRICE_JOIN_MISS                         |    616 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |     60 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| HAS_5D_FUTURE_BARS                  |    953 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |    293 |
| TOO_RECENT_FOR_5D                   |    287 |
| PRICE_JOIN_MISS                     |      5 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.