# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 35
- SLINGSHOT signal rows: 23
- Active `setup_family=SLINGSHOT` rows: 23
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 0 / 23
- Contraction quality ≥ 50: 0 / 23
- Volume ratio ≥ 1.2x: 0 / 23
- `custom_rs_rating` ≥ 70: 0 / 23
- R:R ≥ 2: 0 / 23
- > 8% above 21EMA: 0 / 23
- Resolved outcomes available: 0 / 23

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
| ACLX     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| APA      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CB       | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CRGY     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| GTEN     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| HESM     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| HP       | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| KW       | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LYB      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MET      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MPC      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ODFL     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| OVV      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| PR       | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| PSX      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| RNGR     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| SPIR     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| STRZ     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| TALK     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| TALO     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| UNF      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| VLO      | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| VNOM     | 2026-05-15    | SLINGSHOT      | slingshot       | <NA>             |                      nan |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| volume_ratio        | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| distance_from_21ema | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| risk_pct            | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| range_break         | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| custom_rs_rating    | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| rr_pass             | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| vol_gate            | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |
| contraction_gate    | MISSING  |       23 |            0 |              nan |        nan |              nan |               nan |           nan |                 nan |                         nan |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
