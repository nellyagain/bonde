# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-05-22

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| FULL_PLAN_NO_PRICE_DATA           |    431 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    226 |
| MISSING_ENTRY                     |    221 |
| OK_EVALUABLE                      |      3 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **198**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **99**
- From same-date universe plan rows: **99**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    591 |          469 |         469 |           469 |               469 |               144 |                   121 |              0 |                                         0 |                                   2 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    143 |          101 |         101 |           101 |               101 |               143 |                    40 |              2 |                                        99 |                                   4 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |     89 |           89 |          89 |            89 |                89 |                25 |                     0 |              0 |                                         0 |                                   2 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                    57 |              0 |                                         0 |                                   6 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                   7 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |    732 |          568 |         568 |           568 |               568 |               287 |                   161 |              2 |                                        99 |                                 3   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |     37 |           37 |          37 |            37 |                37 |                14 |                     0 |              0 |                                         0 |                                 2   |
| EP9M           | SLINGSHOT_OVERLAY               |     31 |           31 |          31 |            31 |                31 |                 5 |                     0 |              0 |                                         0 |                                 2   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                    28 |              0 |                                         0 |                                 6   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                    13 |              0 |                                         0 |                                 6   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                    11 |              0 |                                         0 |                                 6   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             8 |                 8 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |      8 |            8 |           8 |             8 |                 8 |                 6 |                     0 |              0 |                                         0 |                                 1.5 |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     4 |              0 |                                         0 |                                 6.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 3   |
| EP_SPIKE       | SLINGSHOT_PRIMARY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 1.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 2 |                     2 |              1 |                                         0 |                                 7   |
| PAUSE          | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 4   |
| ANTICIPATION   | SLINGSHOT_OVERLAY               |      1 |            1 |           1 |             1 |                 1 |                 0 |                     0 |              0 |                                         0 |                                 2   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-21           | SLINGSHOT_DIAGNOSTIC    |    152 |          152 |         152 |           152 |               152 |                 9 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-20           | SLINGSHOT_DIAGNOSTIC    |    248 |          248 |         248 |           248 |               248 |                12 |                     0 |              0 |                                         0 |                                   2 |
| 2026-05-20           | DECISION_LOG            |      6 |            6 |           6 |             6 |                 6 |                 6 |                     0 |              0 |                                         6 |                                   2 |
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |            47 |                47 |                 0 |                     0 |              0 |                                         0 |                                   3 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |            84 |                84 |                83 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |            72 |                72 |                73 |                     0 |              0 |                                        72 |                                   4 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |            27 |                27 |                24 |                     0 |              0 |                                         0 |                                   5 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |            21 |                21 |                24 |                     0 |              0 |                                        21 |                                   5 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                   113 |              0 |                                         0 |                                   6 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                    65 |              0 |                                         0 |                                   7 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                   7 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    428 |
| PRICE_DATA_OK                           |    330 |
| PRICE_JOIN_MISS                         |    123 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| TOO_RECENT_FOR_5D                   |    611 |
| HAS_5D_FUTURE_BARS                  |    219 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |     48 |
| PRICE_JOIN_MISS                     |      3 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.