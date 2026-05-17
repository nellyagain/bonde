# Realized P&L Attribution — 2026-05-17

_Broker-export mode. Raw IBKR CSVs are normalized; open positions are separated from closed realized P&L. Stable latest CSVs replace prior generated broker files each run._

## Source files

## Overall
No closed realized broker rows found.

## Closed vs open handling
- Closed realized rows included in P&L: **0**
- Open-position rows excluded from realized P&L: **0**
- Closed realized net P&L: **0.00**
- Rows with realized R computed: **0**


## Interpretation rules
- This report excludes open-position rows from realized P&L.
- `R_AVAILABLE_FROM_DECISION_LOG` means realized R was computed from broker net P&L divided by planned risk from decision-log trigger/stop.
- `PNL_ONLY_MISSING_RISK` means P&L is usable but R-multiple is not yet computable.
- `NON_BONDE` rows are kept for account reconciliation but excluded from Bonde-only conclusions.
- `AMBIGUOUS_MATCH` rows should not be used as clean Bonde evidence unless manually confirmed.