# Realized P&L Attribution — 2026-05-16

_No broker/trade export file found._

Practical workflow: export raw IBKR/Broker trades as CSV and drop the file into:

```text
/content/drive/MyDrive/bonde_learning/_inbox/
```

Use a filename like:

```text
ibkr_trades_YYYY-MM-DD.csv
broker_trades_YYYY-MM-DD.csv
executions_YYYY-MM-DD.csv
```

Do not manually fill R. The notebook will try to infer signal date, stop/risk, and realized R from the decision log. If risk cannot be inferred, it will still keep net P&L and mark `risk_status = PNL_ONLY_MISSING_RISK`.

Fallback template, only if needed, written to:

```text
/content/drive/MyDrive/bonde_screener_cache/learning_outputs/realized_trades_template.csv
```
