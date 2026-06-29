# Broker Export Normalization Audit — 2026-06-29

Parser version: **v4.13.34**

## Source hygiene
- Broker source scan is limited to `bonde_learning/_inbox/` only.
- Stale generated broker CSVs removed before this run: **0**

## Source files scanned
| file                                                                    |   rows_loaded | status   |
|:------------------------------------------------------------------------|--------------:|:---------|
| /content/drive/MyDrive/bonde_learning/_inbox/ibkr_trades_2026-05-16.csv |            10 | LOADED   |
| /content/drive/MyDrive/bonde_learning/_inbox/ibkr_trades_2026-05-18.csv |             2 | LOADED   |

## Normalization result
- Raw execution fills parsed: **12**
- Aggregated normalized rows: **6**
- Closed realized rows: **2**
- Open-position rows excluded from realized P&L: **4**
- Closed realized net P&L: **237.92**
- Rows with realized R computed: **1**

## Normalized trade rows
| ticker   | trade_date   | trade_state     | side   |   abs_quantity |   avg_trade_price |   net_pnl | match_status    | join_confidence   |   match_days_diff | setup_family   | action_label   | final_trade_status   |   planned_entry_price |   stop_price |   planned_risk_amount |   realized_r | risk_status                   | join_notes                                                                                     |
|:---------|:-------------|:----------------|:-------|---------------:|------------------:|----------:|:----------------|:------------------|------------------:|:---------------|:---------------|:---------------------|----------------------:|-------------:|----------------------:|-------------:|:------------------------------|:-----------------------------------------------------------------------------------------------|
| ARMK     | 2026-05-15   | CLOSED_REALIZED | SELL   |            150 |           52.64   |  218.446  | BONDE_MATCHED   | HIGH              |                 3 | EP_ACTIVE      | B              | WATCH                |                 48.45 |        47.73 |                 108   |      2.02265 | R_AVAILABLE_FROM_DECISION_LOG | matched on ticker + nearest prior signal_date; days_diff=3; candidate_count=1; min_days_ties=1 |
| FIVN     | 2026-05-15   | CLOSED_REALIZED | SELL   |            350 |           21.4025 |   19.4723 | NON_BONDE       | NONE              |               nan | nan            | nan            | nan                  |                nan    |       nan    |                 nan   |    nan       | PNL_ONLY_MISSING_RISK         | No decision-log row for ticker within 10 calendar days before trade date.                      |
| FTI      | 2026-05-18   | OPEN_POSITION   | BUY    |            100 |           73.805  |    0      | NON_BONDE       | NONE              |               nan | nan            | nan            | nan                  |                nan    |       nan    |                 nan   |    nan       | OPEN_POSITION_NOT_REALIZED    | No decision-log row for ticker within 10 calendar days before trade date.                      |
| PRMB     | 2026-05-18   | OPEN_POSITION   | BUY    |            300 |           23.425  |    0      | NON_BONDE       | NONE              |               nan | nan            | nan            | nan                  |                nan    |       nan    |                 nan   |    nan       | OPEN_POSITION_NOT_REALIZED    | No decision-log row for ticker within 10 calendar days before trade date.                      |
| TWLO     | 2026-05-15   | OPEN_POSITION   | BUY    |             40 |          198.955  |    0      | BONDE_MATCHED   | HIGH              |                 0 | DELAYED_EP     | B              | WATCH                |                203.71 |       193    |                 428.4 |    nan       | OPEN_POSITION_NOT_REALIZED    | matched on ticker + nearest prior signal_date; days_diff=0; candidate_count=1; min_days_ties=1 |
| WERN     | 2026-05-15   | OPEN_POSITION   | BUY    |            200 |           37.25   |    0      | AMBIGUOUS_MATCH | LOW               |                 9 | UNKNOWN        | B              | WATCH                |                 38.46 |        35.03 |                 686   |    nan       | OPEN_POSITION_NOT_REALIZED    | matched on ticker + nearest prior signal_date; days_diff=9; candidate_count=1; min_days_ties=1 |

## Notes
- IBKR `Trades,Data,Trade` rows are parsed; `Order`, `ClosedLot`, `SubTotal`, and `Total` rows are ignored to avoid double-counting.
- Rows with IBKR code `O` are open-position rows and are excluded from realized P&L.
- Rows with IBKR code `C` are closed realized rows and are included in realized P&L.
- Match confidence: 0–3 days + unique + non-UNKNOWN family = BONDE_MATCHED/HIGH; 4–10 days or weak family context = AMBIGUOUS_MATCH.
- Realized R uses decision-log `trigger_price` and `invalidation_price` when both are available; otherwise P&L remains valid but R is unavailable.