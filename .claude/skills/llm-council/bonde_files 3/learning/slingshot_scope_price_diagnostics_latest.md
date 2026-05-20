# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-05-20

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| MISSING_ENTRY                     |    221 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |    202 |
| FULL_PLAN_NO_PRICE_DATA           |     52 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **186**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **93**
- From same-date universe plan rows: **93**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    256 |          134 |         134 |           134 |               134 |               135 |                     0 |              0 |                                         0 |                                   3 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |    137 |           95 |          95 |            95 |                95 |               137 |                     0 |              0 |                                        93 |                                   2 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                17 |                     0 |              0 |                                         0 |                                   4 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |     24 |           24 |          24 |            24 |                24 |                13 |                     0 |              0 |                                         0 |                                   2 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     0 |              0 |                                         0 |                                   5 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |    393 |          229 |         229 |           229 |               229 |               272 |                     0 |              0 |                                        93 |                                 3   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                10 |                     0 |              0 |                                         0 |                                 4   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 4   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |     11 |           11 |          11 |            11 |                11 |                 8 |                     0 |              0 |                                         0 |                                 2   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 4 |                     0 |              0 |                                         0 |                                 4   |
| EP9M           | SLINGSHOT_OVERLAY               |      5 |            5 |           5 |             5 |                 5 |                 3 |                     0 |              0 |                                         0 |                                 2   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 2 |                     0 |              0 |                                         0 |                                 4.5 |
| DELAYED_EP     | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 1   |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      2 |            1 |           1 |             1 |                 1 |                 2 |                     0 |              0 |                                         0 |                                 5   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 2 |                     0 |              0 |                                         0 |                                 2   |
| EP_SPIKE       | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| PAUSE          | SLINGSHOT_OVERLAY               |      2 |            2 |           2 |             2 |                 2 |                 0 |                     0 |              0 |                                         0 |                                 2   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-19           | SLINGSHOT_DIAGNOSTIC    |     47 |           47 |          47 |            47 |                47 |                 0 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-18           | SLINGSHOT_DIAGNOSTIC    |     85 |           84 |          84 |            84 |                84 |                83 |                     0 |              0 |                                         0 |                                   2 |
| 2026-05-18           | DECISION_LOG            |     73 |           72 |          72 |            72 |                72 |                73 |                     0 |              0 |                                        72 |                                   2 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     27 |           27 |          27 |            27 |                27 |                24 |                     0 |              0 |                                         0 |                                   3 |
| 2026-05-15           | DECISION_LOG            |     24 |           21 |          21 |            21 |                21 |                24 |                     0 |              0 |                                        21 |                                   3 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                58 |                     0 |              0 |                                         0 |                                   5 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                     0 |              0 |                                         0 |                                   5 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| PRICE_DATA_OK                           |    303 |
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    165 |
| PRICE_JOIN_MISS                         |      7 |

## Future-bar reason
| future_bar_reason                   |   rows |
|:------------------------------------|-------:|
| TOO_RECENT_FOR_5D                   |    369 |
| PRICE_WINDOW_INCOMPLETE_OR_CALC_BUG |     99 |
| PRICE_JOIN_MISS                     |      7 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.