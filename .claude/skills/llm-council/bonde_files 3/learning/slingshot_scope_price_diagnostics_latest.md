# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-05-24

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| FULL_PLAN_NO_PRICE_DATA           |    440 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    295 |
| MISSING_ENTRY                     |    222 |
| OK_EVALUABLE                      |     42 |
| FULL_PLAN_NEVER_TRIGGERED_5D      |      6 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **302**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **151**
- From same-date universe plan rows: **151**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    644 |          522 |         522 |           522 |               522 |               196 |                   143 |             19 |                                         0 |                                   3 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    196 |          153 |         153 |           153 |               153 |               196 |                    64 |             20 |                                       151 |                                   5 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |    107 |          107 |         107 |           107 |               107 |                35 |                     5 |              2 |                                         0 |                                   3 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                    57 |              0 |                                         0 |                                   7 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                   8 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |    838 |          673 |         673 |           673 |               673 |               392 |                   207 |             39 |                                       151 |                                 3   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |     50 |           50 |          50 |            50 |                50 |                20 |                     3 |              1 |                                         0 |                                 2.5 |
| EP9M           | SLINGSHOT_OVERLAY               |     31 |           31 |          31 |            31 |                31 |                 5 |                     1 |              1 |                                         0 |                                 3   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                    28 |              0 |                                         0 |                                 7   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                 7   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                    11 |              0 |                                         0 |                                 7   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |     11 |           11 |          11 |            11 |                11 |                 8 |                     0 |              0 |                                         0 |                                 2   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             8 |                 8 |                 0 |                     0 |              0 |                                         0 |                                 3   |
| PAUSE          | SLINGSHOT_OVERLAY               |      4 |            4 |           4 |             4 |                 4 |                 2 |                     1 |              0 |                                         0 |                                 2.5 |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     4 |              0 |                                         0 |                                 7.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 4   |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 2 |                     2 |              1 |                                         0 |                                 8   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 2.5 |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      1 |            1 |           1 |             1 |                 1 |                 0 |                     0 |              0 |                                         0 |                                 3   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-22           | SLINGSHOT_DIAGNOSTIC    |     70 |           70 |          70 |            70 |                70 |                62 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-22           | DECISION_LOG            |     53 |           52 |          52 |            52 |                52 |                53 |                     0 |              0 |                                        52 |                                   1 |
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    153 |          153 |         153 |           153 |               153 |                 9 |                     0 |              0 |                                         0 |                                   2 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |           248 |               248 |                12 |                     0 |              0 |                                         0 |                                   3 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     0 |              0 |                                         6 |                                   3 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |            47 |                47 |                 0 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |            84 |                84 |                83 |                     0 |              0 |                                         0 |                                   5 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |            72 |                72 |                73 |                     0 |              0 |                                        72 |                                   5 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |            27 |                27 |                24 |                    27 |             21 |                                         0 |                                   6 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |            21 |                21 |                24 |                    24 |             18 |                                        21 |                                   6 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                   7 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                    65 |              0 |                                         0 |                                   8 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                   8 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |    445 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    435 |
| PRICE_JOIN_MISS                         |    125 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| TOO_RECENT_FOR_5D                   |    577 |
| HAS_5D_FUTURE_BARS                  |    270 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |    156 |
| PRICE_JOIN_MISS                     |      2 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.