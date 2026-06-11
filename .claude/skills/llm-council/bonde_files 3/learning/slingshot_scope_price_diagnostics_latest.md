# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-11

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| ENTRY_STOP_NO_TARGET              |   1081 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    478 |
| FULL_PLAN_NO_PRICE_DATA           |    339 |
| OK_EVALUABLE                      |    215 |
| MISSING_ENTRY                     |    184 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |     89 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **1172**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **586**
- From same-date universe plan rows: **586**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |   1451 |         1328 |        1328 |           583 |              1304 |               577 |                  1086 |            287 |                                         0 |                                  12 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    590 |          586 |         586 |           446 |               571 |               590 |                   351 |            315 |                                       585 |                                   8 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    287 |          287 |         287 |            91 |               259 |               133 |                   239 |             72 |                                         0 |                                  11 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                 0 |                    57 |              0 |                                         0 |                                  20 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         1 |                                   7 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   2027 |         1900 |        1900 |          1027 |              1868 |              1161 |                  1430 |            601 |                                       585 |                                11   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |    123 |          123 |         123 |            38 |               114 |                52 |                   108 |             32 |                                         0 |                                12   |
| EP9M           | SLINGSHOT_OVERLAY               |     79 |           79 |          79 |            34 |                78 |                33 |                    66 |             20 |                                         0 |                                11   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     32 |           32 |          32 |             3 |                17 |                14 |                    19 |              2 |                                         0 |                                 8   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                 0 |                    28 |              0 |                                         0 |                                20   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     25 |           25 |          25 |             5 |                23 |                18 |                    24 |              8 |                                         0 |                                12   |
| PAUSE          | SLINGSHOT_OVERLAY               |     14 |           14 |          14 |             5 |                13 |                 8 |                    11 |              6 |                                         0 |                                 9   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |     14 |           14 |          14 |             2 |                 7 |                 6 |                     7 |              1 |                                         0 |                                 5   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                20   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 0 |                    11 |              0 |                                         0 |                                20   |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |     10 |           10 |          10 |             4 |                10 |                 7 |                     8 |              4 |                                         0 |                                10.5 |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      4 |            4 |           4 |             2 |                 4 |                 1 |                     3 |              0 |                                         0 |                                 7.5 |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 0 |                     4 |              0 |                                         0 |                                20.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 1 |                     2 |              1 |                                         1 |                                14   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-06-10           | SLINGSHOT_DIAGNOSTIC    |     50 |           50 |          50 |            47 |                47 |                 0 |                     0 |              0 |                                         0 |                                   1 |
| 2026-06-09           | SLINGSHOT_DIAGNOSTIC    |    133 |          133 |         133 |           119 |               119 |               129 |                     0 |              0 |                                         0 |                                   2 |
| 2026-06-09           | DECISION_LOG            |    116 |          116 |         116 |           107 |               107 |               116 |                     0 |              0 |                                       116 |                                   2 |
| 2026-06-08           | SLINGSHOT_DIAGNOSTIC    |     34 |           33 |          33 |            22 |                22 |                34 |                     0 |              0 |                                         0 |                                   3 |
| 2026-06-08           | DECISION_LOG            |     18 |           17 |          17 |            16 |                16 |                18 |                     0 |              0 |                                        17 |                                   3 |
| 2026-06-05           | SLINGSHOT_DIAGNOSTIC    |     77 |           77 |          77 |            77 |                77 |                 0 |                     0 |              0 |                                         0 |                                   4 |
| 2026-06-04           | SLINGSHOT_DIAGNOSTIC    |    119 |          119 |         119 |           114 |               114 |               119 |                     0 |              0 |                                         0 |                                   5 |
| 2026-06-04           | DECISION_LOG            |    105 |          105 |         105 |           101 |               102 |               105 |                     0 |              0 |                                       104 |                                   5 |
| 2026-06-03           | SLINGSHOT_DIAGNOSTIC    |     71 |           71 |          71 |            69 |                69 |                 0 |                    71 |              0 |                                         0 |                                   6 |
| 2026-06-02           | SLINGSHOT_DIAGNOSTIC    |    161 |          161 |         161 |           154 |               154 |                12 |                   161 |             10 |                                         0 |                                   7 |
| 2026-06-02           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     6 |              5 |                                         6 |                                   7 |
| 2026-06-01           | SLINGSHOT_DIAGNOSTIC    |     82 |           82 |          82 |            72 |                72 |                74 |                    82 |             56 |                                         0 |                                   8 |
| 2026-06-01           | DECISION_LOG            |     54 |           54 |          54 |            52 |                52 |                54 |                    54 |             51 |                                        54 |                                   8 |
| 2026-05-29           | SLINGSHOT_DIAGNOSTIC    |     52 |           52 |          52 |             0 |                52 |                 0 |                    52 |              0 |                                         0 |                                   9 |
| 2026-05-27           | DECISION_LOG            |     60 |           60 |          60 |            30 |                60 |                60 |                    60 |             54 |                                        60 |                                  11 |
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     39 |           39 |          39 |             0 |                39 |                39 |                    39 |             33 |                                         0 |                                  11 |
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |             0 |               169 |               164 |                   169 |            140 |                                         0 |                                  12 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                   129 |            110 |                                       129 |                                  12 |
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |             0 |                70 |                11 |                    70 |             11 |                                         0 |                                  14 |
| 2026-05-22           | DECISION_LOG            |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         1 |                                  14 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |             0 |               153 |                 9 |                   153 |              4 |                                         0 |                                  15 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |             0 |               248 |                12 |                   248 |              9 |                                         0 |                                  16 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             5 |                 6 |                 6 |                     6 |              5 |                                         6 |                                  16 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |             0 |                47 |                 0 |                    47 |              0 |                                         0 |                                  17 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |             0 |                84 |                83 |                    85 |             75 |                                         0 |                                  18 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |             0 |                72 |                73 |                    73 |             72 |                                        72 |                                  18 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |             0 |                27 |                24 |                    27 |             21 |                                         0 |                                  19 |
| 2026-05-15           | DECISION_LOG            |     23 |           21 |          21 |             0 |                21 |                23 |                    23 |             18 |                                        21 |                                  19 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                  20 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                 0 |                    65 |              0 |                                         0 |                                  21 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |   1301 |
| PRICE_JOIN_MISS                         |    954 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    131 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| HAS_5D_FUTURE_BARS                  |   1734 |
| TOO_RECENT_FOR_5D                   |    428 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |    224 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.