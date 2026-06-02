# SLINGSHOT Scope / Stage / Price Diagnostics — 2026-06-02

Measurement-only. No SLINGSHOT rule, gate, label, ranking, status, or trade-permission logic changed.

## Evaluability stage funnel
| evaluability_stage                |   rows |
|:----------------------------------|-------:|
| MISSING_ENTRY                     |     78 |
| FULL_PLAN_WAITING_FOR_FUTURE_BARS |     60 |
| OK_EVALUABLE                      |      5 |

## Decision-log target/R:R backfill
- Total DECISION_LOG rows enriched inside the learning loop: **0**
- From same-date SLINGSHOT_DIAGNOSTIC rows: **0**
- From same-date universe plan rows: **0**
- This is measurement-only enrichment. It does not change actionability skill output, final_trade_status, action_label, ranking, council routing, or trade permission.

## Source scope × SLINGSHOT scope
| source_scope_resolved   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:------------------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| DECISION_LOG            | SLINGSHOT_PRIMARY               |     71 |           32 |          32 |            32 |                32 |                71 |                    41 |              2 |                                         0 |                                  14 |
| SLINGSHOT_DIAGNOSTIC    | SLINGSHOT_PRIMARY               |     71 |           32 |          32 |            32 |                32 |                71 |                    41 |              2 |                                         0 |                                  14 |
| DECISION_LOG            | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                  14 |

## Setup family × SLINGSHOT scope
| setup_family   | slingshot_scope_resolved        |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------|:--------------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| SLINGSHOT      | SLINGSHOT_PRIMARY               |    142 |           64 |          64 |            64 |                64 |               142 |                    82 |              4 |                                         0 |                                  14 |
| DELAYED_EP     | SLINGSHOT_OVERLAY_OR_DIAGNOSTIC |      1 |            1 |           1 |             1 |                 1 |                 1 |                     1 |              1 |                                         0 |                                  14 |

## Signal-date summary
| signal_date_parsed   | source_scope_resolved   |   rows |   with_entry |   with_stop |   with_target |   with_planned_rr |   with_price_data |   with_5d_future_bars |   ok_evaluable |   decision_log_backfilled_from_diagnostic |   median_business_days_since_signal |
|:---------------------|:------------------------|-------:|-------------:|------------:|--------------:|------------------:|------------------:|----------------------:|---------------:|------------------------------------------:|------------------------------------:|
| 2026-05-27           | SLINGSHOT_DIAGNOSTIC    |     30 |           30 |          30 |            30 |                30 |                30 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-27           | DECISION_LOG            |     30 |           30 |          30 |            30 |                30 |                30 |                     0 |              0 |                                         0 |                                   4 |
| 2026-05-15           | SLINGSHOT_DIAGNOSTIC    |      1 |            0 |           0 |             0 |                 0 |                 1 |                     1 |              0 |                                         0 |                                  12 |
| 2026-05-15           | DECISION_LOG            |      1 |            0 |           0 |             0 |                 0 |                 1 |                     1 |              0 |                                         0 |                                  12 |
| 2026-05-13           | DECISION_LOG            |     41 |            3 |           3 |             3 |                 3 |                41 |                    41 |              3 |                                         0 |                                  14 |
| 2026-05-13           | SLINGSHOT_DIAGNOSTIC    |     40 |            2 |           2 |             2 |                 2 |                40 |                    40 |              2 |                                         0 |                                  14 |

## Price-data reason
| price_data_reason   |   rows |
|:--------------------|-------:|
| PRICE_DATA_OK       |    143 |

## Future-bar reason
| future_bar_reason   |   rows |
|:--------------------|-------:|
| HAS_5D_FUTURE_BARS  |     83 |
| TOO_RECENT_FOR_5D   |     60 |

## Interpretation
- `MISSING_ENTRY` rows remain an upstream/scope issue; they should be split into primary-vs-overlay/context before judging SLINGSHOT expectancy.
- `ENTRY_STOP_NO_TARGET` rows are an upstream target/R:R-completion issue.
- `FULL_PLAN_WAITING_FOR_FUTURE_BARS` rows are field-complete enough for later outcome review, but T+5 has not matured or future bars are not yet available.
- `PRICE_JOIN_MISS` after 5+ business days should be treated as an outcome-data bug.