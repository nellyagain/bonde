# Broker Export Normalization Audit — 2026-05-16

Parser version: **v4.13.34**

## Source hygiene
- Broker source scan is limited to `bonde_learning/_inbox/` only.
- Stale generated broker CSVs removed before this run: **17**
- Removed generated files include:
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/broker_export_normalized_trades_v41332.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/broker_export_normalized_trades_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_latest/bonde_files 3/learning/broker_export_normalized_trades_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_2026-05-16/bonde_files 3/learning/broker_export_normalized_trades_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_master_v41330.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_master_v41332.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_master_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_latest/bonde_files 3/learning/realized_trades_master_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_2026-05-16/bonde_files 3/learning/realized_trades_master_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_pnl_attribution_summary_v41330.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_pnl_attribution_summary_v41332.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_pnl_attribution_summary_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_latest/bonde_files 3/learning/realized_pnl_attribution_summary_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_2026-05-16/bonde_files 3/learning/realized_pnl_attribution_summary_v41331.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_template.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_latest/bonde_files 3/learning/realized_trades_template.csv`
  - `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/council_ready_bundle_2026-05-16/bonde_files 3/learning/realized_trades_template.csv`

## Source files scanned
| file                                                                    |   rows_loaded | status   |
|:------------------------------------------------------------------------|--------------:|:---------|
| /content/drive/MyDrive/bonde_learning/_inbox/ibkr_trades_2026-05-16.csv |            10 | LOADED   |

## Normalization result
- Raw execution fills parsed: **10**
- Aggregated normalized rows: **4**
- Closed realized rows: **2**
- Open-position rows excluded from realized P&L: **2**
- Closed realized net P&L: **237.92**
- Rows with realized R computed: **1**

## Normalized trade rows
| ticker   | trade_date   | trade_state     | side   |   abs_quantity |   avg_trade_price |   net_pnl | match_status    | join_confidence   |   match_days_diff | setup_family   | action_label   | final_trade_status   |   planned_entry_price |   stop_price |   planned_risk_amount |   realized_r | risk_status                   | join_notes                                                                                     |
|:---------|:-------------|:----------------|:-------|---------------:|------------------:|----------:|:----------------|:------------------|------------------:|:---------------|:---------------|:---------------------|----------------------:|-------------:|----------------------:|-------------:|:------------------------------|:-----------------------------------------------------------------------------------------------|
| ARMK     | 2026-05-15   | CLOSED_REALIZED | SELL   |            150 |           52.64   |  218.446  | BONDE_MATCHED   | HIGH              |                 3 | EP_ACTIVE      | B              | WATCH                |                 48.45 |        47.73 |                 108   |      2.02265 | R_AVAILABLE_FROM_DECISION_LOG | matched on ticker + nearest prior signal_date; days_diff=3; candidate_count=1; min_days_ties=1 |
| FIVN     | 2026-05-15   | CLOSED_REALIZED | SELL   |            350 |           21.4025 |   19.4723 | NON_BONDE       | NONE              |               nan | nan            | nan            | nan                  |                nan    |       nan    |                 nan   |    nan       | PNL_ONLY_MISSING_RISK         | No decision-log row for ticker within 10 calendar days before trade date.                      |
| TWLO     | 2026-05-15   | OPEN_POSITION   | BUY    |             40 |          198.955  |    0      | BONDE_MATCHED   | HIGH              |                 0 | DELAYED_EP     | B              | WATCH                |                203.71 |       193    |                 428.4 |    nan       | OPEN_POSITION_NOT_REALIZED    | matched on ticker + nearest prior signal_date; days_diff=0; candidate_count=1; min_days_ties=1 |
| WERN     | 2026-05-15   | OPEN_POSITION   | BUY    |            200 |           37.25   |    0      | AMBIGUOUS_MATCH | LOW               |                 9 | UNKNOWN        | B              | WATCH                |                 38.46 |        35.03 |                 686   |    nan       | OPEN_POSITION_NOT_REALIZED    | matched on ticker + nearest prior signal_date; days_diff=9; candidate_count=1; min_days_ties=1 |

## Notes
- IBKR `Trades,Data,Trade` rows are parsed; `Order`, `ClosedLot`, `SubTotal`, and `Total` rows are ignored to avoid double-counting.
- Rows with IBKR code `O` are open-position rows and are excluded from realized P&L.
- Rows with IBKR code `C` are closed realized rows and are included in realized P&L.
- Match confidence: 0–3 days + unique + non-UNKNOWN family = BONDE_MATCHED/HIGH; 4–10 days or weak family context = AMBIGUOUS_MATCH.
- Realized R uses decision-log `trigger_price` and `invalidation_price` when both are available; otherwise P&L remains valid but R is unavailable.