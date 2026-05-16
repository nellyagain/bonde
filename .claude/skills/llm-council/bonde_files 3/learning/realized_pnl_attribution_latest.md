# Realized P&L Attribution — 2026-05-16

_Broker-export mode. No manual R sheet required. Raw broker CSVs are normalized and joined to decision logs where possible._

## Source files
- `/content/drive/MyDrive/bonde_learning/_inbox/ibkr_trades_2026-05-16.csv`
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_2026-05-16/bonde_files 3/learning/realized_trades_master_v41330.csv`
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_latest/bonde_files 3/learning/realized_trades_master_v41330.csv`
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_master_v41330.csv`
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_2026-05-16/bonde_files 3/learning/realized_trades_template.csv`
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_latest/bonde_files 3/learning/realized_trades_template.csv`
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_template.csv`

## Overall
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| OVERALL      | ALL           |       10 |              10 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     241.286 |   24.1286 |

## Risk/R calculation status
| slice_name   | slice_value           |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:----------------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| risk_status  | PNL_ONLY_MISSING_RISK |       10 |              10 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     241.286 |   24.1286 |

## By setup_family
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |    avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|-----------:|
| setup_family | DELAYED_EP    |        2 |               2 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |    0.358377 |   0.179189 |
| setup_family | EP_ACTIVE     |        1 |               1 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |  219.194    | 219.194    |
| setup_family | UNKNOWN       |        1 |               1 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |    0.741115 |   0.741115 |
| setup_family | nan           |        6 |               6 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |   20.9918   |   3.49864  |

## By action_label
| slice_name   | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| action_label | B             |        4 |               4 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |    220.294  |  55.0734  |
| action_label | nan           |        6 |               6 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     20.9918 |   3.49864 |

## By final_trade_status
| slice_name         | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-------------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| final_trade_status | WATCH         |        4 |               4 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |    220.294  |  55.0734  |
| final_trade_status | nan           |        6 |               6 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     20.9918 |   3.49864 |

## By council_verdict
| slice_name      |   slice_value |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:----------------|--------------:|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| council_verdict |           nan |       10 |              10 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     241.286 |   24.1286 |

## By sugar_baby_flag
| slice_name      |   slice_value |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:----------------|--------------:|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| sugar_baby_flag |           nan |       10 |              10 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     241.286 |   24.1286 |

## By ep9m_context_type
| slice_name        |   slice_value |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:------------------|--------------:|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| ep9m_context_type |           nan |       10 |              10 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     241.286 |   24.1286 |

## By trade_taken_or_skipped
| slice_name             | slice_value   |   n_rows |   n_traded_rows |   n_with_realized_r |   total_realized_r |   avg_realized_r |   median_realized_r |   win_rate_r |   gross_win_r |   gross_loss_r |   profit_factor_r |   total_pnl |   avg_pnl |
|:-----------------------|:--------------|---------:|----------------:|--------------------:|-------------------:|-----------------:|--------------------:|-------------:|--------------:|---------------:|------------------:|------------:|----------:|
| trade_taken_or_skipped | TRADED        |       10 |              10 |                   0 |                nan |              nan |                 nan |          nan |           nan |            nan |               nan |     241.286 |   24.1286 |

## Interpretation rules
- Realized R is only calculated where broker P&L/entry/exit can be matched to a planned stop or risk amount.
- Rows marked `PNL_ONLY_MISSING_RISK` are still useful for P&L, but not for R-multiple attribution.
- Use this report to compare actual trading results against setup family, final status, council verdict, Sugar Babies, and EP9M context.
