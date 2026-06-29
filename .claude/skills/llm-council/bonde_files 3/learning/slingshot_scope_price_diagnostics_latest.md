# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-29

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| ENTRY_STOP_NO_TARGET              |   1176 |
| OK_EVALUABLE                      |    996 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    902 |
| FULL_PLAN_NO_PRICE_DATA           |    743 |
| MISSING_ENTRY                     |    185 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |    167 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **2382**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **1191**
- From same-date universe plan rows: **1191**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |   2404 |         2280 |        2280 |          1501 |              2222 |              1187 |                  1885 |            674 |                                         0 |                                16   |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |   1194 |         1190 |        1190 |          1028 |              1156 |              1194 |                   768 |            698 |                                      1189 |                                11   |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    512 |          512 |         512 |           277 |               449 |               268 |                   393 |            124 |                                         0 |                                15.5 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                 0 |                    57 |              0 |                                         0 |                                32   |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            2 |           2 |             2 |                 2 |                 2 |                     1 |              1 |                                         2 |                                11   |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   3576 |         3448 |        3448 |          2525 |              3369 |              2372 |                  2633 |           1368 |                                      1189 |                                14   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |    246 |          246 |         246 |           144 |               222 |               127 |                   174 |             47 |                                         0 |                                12.5 |
| EP9M           | SLINGSHOT_OVERLAY               |    136 |          136 |         136 |            91 |               135 |                70 |                   106 |             40 |                                         0 |                                17   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     50 |           50 |          50 |             6 |                20 |                16 |                    45 |              7 |                                         0 |                                15   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     37 |           37 |          37 |            10 |                30 |                27 |                    31 |             10 |                                         0 |                                20   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                 0 |                    28 |              0 |                                         0 |                                32   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |     22 |           22 |          22 |             4 |                 9 |                 9 |                    20 |              4 |                                         0 |                                14.5 |
| PAUSE          | SLINGSHOT_OVERLAY               |     20 |           20 |          20 |            11 |                19 |                13 |                    16 |              8 |                                         0 |                                18.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |     15 |           15 |          15 |             9 |                15 |                11 |                    14 |              9 |                                         0 |                                19   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                32   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 0 |                    11 |              0 |                                         0 |                                32   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             6 |                 8 |                 4 |                     7 |              3 |                                         0 |                                12   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 0 |                     4 |              0 |                                         0 |                                32.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      3 |            2 |           2 |             2 |                 2 |                 2 |                     2 |              1 |                                         2 |                                19   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-06-26           | SLINGSHOT_DIAGNOSTIC    |    160 |          160 |         160 |           151 |               151 |               160 |                     0 |              0 |                                         0 |                                   1 |
| 2026-06-26           | DECISION_LOG            |    102 |          102 |         102 |            99 |                99 |               102 |                     0 |              0 |                                       102 |                                   1 |
| 2026-06-25           | SLINGSHOT_DIAGNOSTIC    |     96 |           96 |          96 |            91 |                91 |                92 |                     0 |              0 |                                         0 |                                   2 |
| 2026-06-25           | DECISION_LOG            |     88 |           88 |          88 |            86 |                86 |                88 |                     0 |              0 |                                        88 |                                   2 |
| 2026-06-24           | SLINGSHOT_DIAGNOSTIC    |    131 |          131 |         131 |           112 |               114 |               131 |                     0 |              0 |                                         0 |                                   3 |
| 2026-06-24           | DECISION_LOG            |    106 |          106 |         106 |            96 |                98 |               106 |                     0 |              0 |                                       106 |                                   3 |
| 2026-06-23           | SLINGSHOT_DIAGNOSTIC    |    143 |          143 |         143 |           139 |               139 |               143 |                     0 |              0 |                                         0 |                                   4 |
| 2026-06-23           | DECISION_LOG            |    131 |          131 |         131 |           129 |               129 |               131 |                     0 |              0 |                                       131 |                                   4 |
| 2026-06-22           | SLINGSHOT_DIAGNOSTIC    |    108 |          108 |         108 |           105 |               105 |                 0 |                     0 |              0 |                                         0 |                                   5 |
| 2026-06-18           | SLINGSHOT_DIAGNOSTIC    |    119 |          118 |         118 |           112 |               112 |                42 |                   119 |             37 |                                         0 |                                   7 |
| 2026-06-18           | DECISION_LOG            |     34 |           34 |          34 |            32 |                32 |                34 |                    34 |             31 |                                        34 |                                   7 |
| 2026-06-17           | SLINGSHOT_DIAGNOSTIC    |     28 |           28 |          28 |            20 |                20 |                 0 |                    28 |              0 |                                         0 |                                   8 |
| 2026-06-16           | SLINGSHOT_DIAGNOSTIC    |     25 |           25 |          25 |            19 |                21 |                25 |                    25 |             19 |                                         0 |                                   9 |
| 2026-06-16           | DECISION_LOG            |     15 |           15 |          15 |            13 |                14 |                15 |                    15 |             13 |                                        15 |                                   9 |
| 2026-06-15           | SLINGSHOT_DIAGNOSTIC    |     33 |           33 |          33 |            33 |                33 |                33 |                    33 |             29 |                                         0 |                                  10 |
| 2026-06-15           | DECISION_LOG            |     24 |           24 |          24 |            24 |                24 |                24 |                    24 |             24 |                                        24 |                                  10 |
| 2026-06-12           | SLINGSHOT_DIAGNOSTIC    |    124 |          124 |         124 |           119 |               119 |               119 |                   124 |            110 |                                         0 |                                  11 |
| 2026-06-12           | DECISION_LOG            |    105 |          105 |         105 |           104 |               104 |               105 |                   105 |             97 |                                       105 |                                  11 |
| 2026-06-11           | SLINGSHOT_DIAGNOSTIC    |    211 |          211 |         211 |           203 |               203 |                 0 |                   211 |              0 |                                         0 |                                  12 |
| 2026-06-10           | SLINGSHOT_DIAGNOSTIC    |     50 |           50 |          50 |            47 |                47 |                 0 |                    50 |              0 |                                         0 |                                  13 |
| 2026-06-09           | SLINGSHOT_DIAGNOSTIC    |    133 |          133 |         133 |           119 |               119 |               129 |                   133 |            115 |                                         0 |                                  14 |
| 2026-06-09           | DECISION_LOG            |    116 |          116 |         116 |           107 |               107 |               116 |                   116 |            105 |                                       116 |                                  14 |
| 2026-06-08           | SLINGSHOT_DIAGNOSTIC    |     34 |           33 |          33 |            22 |                22 |                34 |                    34 |             22 |                                         0 |                                  15 |
| 2026-06-08           | DECISION_LOG            |     18 |           17 |          17 |            16 |                16 |                18 |                    18 |             16 |                                        17 |                                  15 |
| 2026-06-05           | SLINGSHOT_DIAGNOSTIC    |     77 |           77 |          77 |            77 |                77 |                 0 |                    77 |              0 |                                         0 |                                  16 |
| 2026-06-04           | SLINGSHOT_DIAGNOSTIC    |    119 |          119 |         119 |           114 |               114 |               119 |                   119 |            107 |                                         0 |                                  17 |
| 2026-06-04           | DECISION_LOG            |    105 |          105 |         105 |           101 |               102 |               105 |                   105 |             96 |                                       104 |                                  17 |
| 2026-06-03           | SLINGSHOT_DIAGNOSTIC    |     71 |           71 |          71 |            69 |                69 |                 0 |                    71 |              0 |                                         0 |                                  18 |
| 2026-06-02           | SLINGSHOT_DIAGNOSTIC    |    161 |          161 |         161 |           154 |               154 |                12 |                   161 |             10 |                                         0 |                                  19 |
| 2026-06-02           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     6 |              5 |                                         6 |                                  19 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |   2651 |
| PRICE_JOIN_MISS                         |   1514 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |      4 |

## Future-bar reason
| future_bar_reason   |   rows |
|:--------------------|-------:|
| HAS_5D_FUTURE_BARS  |   3104 |
| TOO_RECENT_FOR_5D   |    957 |
| PRICE_JOIN_MISS     |    108 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.