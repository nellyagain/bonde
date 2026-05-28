# Sugar Babies Overlay Report — 2026-05-28

_v4.13.3 additive context overlay. This is monitoring only, not rule evidence._

## Guardrail

**SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE.** Do not change trading rules from this section alone. Sugar Babies is a context overlay, not an automatic trade signal or gate.

## Data-quality diagnostics

| metric | value |
|---|---|
| `sugar_babies_file_used` | NONE |
| `sugar_babies_source_rows` | 0 |
| `sugar_babies_unique_tickers` | 0 |
| `ticker_rows_loaded` | 0 |
| `ticker_rows_matched` | 0 |
| `candidate_rows_loaded` | 0 |
| `candidate_rows_matched` | 0 |
| `decision_rows_loaded` | 888 |
| `decision_rows_matched` | 0 |
| `outputs_written` | /content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_outcomes_sugar_enriched_v410.csv |

- Search paths: `['/content/drive/MyDrive/bonde_screener_cache/sugar_babies', '/content/drive/MyDrive/bonde_screener_cache', '/content']`
- Files found: `[]`

## Summary

No Sugar Babies overlay rows available yet. Confirm `sugar_babies.csv` is visible to Colab and that outcome files exist.

## Reading rules

- `sugar_baby_flag=True` means the ticker appeared in the Sugar Babies CSV, not that it is automatically tradeable.
- Use this report to test whether Sugar Baby context improves A2/B+/setup-family outcomes over time.
- Missing future bars are excluded from T+N metrics, not treated as zero.
- Rule changes still require mature, repeated weekly cohort evidence.