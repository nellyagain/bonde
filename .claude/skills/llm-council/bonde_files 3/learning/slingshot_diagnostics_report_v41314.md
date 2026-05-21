# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 4225
- SLINGSHOT signal rows: 585
- Active `setup_family=SLINGSHOT` rows: 472
- Precedence-absorbed SLINGSHOT signal rows: 113

## Gate-observation counts
- Range-break true: 252 / 585
- Contraction quality ≥ 50: 275 / 585
- Volume ratio ≥ 1.2x: 219 / 585
- `custom_rs_rating` ≥ 70: 349 / 585
- R:R ≥ 2: 144 / 585
- > 8% above 21EMA: 177 / 585
- Resolved outcomes available: 0 / 585

## Metric sources
- `sg_contraction_quality`: `slingshot_contraction_quality`
- `sg_volume_ratio`: `vol_ratio`
- `sg_custom_rs_rating`: `custom_rs_rating`
- `sg_quarterly_rs_score`: `quarterly_rs_score`
- `sg_distance_21ema_pct`: `distance_from_21ema_pct`
- `sg_distance_200sma_pct`: `computed_from_close_sma_200`
- `sg_risk_pct`: `risk_pct`
- `sg_today_pct`: `today_pct`
- `sg_rr_value`: `planned_rr`
- `sg_range_break`: `slingshot_range_break_flag`
- `sg_ret_5d_pct`: `ret_5d_close_pct`
- `sg_ret_10d_pct`: `ret_10d_close_pct`
- `sg_mfe_5d_r`: `missing`
- `sg_mae_5d_r`: `missing`

