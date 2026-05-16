# Broker Export Normalization Audit — 2026-05-16

Parser version: **v4.13.32**

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

## Normalized trade rows
| ticker   | trade_date   | trade_state     | side   |   abs_quantity |   avg_trade_price |   net_pnl | match_status   | setup_family   | action_label   | final_trade_status   | risk_status                | join_notes                                                                    |
|:---------|:-------------|:----------------|:-------|---------------:|------------------:|----------:|:---------------|:---------------|:---------------|:---------------------|:---------------------------|:------------------------------------------------------------------------------|
| ARMK     | 2026-05-15   | CLOSED_REALIZED | SELL   |            150 |           52.64   |  218.446  | BONDE_MATCHED  | EP_ACTIVE      | B              | WATCH                | PNL_ONLY_MISSING_RISK      | matched on ticker + nearest prior signal_date; days_diff=3; candidate_count=1 |
| FIVN     | 2026-05-15   | CLOSED_REALIZED | SELL   |            350 |           21.4025 |   19.4723 | NON_BONDE      | nan            | nan            | nan                  | PNL_ONLY_MISSING_RISK      | No decision-log row for ticker within 10 calendar days before trade date.     |
| TWLO     | 2026-05-15   | OPEN_POSITION   | BUY    |             40 |          198.955  |    0      | BONDE_MATCHED  | DELAYED_EP     | B              | WATCH                | OPEN_POSITION_NOT_REALIZED | matched on ticker + nearest prior signal_date; days_diff=0; candidate_count=1 |
| WERN     | 2026-05-15   | OPEN_POSITION   | BUY    |            200 |           37.25   |    0      | BONDE_MATCHED  | UNKNOWN        | B              | WATCH                | OPEN_POSITION_NOT_REALIZED | matched on ticker + nearest prior signal_date; days_diff=9; candidate_count=1 |

## Notes
- IBKR `Trades,Data,Trade` rows are parsed; `Order`, `ClosedLot`, `SubTotal`, and `Total` rows are ignored to avoid double-counting.
- Rows with IBKR code `O` are open-position rows and are excluded from realized P&L.
- Rows with IBKR code `C` are closed realized rows and are included in realized P&L.
- Realized R remains unavailable until planned risk/stop can be matched reliably; P&L remains valid.