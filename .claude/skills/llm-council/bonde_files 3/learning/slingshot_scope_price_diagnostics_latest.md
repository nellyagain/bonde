# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-05-16

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| MISSING_ENTRY                     |    184 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |     45 |
| FULL_PLAN_NO_PRICE_DATA           |      2 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **42**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **21**
- From same-date universe plan rows: **21**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |    144 |           21 |          21 |            21 |                21 |                23 |                     0 |              0 |                                         0 |                                   2 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     57 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   2 |
| DECISION_LOG            | SLINGSHOT_PRIMARY               |     23 |           21 |          21 |            21 |                21 |                23 |                     0 |              0 |                                        21 |                                   1 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_OVERLAY               |      7 |            5 |           5 |             5 |                 5 |                 5 |                     0 |              0 |                                         0 |                                   1 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |    167 |           42 |          42 |            42 |                42 |                46 |                     0 |              0 |                                        21 |                                 2   |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     28 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP_SPIKE       | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     13 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP9M           | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |     11 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2   |
| EP_ACTIVE      | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      4 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 2.5 |
| ACTIVE_BURST   | SLINGSHOT_OVERLAY               |      3 |            3 |           3 |             3 |                 3 |                 2 |                     0 |              0 |                                         0 |                                 1   |
| EP9M           | SLINGSHOT_OVERLAY               |      2 |            1 |           1 |             1 |                 1 |                 2 |                     0 |              0 |                                         0 |                                 1   |
| PAUSE          | SLINGSHOT_OVERLAY               |      2 |            1 |           1 |             1 |                 1 |                 1 |                     0 |              0 |                                         0 |                                 1   |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                 3   |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |     30 |           26 |          26 |            26 |                26 |                28 |                     0 |              0 |                                         0 |                                   1 |
| 2026-05-15           | DECISION_LOG            |     23 |           21 |          21 |            21 |                21 |                23 |                     0 |              0 |                                        21 |                                   1 |
| 2026-05-14           | SLINGSHOT_DIAGNOSTIC    |    113 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   2 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     65 |            0 |           0 |             0 |                 0 |                 0 |                     0 |              0 |                                         0 |                                   3 |

## Price-data reason
| price_data_reason                       |   rows |
|:----------------------------------------|-------:|
| TOO_RECENT_FOR_5D_OR_PRICE_JOIN_PENDING |    180 |
| PRICE_DATA_OK                           |     51 |

## Future-bar reason
| future_bar_reason   |   rows |
|:--------------------|-------:|
| TOO_RECENT_FOR_5D   |    231 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.