## Row-level diagnostic sample
| ticker   | signal_date   | setup_family   | sg_range_break   |   sg_contraction_quality |   sg_volume_ratio |   sg_custom_rs_rating |   sg_distance_21ema_pct |   sg_risk_pct |   sg_rr_value | sg_outcome_resolved   |   sg_realized_r |
|:---------|:--------------|:---------------|:-----------------|-------------------------:|------------------:|----------------------:|------------------------:|--------------:|--------------:|:----------------------|----------------:|
| UDR      | 2026-05-20    | SLINGSHOT      | True             |                  75.8082 |          0.709406 |                    27 |                3.04948  |        1.951  |      1.14864  | False                 |             nan |
| MRK      | 2026-05-19    | SLINGSHOT      | True             |                  75.6409 |          0.561273 |                    67 |                0.819765 |        2.5804 |      0.70707  | False                 |             nan |
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |    nan        | False                 |             nan |
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| WBD      | 2026-05-20    | SLINGSHOT      | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| WBD      | 2026-05-20    | EP9M           | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| IFS      | 2026-05-19    | SLINGSHOT      | True             |                  70.9804 |          1.60272  |                    58 |                2.11166  |        4.0291 |      0.644563 | False                 |             nan |
| GTY      | 2026-05-20    | SLINGSHOT      | True             |                  70.7307 |          1.22781  |                    53 |                1.70789  |        2.9447 |      0.412055 | False                 |             nan |
| STRA     | 2026-05-18    | SLINGSHOT      | True             |                  70.6048 |          0.838977 |                    31 |                2.23565  |        4.3761 |      1.10112  | False                 |             nan |
| CYTK     | 2026-05-20    | SLINGSHOT      | True             |                  69.9326 |          0.911393 |                    89 |                8.6242   |        3.5642 |      1.97163  | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| H        | 2026-05-20    | SLINGSHOT      | True             |                  69.6637 |          0.886654 |                    59 |                4.42163  |        6.0897 |      0.75127  | False                 |             nan |
| SEPN     | 2026-05-14    | SLINGSHOT      | True             |                  69.5089 |          1.80142  |                    89 |               13.951    |      nan      |    nan        | False                 |             nan |
| URI      | 2026-05-14    | SLINGSHOT      | True             |                  69.2132 |          0.651686 |                    69 |                6.61549  |      nan      |    nan        | False                 |             nan |
| ROIV     | 2026-05-20    | EP_ACTIVE      | True             |                  68.6911 |          3.09721  |                    92 |               11.8329   |       10.4978 |      2        | False                 |             nan |
| ROIV     | 2026-05-20    | SLINGSHOT      | True             |                  68.6911 |          3.09721  |                    92 |               11.8329   |       10.4978 |      2        | False                 |             nan |
| ROIV     | 2026-05-20    | EP9M           | True             |                  68.6911 |          3.09721  |                    92 |               11.8329   |       10.4978 |      2        | False                 |             nan |
| PEN      | 2026-05-18    | SLINGSHOT      | True             |                  68.164  |          0.735292 |                    48 |                0.276773 |        1.0935 |      0.219572 | False                 |             nan |
| PHVS     | 2026-05-13    | SLINGSHOT      | True             |                  68.0884 |          0.86167  |                    85 |               10.7527   |      nan      |    nan        | False                 |             nan |
| MASI     | 2026-05-18    | SLINGSHOT      | True             |                  68.0289 |          1.28137  |                    51 |                0.264313 |        0.3241 |      0.482755 | False                 |             nan |
| NSC      | 2026-05-14    | SLINGSHOT      | True             |                  67.7412 |          0.471863 |                    59 |                2.35073  |      nan      |    nan        | False                 |             nan |
| ESS      | 2026-05-19    | SLINGSHOT      | True             |                  67.6196 |          0.742452 |                    38 |                2.96872  |        1.3087 |      2.7535   | False                 |             nan |
| VEON     | 2026-05-13    | EP_ACTIVE      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| VEON     | 2026-05-13    | SLINGSHOT      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| LSCC     | 2026-05-20    | ACTIVE_BURST   | True             |                  67.2816 |          1.92463  |                    93 |               13.6104   |        8.8669 |      0.296146 | False                 |             nan |
| BFST     | 2026-05-20    | SLINGSHOT      | True             |                  66.3637 |          1.64918  |                    44 |                1.62336  |        3.3309 |      0.526883 | False                 |             nan |
| HIG      | 2026-05-18    | SLINGSHOT      | True             |                  66.1638 |          0.820699 |                    35 |                1.18642  |        2.5965 |      0.856546 | False                 |             nan |
| TYRA     | 2026-05-13    | SLINGSHOT      | True             |                  65.9616 |          0.566367 |                    94 |                3.16003  |      nan      |    nan        | False                 |             nan |
| AAT      | 2026-05-19    | SLINGSHOT      | True             |                  65.9091 |          0.575003 |                    53 |                2.46504  |        1.3634 |      2.20689  | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |       90 |            0 |              nan |        nan |            -3.38 |              24.4 |          41.7 |                30   |                         0   |
| contraction_quality | 40-50    |      119 |            0 |              nan |        nan |            -4.61 |              37.8 |          35   |                33.6 |                         0   |
| contraction_quality | 50-60    |      169 |            0 |              nan |        nan |            -3.32 |              52.7 |          35.5 |                46.7 |                       100   |
| contraction_quality | <30      |      101 |            0 |              nan |        nan |            -6.04 |              35.6 |          39.7 |                40.6 |                         0   |
| contraction_quality | >=60     |      106 |            0 |              nan |        nan |            -5.51 |              56.6 |          28   |                30.2 |                       100   |
| volume_ratio        | 0.8-1.0x |      108 |            0 |              nan |        nan |            -0.35 |              30.6 |          38.1 |                 0   |                        41.7 |
| volume_ratio        | 1.0-1.2x |       64 |            0 |              nan |        nan |            -4.82 |              32.8 |          46.8 |                 0   |                        35.9 |
| volume_ratio        | <0.8x    |      194 |            0 |              nan |        nan |            -1.48 |              27.8 |          33.8 |                 0   |                        49.5 |
| volume_ratio        | >=1.2x   |      219 |            0 |              nan |        nan |            -5.88 |              65.8 |          31.3 |               100   |                        50.7 |
| distance_from_21ema | 3-5%     |       70 |            0 |              nan |        nan |            -3.63 |              41.4 |          32   |                31.4 |                        62.9 |
| distance_from_21ema | 5-8%     |       72 |            0 |              nan |        nan |            -5.48 |              62.5 |          32.4 |                47.2 |                        47.2 |
| distance_from_21ema | 8-12%    |       74 |            0 |              nan |        nan |            -4.31 |              63.5 |          47.1 |                63.5 |                        48.6 |
| distance_from_21ema | <=3%     |      266 |            0 |              nan |        nan |             0.64 |              19.2 |          32.1 |                14.7 |                        46.6 |
| distance_from_21ema | >12%     |      103 |            0 |              nan |        nan |            -6.14 |              77.7 |          48.1 |                74.8 |                        35.9 |
| risk_pct            | 3-5%     |      135 |            0 |              nan |        nan |           nan    |              23.7 |          25.2 |                17   |                        48.9 |
| risk_pct            | 5-8%     |       72 |            0 |              nan |        nan |           nan    |              38.9 |          37.5 |                41.7 |                        37.5 |
| risk_pct            | 8-12%    |       34 |            0 |              nan |        nan |           nan    |              67.6 |          38.2 |                61.8 |                        26.5 |
| risk_pct            | <=3%     |      141 |            0 |              nan |        nan |           nan    |              32.6 |          44.7 |                13.5 |                        58.9 |
| risk_pct            | >12%     |       24 |            0 |              nan |        nan |           nan    |              87.5 |          29.2 |                91.7 |                        75   |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -4.58 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      333 |            0 |              nan |        nan |            -2.3  |               0   |          39.8 |                22.5 |                        37.8 |
| range_break         | TRUE     |      252 |            0 |              nan |        nan |            -6.1  |             100   |          28   |                57.1 |                        59.1 |
| custom_rs_rating    | 50-70    |      148 |            0 |              nan |        nan |            -2.31 |              33.8 |          25.2 |                23.6 |                        53.4 |
| custom_rs_rating    | 70-90    |      211 |            0 |              nan |        nan |            -5.91 |              46.4 |          40.2 |                44.1 |                        41.2 |
| custom_rs_rating    | <50      |       87 |            0 |              nan |        nan |            -3.98 |              29.9 |          27   |                12.6 |                        44.8 |
| custom_rs_rating    | >=90     |      138 |            0 |              nan |        nan |            -3.07 |              55.8 |          50.6 |                57.2 |                        50   |
| custom_rs_rating    | MISSING  |        1 |            0 |              nan |        nan |           nan    |             100   |           0   |               100   |                       100   |
| rr_pass             | FALSE    |      262 |            0 |              nan |        nan |           nan    |              41.2 |           0   |                30.2 |                        52.3 |
| rr_pass             | MISSING  |      179 |            0 |              nan |        nan |            -4.58 |              57   |         nan   |                58.1 |                        40.2 |
| rr_pass             | TRUE     |      144 |            0 |              nan |        nan |           nan    |              29.2 |         100   |                25   |                        45.8 |
| vol_gate            | FALSE    |      366 |            0 |              nan |        nan |            -2.36 |              29.5 |          37.1 |                 0   |                        44.8 |
| vol_gate            | TRUE     |      219 |            0 |              nan |        nan |            -5.88 |              65.8 |          31.3 |               100   |                        50.7 |
| contraction_gate    | FALSE    |      310 |            0 |              nan |        nan |            -4.88 |              33.2 |          38.4 |                34.8 |                         0   |
| contraction_gate    | TRUE     |      275 |            0 |              nan |        nan |            -3.94 |              54.2 |          32.5 |                40.4 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
