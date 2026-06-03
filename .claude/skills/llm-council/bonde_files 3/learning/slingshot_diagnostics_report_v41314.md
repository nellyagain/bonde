# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 795
- SLINGSHOT signal rows: 95
- Active `setup_family=SLINGSHOT` rows: 95
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 27 / 95
- Contraction quality ≥ 50: 31 / 95
- Volume ratio ≥ 1.2x: 0 / 95
- `custom_rs_rating` ≥ 70: 0 / 95
- R:R ≥ 2: 3 / 95
- > 8% above 21EMA: 0 / 95
- Resolved outcomes available: 0 / 95

## Metric sources
- `sg_contraction_quality`: `slingshot_contraction_quality`
- `sg_volume_ratio`: `missing`
- `sg_custom_rs_rating`: `missing`
- `sg_quarterly_rs_score`: `missing`
- `sg_distance_21ema_pct`: `missing`
- `sg_distance_200sma_pct`: `missing`
- `sg_risk_pct`: `missing`
- `sg_today_pct`: `day1_move_pct`
- `sg_rr_value`: `planned_rr`
- `sg_range_break`: `slingshot_range_break_flag`
- `sg_ret_5d_pct`: `ret_5d_close_pct`
- `sg_ret_10d_pct`: `ret_10d_close_pct`
- `sg_mfe_5d_r`: `missing`
- `sg_mae_5d_r`: `missing`

## Row-level diagnostic sample
| ticker   | signal_date   | setup_family   | primary_setup   | sg_range_break   |   sg_contraction_quality |   sg_volume_ratio |   sg_custom_rs_rating |   sg_distance_21ema_pct |   sg_risk_pct |   sg_rr_value | sg_outcome_resolved   |   sg_realized_r |
|:---------|:--------------|:---------------|:----------------|:-----------------|-------------------------:|------------------:|----------------------:|------------------------:|--------------:|--------------:|:----------------------|----------------:|
| ANDE     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  76.662  |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MSGE     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  73.2617 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| SNEX     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  70.8804 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| TRIN     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  68.2382 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| NWS      | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  67.8992 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ABNB     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  67.7724 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ADM      | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  66.7223 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ALMU     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  64.3768 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| EWTX     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  63.7665 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CSCO     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  62.5705 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CNTA     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  61.6808 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CRML     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  60.3069 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| UTI      | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  58.327  |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| BK       | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  57.724  |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| C        | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  57.3448 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| GLXY     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  56.8824 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| SVCO     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  55.0941 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| RLYB     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  53.4786 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| NOVT     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  52.0556 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| SBLK     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  50.2442 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| ALOY     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  48.402  |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| SHIP     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  44.6097 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| WLY      | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  43.995  |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MP       | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  40.5131 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| SPXC     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  40.2593 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| KPTI     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  27.3395 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| CDNS     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | True             |                  24.2962 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| LINC     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | False            |                  71.4251 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MMI      | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | False            |                  69.5884 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |
| MATX     | 2026-06-01    | SLINGSHOT      | SLINGSHOT       | False            |                  67.2614 |               nan |                   nan |                     nan |           nan |           nan | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |        2 |            0 |              nan |        nan |           nan    |               0   |           nan |                 nan |                         0   |
| contraction_quality | 40-50    |       11 |            0 |              nan |        nan |           nan    |              45.5 |           100 |                 nan |                         0   |
| contraction_quality | 50-60    |       12 |            0 |              nan |        nan |           nan    |              66.7 |           nan |                 nan |                       100   |
| contraction_quality | <30      |       10 |            0 |              nan |        nan |           nan    |              20   |           100 |                 nan |                         0   |
| contraction_quality | >=60     |       19 |            0 |              nan |        nan |           nan    |              63.2 |           nan |                 nan |                       100   |
| contraction_quality | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |           nan |                 nan |                       nan   |
| volume_ratio        | MISSING  |       95 |            0 |              nan |        nan |            -2.44 |              50   |           100 |                 nan |                        57.4 |
| distance_from_21ema | MISSING  |       95 |            0 |              nan |        nan |            -2.44 |              50   |           100 |                 nan |                        57.4 |
| risk_pct            | MISSING  |       95 |            0 |              nan |        nan |            -2.44 |              50   |           100 |                 nan |                        57.4 |
| range_break         | FALSE    |       27 |            0 |              nan |        nan |           nan    |               0   |           100 |                 nan |                        40.7 |
| range_break         | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |           nan |                 nan |                       nan   |
| range_break         | TRUE     |       27 |            0 |              nan |        nan |           nan    |             100   |           nan |                 nan |                        74.1 |
| custom_rs_rating    | MISSING  |       95 |            0 |              nan |        nan |            -2.44 |              50   |           100 |                 nan |                        57.4 |
| rr_pass             | MISSING  |       92 |            0 |              nan |        nan |            -2.44 |              52.9 |           nan |                 nan |                        60.8 |
| rr_pass             | TRUE     |        3 |            0 |              nan |        nan |           nan    |               0   |           100 |                 nan |                         0   |
| vol_gate            | MISSING  |       95 |            0 |              nan |        nan |            -2.44 |              50   |           100 |                 nan |                        57.4 |
| contraction_gate    | FALSE    |       23 |            0 |              nan |        nan |           nan    |              30.4 |           100 |                 nan |                         0   |
| contraction_gate    | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |           nan |                 nan |                       nan   |
| contraction_gate    | TRUE     |       31 |            0 |              nan |        nan |           nan    |              64.5 |           nan |                 nan |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
