# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 90
- SLINGSHOT signal rows: 73
- Active `setup_family=SLINGSHOT` rows: 73
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 0 / 73
- Contraction quality ≥ 50: 0 / 73
- Volume ratio ≥ 1.2x: 0 / 73
- `custom_rs_rating` ≥ 70: 0 / 73
- R:R ≥ 2: 0 / 73
- > 8% above 21EMA: 0 / 73
- Resolved outcomes available: 0 / 73

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
| ACEL     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| AHRT     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| AIG      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ALF      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| APLE     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ASH      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BCAL     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BKR      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BKSY     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BNL      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BRC      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BRX      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CFR      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CHCT     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CHRW     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CLMT     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CPAY     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CTO      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CWAN     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| D        | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| DEA      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| DRH      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| EFSC     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| EW       | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| FCPT     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| FIVE     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| GLRE     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| GNW      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| GPRK     | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| HIG      | 2026-05-18    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| volume_ratio        | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| distance_from_21ema | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| risk_pct            | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| range_break         | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| custom_rs_rating    | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| rr_pass             | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| vol_gate            | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| contraction_gate    | MISSING  |       73 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
