# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 738
- SLINGSHOT signal rows: 42
- Active `setup_family=SLINGSHOT` rows: 42
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 0 / 42
- Contraction quality ≥ 50: 0 / 42
- Volume ratio ≥ 1.2x: 0 / 42
- `custom_rs_rating` ≥ 70: 0 / 42
- R:R ≥ 2: 0 / 42
- > 8% above 21EMA: 0 / 42
- Resolved outcomes available: 0 / 42

## Metric sources
- `sg_contraction_quality`: `missing`
- `sg_volume_ratio`: `missing`
- `sg_custom_rs_rating`: `missing`
- `sg_quarterly_rs_score`: `missing`
- `sg_distance_21ema_pct`: `missing`
- `sg_distance_200sma_pct`: `missing`
- `sg_risk_pct`: `missing`
- `sg_today_pct`: `day1_move_pct`
- `sg_rr_value`: `missing`
- `sg_range_break`: `missing`
- `sg_ret_5d_pct`: `ret_5d_close_pct`
- `sg_ret_10d_pct`: `ret_10d_close_pct`
- `sg_mfe_5d_r`: `missing`
- `sg_mae_5d_r`: `missing`

## Row-level diagnostic sample
| ticker   | signal_date   | setup_family   | primary_setup   | sg_range_break   |   sg_contraction_quality |   sg_volume_ratio |   sg_custom_rs_rating |   sg_distance_21ema_pct |   sg_risk_pct |   sg_rr_value | sg_outcome_resolved   |   sg_realized_r |
|:---------|:--------------|:---------------|:----------------|:-----------------|-------------------------:|------------------:|----------------------:|------------------------:|--------------:|--------------:|:----------------------|----------------:|
| ACHC     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| AGX      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ALAB     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| AOSL     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ARM      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ATI      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| AVT      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CHD      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CORZ     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CW       | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| DY       | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ETON     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ETOR     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| FN       | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| GVA      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| HLX      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| INTT     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| IONS     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| KC       | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LFST     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LION     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LLYVA    | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LUMN     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LYV      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MRVL     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MS       | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MUSA     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| NBIS     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| NPKI     | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ORN      | 2026-05-13    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| volume_ratio        | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| distance_from_21ema | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| risk_pct            | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| range_break         | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| custom_rs_rating    | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| rr_pass             | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| vol_gate            | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |
| contraction_gate    | MISSING  |       42 |            0 |              nan |        nan |            -2.44 |               nan |           nan |                 nan |                         nan |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
