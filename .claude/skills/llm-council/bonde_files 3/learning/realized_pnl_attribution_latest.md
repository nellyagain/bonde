# Realized P&L Attribution — 2026-06-26

_Broker-export mode. Raw IBKR CSVs are normalized; open positions are separated from closed realized P&L. Stable latest CSVs replace prior generated broker files each run._

## Source files
- `/content/drive/MyDrive/bonde_learning/_inbox/ibkr_trades_2026-05-16.csv`
- `/content/drive/MyDrive/bonde_learning/_inbox/ibkr_trades_2026-05-18.csv`

## Overall
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| OVERALL      | ALL           |        2 |               2 |                   1 |            2.02265 |          2.02265 |             2.02265 |           50 |       2.02265 |              0 |               nan |     237.919 |   118.959 |

## Closed vs open handling
- Closed realized rows included in P&L: **2**
- Open-position rows excluded from realized P&L: **4**
- Closed realized net P&L: **237.92**
- Rows with realized R computed: **1**

## Trade-state summary
| trade_state     |   rows |   total_pnl |
|:----------------|-------:|------------:|
| CLOSED_REALIZED |      2 |     237.919 |
| OPEN_POSITION   |      4 |       0     |

## Risk/R calculation status
| slice_name   | slice_value                   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:------------------------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| risk_status  | PNL_ONLY_MISSING_RISK         |        1 |               1 |                   0 |          nan       |        nan       |           nan       |          nan |     nan       |            nan |               nan |     19.4723 |   19.4723 |
| risk_status  | R_AVAILABLE_FROM_DECISION_LOG |        1 |               1 |                   1 |            2.02265 |          2.02265 |             2.02265 |          100 |       2.02265 |              0 |               nan |    218.446  |  218.446  |

## Bonde match status
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| match_status | BONDE_MATCHED |        1 |               1 |                   1 |            2.02265 |          2.02265 |             2.02265 |          100 |       2.02265 |              0 |               nan |    218.446  |  218.446  |
| match_status | NON_BONDE     |        1 |               1 |                   0 |          nan       |        nan       |           nan       |          nan |     nan       |            nan |               nan |     19.4723 |   19.4723 |

## By setup_family
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| setup_family | EP_ACTIVE     |        1 |               1 |                   1 |            2.02265 |          2.02265 |             2.02265 |          100 |       2.02265 |              0 |               nan |    218.446  |  218.446  |
| setup_family | nan           |        1 |               1 |                   0 |          nan       |        nan       |           nan       |          nan |     nan       |            nan |               nan |     19.4723 |   19.4723 |

## By action_label
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| action_label | B             |        1 |               1 |                   1 |            2.02265 |          2.02265 |             2.02265 |          100 |       2.02265 |              0 |               nan |    218.446  |  218.446  |
| action_label | nan           |        1 |               1 |                   0 |          nan       |        nan       |           nan       |          nan |     nan       |            nan |               nan |     19.4723 |   19.4723 |

## By final_trade_status
| slice_name         | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| final_trade_status | WATCH         |        1 |               1 |                   1 |            2.02265 |          2.02265 |             2.02265 |          100 |       2.02265 |              0 |               nan |    218.446  |  218.446  |
| final_trade_status | nan           |        1 |               1 |                   0 |          nan       |        nan       |           nan       |          nan |     nan       |            nan |               nan |     19.4723 |   19.4723 |

## By sugar_baby_flag
| slice_name      |   slice_value |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:----------------|--------------:|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| sugar_baby_flag |           nan |        2 |               2 |                   1 |            2.02265 |          2.02265 |             2.02265 |           50 |       2.02265 |              0 |               nan |     237.919 |   118.959 |

## By ep9m_context_type
| slice_name        | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:------------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| ep9m_context_type |               |        1 |               1 |                   1 |            2.02265 |          2.02265 |             2.02265 |          100 |       2.02265 |              0 |               nan |    218.446  |  218.446  |
| ep9m_context_type | nan           |        1 |               1 |                   0 |          nan       |        nan       |           nan       |          nan |     nan       |            nan |               nan |     19.4723 |   19.4723 |

## Interpretation rules
- This report excludes open-position rows from realized P&L.
- `R_AVAILABLE_FROM_DECISION_LOG` means realized R was computed from broker net P&L divided by planned risk from decision-log trigger/stop.
- `PNL_ONLY_MISSING_RISK` means P&L is usable but R-multiple is not yet computable.
- `NON_BONDE` rows are kept for account reconciliation but excluded from Bonde-only conclusions.
- `AMBIGUOUS_MATCH` rows should not be used as clean Bonde evidence unless manually confirmed.