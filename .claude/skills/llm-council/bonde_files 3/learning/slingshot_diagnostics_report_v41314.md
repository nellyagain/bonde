# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 835
- SLINGSHOT signal rows: 71
- Active `setup_family=SLINGSHOT` rows: 71
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 14 / 71
- Contraction quality ≥ 50: 21 / 71
- Volume ratio ≥ 1.2x: 0 / 71
- `custom_rs_rating` ≥ 70: 0 / 71
- R:R ≥ 2: 6 / 71
- > 8% above 21EMA: 0 / 71
- Resolved outcomes available: 0 / 71

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
| CWAN     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  73.4129 |               nan |                   nan |                     nan |           nan |     1.57144   | False                 |             nan |
| ACEL     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  72.3597 |               nan |                   nan |                     nan |           nan |     0.971428  | False                 |             nan |
| CDNA     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  64.6619 |               nan |                   nan |                     nan |           nan |     2.18781   | False                 |             nan |
| ARRY     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  64.4128 |               nan |                   nan |                     nan |           nan |     0.489797  | False                 |             nan |
| WH       | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  57.1824 |               nan |                   nan |                     nan |           nan |     1.20556   | False                 |             nan |
| SAIA     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  57.1278 |               nan |                   nan |                     nan |           nan |     1.92503   | False                 |             nan |
| VMD      | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  56.2811 |               nan |                   nan |                     nan |           nan |     1.07408   | False                 |             nan |
| UMH      | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  54.5619 |               nan |                   nan |                     nan |           nan |     1.66668   | False                 |             nan |
| MAC      | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  54.4064 |               nan |                   nan |                     nan |           nan |     3.16666   | False                 |             nan |
| MSCI     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  51.1565 |               nan |                   nan |                     nan |           nan |     1.26702   | False                 |             nan |
| GLSI     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  50.0646 |               nan |                   nan |                     nan |           nan |     0.878907  | False                 |             nan |
| AGL      | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  47.2524 |               nan |                   nan |                     nan |           nan |     1.27345   | False                 |             nan |
| AVNS     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                  42.5629 |               nan |                   nan |                     nan |           nan |     3         | False                 |             nan |
| TACO     | 2026-05-27    | SLINGSHOT      | slingshot       | True             |                   0      |               nan |                   nan |                     nan |           nan |     5.19998   | False                 |             nan |
| KODK     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  62.121  |               nan |                   nan |                     nan |           nan |     0.583333  | False                 |             nan |
| PTGX     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  61.7227 |               nan |                   nan |                     nan |           nan |     2.16282   | False                 |             nan |
| PFGC     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  60.6729 |               nan |                   nan |                     nan |           nan |     1.36529   | False                 |             nan |
| BRSP     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  60.248  |               nan |                   nan |                     nan |           nan |     1.22222   | False                 |             nan |
| KRO      | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  59.1249 |               nan |                   nan |                     nan |           nan |     0.0888877 | False                 |             nan |
| XYZ      | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  58.8047 |               nan |                   nan |                     nan |           nan |     1.31176   | False                 |             nan |
| OPRA     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  55.3637 |               nan |                   nan |                     nan |           nan |     1.96154   | False                 |             nan |
| MGTX     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  54.7962 |               nan |                   nan |                     nan |           nan |     1.95652   | False                 |             nan |
| UNFI     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  53.1205 |               nan |                   nan |                     nan |           nan |     1.44813   | False                 |             nan |
| KYMR     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  51.7775 |               nan |                   nan |                     nan |           nan |     1.77949   | False                 |             nan |
| ALKS     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  45.9043 |               nan |                   nan |                     nan |           nan |     1.75581   | False                 |             nan |
| ONDS     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  30.4721 |               nan |                   nan |                     nan |           nan |     0.355072  | False                 |             nan |
| CC       | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  27.753  |               nan |                   nan |                     nan |           nan |     3.66666   | False                 |             nan |
| BA       | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  20.2688 |               nan |                   nan |                     nan |           nan |     0.829035  | False                 |             nan |
| LAR      | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  19.6614 |               nan |                   nan |                     nan |           nan |     1.24706   | False                 |             nan |
| VNET     | 2026-05-27    | SLINGSHOT      | slingshot       | False            |                  18.3958 |               nan |                   nan |                     nan |           nan |     1         | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |        1 |            0 |              nan |        nan |           nan    |               0   |           0   |                 nan |                         0   |
| contraction_quality | 40-50    |        3 |            0 |              nan |        nan |           nan    |              66.7 |          33.3 |                 nan |                         0   |
| contraction_quality | 50-60    |       13 |            0 |              nan |        nan |           nan    |              53.8 |           7.7 |                 nan |                       100   |
| contraction_quality | <30      |        5 |            0 |              nan |        nan |           nan    |              20   |          40   |                 nan |                         0   |
| contraction_quality | >=60     |        8 |            0 |              nan |        nan |           nan    |              50   |          25   |                 nan |                       100   |
| contraction_quality | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| volume_ratio        | MISSING  |       71 |            0 |              nan |        nan |            -2.44 |              46.7 |          20   |                 nan |                        70   |
| distance_from_21ema | MISSING  |       71 |            0 |              nan |        nan |            -2.44 |              46.7 |          20   |                 nan |                        70   |
| risk_pct            | MISSING  |       71 |            0 |              nan |        nan |            -2.44 |              46.7 |          20   |                 nan |                        70   |
| range_break         | FALSE    |       16 |            0 |              nan |        nan |           nan    |               0   |          12.5 |                 nan |                        62.5 |
| range_break         | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| range_break         | TRUE     |       14 |            0 |              nan |        nan |           nan    |             100   |          28.6 |                 nan |                        78.6 |
| custom_rs_rating    | MISSING  |       71 |            0 |              nan |        nan |            -2.44 |              46.7 |          20   |                 nan |                        70   |
| rr_pass             | FALSE    |       24 |            0 |              nan |        nan |           nan    |              41.7 |           0   |                 nan |                        75   |
| rr_pass             | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| rr_pass             | TRUE     |        6 |            0 |              nan |        nan |           nan    |              66.7 |         100   |                 nan |                        50   |
| vol_gate            | MISSING  |       71 |            0 |              nan |        nan |            -2.44 |              46.7 |          20   |                 nan |                        70   |
| contraction_gate    | FALSE    |        9 |            0 |              nan |        nan |           nan    |              33.3 |          33.3 |                 nan |                         0   |
| contraction_gate    | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| contraction_gate    | TRUE     |       21 |            0 |              nan |        nan |           nan    |              52.4 |          14.3 |                 nan |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
