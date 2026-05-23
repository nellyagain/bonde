# Broker Export Normalization Audit — 2026-05-23

Parser version: **v4.13.34**

## Source hygiene
- Broker source scan is limited to `bonde_learning/_inbox/` only.
- Stale generated broker CSVs removed before this run: **0**

No broker files found in `_inbox/`.

## Normalization result
- Raw execution fills parsed: **0**
- Aggregated normalized rows: **0**
- Closed realized rows: **0**
- Open-position rows excluded from realized P&L: **0**
- Closed realized net P&L: **0.00**
- Rows with realized R computed: **0**

## Notes
- IBKR `Trades,Data,Trade` rows are parsed; `Order`, `ClosedLot`, `SubTotal`, and `Total` rows are ignored to avoid double-counting.
- Rows with IBKR code `O` are open-position rows and are excluded from realized P&L.
- Rows with IBKR code `C` are closed realized rows and are included in realized P&L.
- Match confidence: 0–3 days + unique + non-UNKNOWN family = BONDE_MATCHED/HIGH; 4–10 days or weak family context = AMBIGUOUS_MATCH.
- Realized R uses decision-log `trigger_price` and `invalidation_price` when both are available; otherwise P&L remains valid but R is unavailable.