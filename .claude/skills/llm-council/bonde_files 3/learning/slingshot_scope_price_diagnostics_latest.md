# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-05-27

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| FULL_PLAN_NO_PRICE_DATA           |    496 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    332 |
| MISSING_ENTRY                     |    221 |
| OK_EVALUABLE                      |    117 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |     85 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **458**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **229**
- From same-date universe plan rows: **229**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    777 |          655 |         655 |           655 |               655 |               282 |                   216 |             86 |                                         0 |                                   5 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    273 |          231 |         231 |           231 |               231 |               273 |                   137 |             92 |                                       229 |                                   7 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    143 |          143 |         143 |           143 |               143 |                62 |                    17 |             10 |                                         0 |                                   4 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                    57 |              0 |                                         0 |                                   9 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                  10 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |   1047 |          883 |         883 |           883 |               883 |               554 |                   353 |            178 |                                       229 |                                 5   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |     68 |           68 |          68 |            68 |                68 |                29 |                     9 |              7 |                                         0 |                                 4   |
| EP9M           | SLINGSHOT_OVERLAY               |     37 |           37 |          37 |            37 |                37 |                11 |                     3 |              2 |                                         0 |                                 4   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                    28 |              0 |                                         0 |                                 9   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     17 |           17 |          17 |            17 |                17 |                14 |                     2 |              1 |                                         0 |                                 3   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                 9   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                    11 |              0 |                                         0 |                                 9   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |     10 |           10 |          10 |            10 |                10 |                 2 |                     2 |              0 |                                         0 |                                 4.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      5 |            5 |           5 |             5 |                 5 |                 3 |                     0 |              0 |                                         0 |                                 1   |
| PAUSE          | SLINGSHOT_OVERLAY               |      5 |            5 |           5 |             5 |                 5 |                 3 |                     1 |              0 |                                         0 |                                 3   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     4 |              0 |                                         0 |                                 9.5 |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      3 |            3 |           3 |             3 |                 3 |                 1 |                     0 |              0 |                                         0 |                                 4   |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 2 |                     2 |              1 |                                         0 |                                10   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      1 |            1 |           1 |             1 |                 1 |                 0 |                     0 |              0 |                                         0 |                                 5   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-26           | SLINGSHOT_DIAGNOSTIC    |    169 |          169 |         169 |           169 |               169 |               164 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-26           | DECISION_LOG            |    129 |          129 |         129 |           129 |               129 |               129 |                     0 |              0 |                                       129 |                                   1 |
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |            70 |                70 |                11 |                     0 |              0 |                                         0 |                                   3 |
| 2026-05-22           | DECISION_LOG            |      1 |            1 |           1 |             1 |                 1 |                 1 |                     0 |              0 |                                         1 |                                   3 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |           153 |               153 |                 9 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |           248 |               248 |                12 |                     0 |              0 |                                         0 |                                   5 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     0 |              0 |                                         6 |                                   5 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |            47 |                47 |                 0 |                     0 |              0 |                                         0 |                                   6 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |            84 |                84 |                83 |                    85 |             75 |                                         0 |                                   7 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |            72 |                72 |                73 |                    73 |             72 |                                        72 |                                   7 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |            27 |                27 |                24 |                    27 |             21 |                                         0 |                                   8 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |            21 |                21 |                24 |                    24 |             18 |                                        21 |                                   8 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                   9 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                    65 |              0 |                                         0 |                                  10 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                  10 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |    635 |
| PRICE_JOIN_MISS                         |    408 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    208 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| TOO_RECENT_FOR_5D                   |    522 |
| HAS_5D_FUTURE_BARS                  |    428 |
| PRICE_JOIN_MISS                     |    283 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |     18 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.