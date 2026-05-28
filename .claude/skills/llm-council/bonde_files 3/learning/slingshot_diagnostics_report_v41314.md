# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 888
- SLINGSHOT signal rows: 170
- Active `setup_family=SLINGSHOT` rows: 170
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 45 / 170
- Contraction quality ≥ 50: 62 / 170
- Volume ratio ≥ 1.2x: 0 / 170
- `custom_rs_rating` ≥ 70: 0 / 170
- R:R ≥ 2: 52 / 170
- > 8% above 21EMA: 0 / 170
- Resolved outcomes available: 0 / 170

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
| NLCP     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  75.6705 |               nan |                   nan |                     nan |           nan |        2      | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  71.881  |               nan |                   nan |                     nan |           nan |        1.1646 | False                 |             nan |
| SEZL     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  69.0516 |               nan |                   nan |                     nan |           nan |        1.6054 | False                 |             nan |
| NPKI     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  68.937  |               nan |                   nan |                     nan |           nan |        1.1277 | False                 |             nan |
| TDAY     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  67.3307 |               nan |                   nan |                     nan |           nan |        2.2308 | False                 |             nan |
| ARI      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  67.2741 |               nan |                   nan |                     nan |           nan |        1.6875 | False                 |             nan |
| PRLB     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  66.8459 |               nan |                   nan |                     nan |           nan |        0.9672 | False                 |             nan |
| SYBT     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  66.1851 |               nan |                   nan |                     nan |           nan |        1.5161 | False                 |             nan |
| ESE      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  65.794  |               nan |                   nan |                     nan |           nan |        2.0361 | False                 |             nan |
| RDNW     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  65.6649 |               nan |                   nan |                     nan |           nan |        3.3333 | False                 |             nan |
| FBLA     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  65.3278 |               nan |                   nan |                     nan |           nan |        0.0986 | False                 |             nan |
| SENEA    | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  64.8781 |               nan |                   nan |                     nan |           nan |        1.6435 | False                 |             nan |
| ADAM     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  64.5808 |               nan |                   nan |                     nan |           nan |        0.8095 | False                 |             nan |
| BANC     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  63.7656 |               nan |                   nan |                     nan |           nan |        1.6452 | False                 |             nan |
| HCC      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  62.5886 |               nan |                   nan |                     nan |           nan |        2      | False                 |             nan |
| TTI      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  62.3543 |               nan |                   nan |                     nan |           nan |        0.7833 | False                 |             nan |
| SRRK     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  62.265  |               nan |                   nan |                     nan |           nan |        0.2859 | False                 |             nan |
| HR       | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  61.6665 |               nan |                   nan |                     nan |           nan |        2.4167 | False                 |             nan |
| NSC      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  61.5306 |               nan |                   nan |                     nan |           nan |        1.5898 | False                 |             nan |
| STT      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  59.8642 |               nan |                   nan |                     nan |           nan |        0.3191 | False                 |             nan |
| RSVR     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  57.7278 |               nan |                   nan |                     nan |           nan |        1.6207 | False                 |             nan |
| AS       | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  57.415  |               nan |                   nan |                     nan |           nan |        1.2981 | False                 |             nan |
| AMR      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  57.2667 |               nan |                   nan |                     nan |           nan |        0.3876 | False                 |             nan |
| BKU      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  55.7154 |               nan |                   nan |                     nan |           nan |        1.3253 | False                 |             nan |
| THR      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  55.3728 |               nan |                   nan |                     nan |           nan |        0.0337 | False                 |             nan |
| SHLS     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  55.2547 |               nan |                   nan |                     nan |           nan |        0.5177 | False                 |             nan |
| CECO     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  54.5901 |               nan |                   nan |                     nan |           nan |        0.1142 | False                 |             nan |
| ROG      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  54.3926 |               nan |                   nan |                     nan |           nan |        0.8304 | False                 |             nan |
| FTV      | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  54.2673 |               nan |                   nan |                     nan |           nan |        0.7749 | False                 |             nan |
| MSGS     | 2026-05-26    | SLINGSHOT      | slingshot       | True             |                  52.0541 |               nan |                   nan |                     nan |           nan |        0.7027 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |       17 |            0 |              nan |        nan |           nan    |              11.8 |          47.1 |                 nan |                         0   |
| contraction_quality | 40-50    |       24 |            0 |              nan |        nan |           nan    |              33.3 |          41.7 |                 nan |                         0   |
| contraction_quality | 50-60    |       35 |            0 |              nan |        nan |           nan    |              37.1 |          31.4 |                 nan |                       100   |
| contraction_quality | <30      |       26 |            0 |              nan |        nan |           nan    |              11.5 |          53.8 |                 nan |                         0   |
| contraction_quality | >=60     |       27 |            0 |              nan |        nan |           nan    |              70.4 |          33.3 |                 nan |                       100   |
| contraction_quality | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| volume_ratio        | MISSING  |      170 |            0 |              nan |        nan |            -2.44 |              34.9 |          40.3 |                 nan |                        48.1 |
| distance_from_21ema | MISSING  |      170 |            0 |              nan |        nan |            -2.44 |              34.9 |          40.3 |                 nan |                        48.1 |
| risk_pct            | MISSING  |      170 |            0 |              nan |        nan |            -2.44 |              34.9 |          40.3 |                 nan |                        48.1 |
| range_break         | FALSE    |       84 |            0 |              nan |        nan |           nan    |               0   |          42.9 |                 nan |                        35.7 |
| range_break         | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| range_break         | TRUE     |       45 |            0 |              nan |        nan |           nan    |             100   |          35.6 |                 nan |                        71.1 |
| custom_rs_rating    | MISSING  |      170 |            0 |              nan |        nan |            -2.44 |              34.9 |          40.3 |                 nan |                        48.1 |
| rr_pass             | FALSE    |       77 |            0 |              nan |        nan |           nan    |              37.7 |           0   |                 nan |                        54.5 |
| rr_pass             | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| rr_pass             | TRUE     |       52 |            0 |              nan |        nan |           nan    |              30.8 |         100   |                 nan |                        38.5 |
| vol_gate            | MISSING  |      170 |            0 |              nan |        nan |            -2.44 |              34.9 |          40.3 |                 nan |                        48.1 |
| contraction_gate    | FALSE    |       67 |            0 |              nan |        nan |           nan    |              19.4 |          47.8 |                 nan |                         0   |
| contraction_gate    | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| contraction_gate    | TRUE     |       62 |            0 |              nan |        nan |           nan    |              51.6 |          32.3 |                 nan |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
