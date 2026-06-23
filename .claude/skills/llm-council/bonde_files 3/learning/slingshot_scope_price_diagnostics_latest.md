# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-23

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| ENTRY_STOP_NO_TARGET              |   1122 |
| OK_EVALUABLE                      |    866 |
| FULL_PLAN_NO_PRICE_DATA           |    735 |
| MISSING_ENTRY                     |    185 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    169 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |    138 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **1534**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **767**
- From same-date universe plan rows: **767**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |   1975 |         1851 |        1851 |          1091 |              1812 |               762 |                  1727 |            604 |                                         0 |                                  15 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    771 |          767 |         767 |           622 |               748 |               771 |                   695 |            629 |                                       766 |                                  13 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    411 |          411 |         411 |           194 |               364 |               174 |                   346 |            108 |                                         0 |                                  15 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                 0 |                    57 |              0 |                                         0 |                                  28 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         1 |                                  15 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   2726 |         2598 |        2598 |          1709 |              2551 |              1525 |                  2406 |           1231 |                                       766 |                                15   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |    183 |          183 |         183 |            93 |               170 |                68 |                   153 |             43 |                                         0 |                                15   |
| EP9M           | SLINGSHOT_OVERLAY               |    111 |          111 |         111 |            66 |               110 |                45 |                    98 |             35 |                                         0 |                                15   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     48 |           48 |          48 |             6 |                20 |                16 |                    38 |              5 |                                         0 |                                11   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     32 |           32 |          32 |             9 |                28 |                23 |                    27 |             10 |                                         0 |                                20   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                 0 |                    28 |              0 |                                         0 |                                28   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |     20 |           20 |          20 |             4 |                 9 |                 8 |                    16 |              2 |                                         0 |                                11   |
| PAUSE          | SLINGSHOT_OVERLAY               |     16 |           16 |          16 |             7 |                15 |                 9 |                    14 |              7 |                                         0 |                                16.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |     14 |           14 |          14 |             8 |                14 |                10 |                    12 |              7 |                                         0 |                                15.5 |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                28   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 0 |                    11 |              0 |                                         0 |                                28   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      7 |            7 |           7 |             5 |                 7 |                 3 |                     4 |              1 |                                         0 |                                10   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 0 |                     4 |              0 |                                         0 |                                28.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 1 |                     2 |              1 |                                         1 |                                22   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-06-22           | SLINGSHOT_DIAGNOSTIC    |    108 |          108 |         108 |           105 |               105 |                 7 |                     0 |              0 |                                         0 |                                   1 |
| 2026-06-22           | DECISION_LOG            |      3 |            3 |           3 |             3 |                 3 |                 3 |                     0 |              0 |                                         3 |                                   1 |
| 2026-06-18           | SLINGSHOT_DIAGNOSTIC    |    119 |          118 |         118 |           112 |               112 |                42 |                     0 |              0 |                                         0 |                                   3 |
| 2026-06-18           | DECISION_LOG            |     34 |           34 |          34 |            32 |                32 |                34 |                     0 |              0 |                                        34 |                                   3 |
| 2026-06-17           | SLINGSHOT_DIAGNOSTIC    |     28 |           28 |          28 |            20 |                20 |                 0 |                     0 |              0 |                                         0 |                                   4 |
| 2026-06-16           | SLINGSHOT_DIAGNOSTIC    |     25 |           25 |          25 |            19 |                21 |                25 |                     0 |              0 |                                         0 |                                   5 |
| 2026-06-16           | DECISION_LOG            |     15 |           15 |          15 |            13 |                14 |                15 |                     0 |              0 |                                        15 |                                   5 |
| 2026-06-15           | SLINGSHOT_DIAGNOSTIC    |     33 |           33 |          33 |            33 |                33 |                33 |                     0 |              0 |                                         0 |                                   6 |
| 2026-06-15           | DECISION_LOG            |     24 |           24 |          24 |            24 |                24 |                24 |                     0 |              0 |                                        24 |                                   6 |
| 2026-06-12           | SLINGSHOT_DIAGNOSTIC    |    124 |          124 |         124 |           119 |               119 |               119 |                   124 |            110 |                                         0 |                                   7 |
| 2026-06-12           | DECISION_LOG            |    105 |          105 |         105 |           104 |               104 |               105 |                   105 |             97 |                                       105 |                                   7 |
| 2026-06-11           | SLINGSHOT_DIAGNOSTIC    |    211 |          211 |         211 |           203 |               203 |                 0 |                   211 |              0 |                                         0 |                                   8 |
| 2026-06-10           | SLINGSHOT_DIAGNOSTIC    |     50 |           50 |          50 |            47 |                47 |                 0 |                    50 |              0 |                                         0 |                                   9 |
| 2026-06-09           | SLINGSHOT_DIAGNOSTIC    |    133 |          133 |         133 |           119 |               119 |               129 |                   133 |            115 |                                         0 |                                  10 |
| 2026-06-09           | DECISION_LOG            |    116 |          116 |         116 |           107 |               107 |               116 |                   116 |            105 |                                       116 |                                  10 |
| 2026-06-08           | SLINGSHOT_DIAGNOSTIC    |     34 |           33 |          33 |            22 |                22 |                34 |                    34 |             22 |                                         0 |                                  11 |
| 2026-06-08           | DECISION_LOG            |     18 |           17 |          17 |            16 |                16 |                18 |                    18 |             16 |                                        17 |                                  11 |
| 2026-06-05           | SLINGSHOT_DIAGNOSTIC    |     77 |           77 |          77 |            77 |                77 |                 0 |                    77 |              0 |                                         0 |                                  12 |
| 2026-06-04           | SLINGSHOT_DIAGNOSTIC    |    119 |          119 |         119 |           114 |               114 |               119 |                   119 |            107 |                                         0 |                                  13 |
| 2026-06-04           | DECISION_LOG            |    105 |          105 |         105 |           101 |               102 |               105 |                   105 |             96 |                                       104 |                                  13 |
| 2026-06-03           | SLINGSHOT_DIAGNOSTIC    |     71 |           71 |          71 |            69 |                69 |                 0 |                    71 |              0 |                                         0 |                                  14 |
| 2026-06-02           | SLINGSHOT_DIAGNOSTIC    |    161 |          161 |         161 |           154 |               154 |                12 |                   161 |             10 |                                         0 |                                  15 |
| 2026-06-02           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     6 |              5 |                                         6 |                                  15 |
| 2026-06-01           | SLINGSHOT_DIAGNOSTIC    |     82 |           82 |          82 |            72 |                72 |                74 |                    82 |             56 |                                         0 |                                  16 |
| 2026-06-01           | DECISION_LOG            |     54 |           54 |          54 |            52 |                52 |                54 |                    54 |             51 |                                        54 |                                  16 |
| 2026-05-29           | SLINGSHOT_DIAGNOSTIC    |     52 |           52 |          52 |             0 |                52 |                 0 |                    52 |              0 |                                         0 |                                  17 |
| 2026-05-27           | DECISION_LOG            |     60 |           60 |          60 |            30 |                60 |                60 |                    60 |             54 |                                        60 |                                  19 |
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     39 |           39 |          39 |             0 |                39 |                39 |                    39 |             33 |                                         0 |                                  19 |
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |             0 |               169 |               164 |                   169 |            140 |                                         0 |                                  20 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                   129 |            110 |                                       129 |                                  20 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |   1708 |
| PRICE_JOIN_MISS                         |   1301 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    206 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| HAS_5D_FUTURE_BARS                  |   2826 |
| TOO_RECENT_FOR_5D                   |    292 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |     97 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.