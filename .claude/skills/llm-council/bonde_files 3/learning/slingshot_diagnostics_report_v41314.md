# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 4586
- SLINGSHOT signal rows: 737
- Active `setup_family=SLINGSHOT` rows: 589
- Precedence-absorbed SLINGSHOT signal rows: 148

## Gate-observation counts
- Range-break true: 305 / 737
- Contraction quality ≥ 50: 325 / 737
- Volume ratio ≥ 1.2x: 281 / 737
- `custom_rs_rating` ≥ 70: 465 / 737
- R:R ≥ 2: 215 / 737
- > 8% above 21EMA: 241 / 737
- Resolved outcomes available: 0 / 737

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
| CDP      | 2026-05-21    | SLINGSHOT      | True             |                  74.5696 |          1.33224  |                    46 |                1.75993  |        3.478  |      0.575217 | False                 |             nan |
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |
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
| EVR      | 2026-05-21    | SLINGSHOT      | True             |                  68.5177 |          0.441011 |                    75 |                3.54889  |        3.8675 |      1.53169  | False                 |             nan |
| PEN      | 2026-05-18    | SLINGSHOT      | True             |                  68.164  |          0.735292 |                    48 |                0.276773 |        1.0935 |      0.219572 | False                 |             nan |
| PHVS     | 2026-05-13    | SLINGSHOT      | True             |                  68.0884 |          0.86167  |                    85 |               10.7527   |      nan      |    nan        | False                 |             nan |
| MASI     | 2026-05-18    | SLINGSHOT      | True             |                  68.0289 |          1.28137  |                    51 |                0.264313 |        0.3241 |      0.482755 | False                 |             nan |
| NSC      | 2026-05-14    | SLINGSHOT      | True             |                  67.7412 |          0.471863 |                    59 |                2.35073  |      nan      |    nan        | False                 |             nan |
| ESS      | 2026-05-19    | SLINGSHOT      | True             |                  67.6196 |          0.742452 |                    38 |                2.96872  |        1.3087 |      2.7535   | False                 |             nan |
| VEON     | 2026-05-13    | EP_ACTIVE      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| VEON     | 2026-05-13    | SLINGSHOT      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| LSCC     | 2026-05-20    | ACTIVE_BURST   | True             |                  67.2816 |          1.92463  |                    93 |               13.6104   |        8.8669 |      0.296146 | False                 |             nan |
| BFST     | 2026-05-20    | SLINGSHOT      | True             |                  66.3637 |          1.64918  |                    44 |                1.62336  |        3.3309 |      0.526883 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      124 |            0 |              nan |        nan |            -1.75 |              25   |          44.7 |                36.3 |                         0   |
| contraction_quality | 40-50    |      162 |            0 |              nan |        nan |            -2.15 |              35.8 |          39.8 |                34   |                         0   |
| contraction_quality | 50-60    |      197 |            0 |              nan |        nan |            -1.12 |              50.3 |          35.6 |                44.2 |                       100   |
| contraction_quality | <30      |      126 |            0 |              nan |        nan |            -3.78 |              34.9 |          48.9 |                42.9 |                         0   |
| contraction_quality | >=60     |      128 |            0 |              nan |        nan |            -1.3  |              57   |          26.9 |                31.2 |                       100   |
| volume_ratio        | 0.8-1.0x |      127 |            0 |              nan |        nan |            -1.82 |              28.3 |          44.7 |                 0   |                        40.9 |
| volume_ratio        | 1.0-1.2x |       78 |            0 |              nan |        nan |            -0.3  |              28.2 |          50.8 |                 0   |                        35.9 |
| volume_ratio        | <0.8x    |      251 |            0 |              nan |        nan |            -2.13 |              25.1 |          38.7 |                 0   |                        47   |
| volume_ratio        | >=1.2x   |      281 |            0 |              nan |        nan |            -2.33 |              65.5 |          30.5 |               100   |                        45.2 |
| distance_from_21ema | 3-5%     |       89 |            0 |              nan |        nan |            -1.86 |              36   |          37.7 |                27   |                        52.8 |
| distance_from_21ema | 5-8%     |       91 |            0 |              nan |        nan |            -0.12 |              54.9 |          37.7 |                44   |                        41.8 |
| distance_from_21ema | 8-12%    |       96 |            0 |              nan |        nan |            -3.84 |              53.1 |          57.1 |                58.3 |                        46.9 |
| distance_from_21ema | <=3%     |      316 |            0 |              nan |        nan |             1.15 |              20.6 |          34.2 |                16.1 |                        47.2 |
| distance_from_21ema | >12%     |      145 |            0 |              nan |        nan |            -4.12 |              73.8 |          41.7 |                75.9 |                        31.7 |
| risk_pct            | 3-5%     |      170 |            0 |              nan |        nan |           nan    |              26.5 |          27.6 |                17.6 |                        48.8 |
| risk_pct            | 5-8%     |      118 |            0 |              nan |        nan |           nan    |              31.4 |          45.8 |                40.7 |                        28   |
| risk_pct            | 8-12%    |       61 |            0 |              nan |        nan |           nan    |              55.7 |          39.3 |                60.7 |                        31.1 |
| risk_pct            | <=3%     |      162 |            0 |              nan |        nan |           nan    |              32.1 |          45.7 |                13.6 |                        59.3 |
| risk_pct            | >12%     |       47 |            0 |              nan |        nan |           nan    |              74.5 |          34   |                85.1 |                        46.8 |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -2.03 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      432 |            0 |              nan |        nan |            -0.08 |               0   |          45.6 |                22.5 |                        35.4 |
| range_break         | TRUE     |      305 |            0 |              nan |        nan |            -3.52 |             100   |          26.1 |                60.3 |                        56.4 |
| custom_rs_rating    | 50-70    |      172 |            0 |              nan |        nan |            -0.16 |              34.3 |          27.3 |                24.4 |                        51.7 |
| custom_rs_rating    | 70-90    |      264 |            0 |              nan |        nan |            -2.4  |              44.3 |          41.1 |                43.2 |                        39   |
| custom_rs_rating    | <50      |       98 |            0 |              nan |        nan |            -1.34 |              29.6 |          28.2 |                14.3 |                        46.9 |
| custom_rs_rating    | >=90     |      201 |            0 |              nan |        nan |            -2.62 |              48.8 |          52.7 |                54.2 |                        42.3 |
| custom_rs_rating    | MISSING  |        2 |            0 |              nan |        nan |           nan    |             100   |           0   |               100   |                       100   |
| rr_pass             | FALSE    |      343 |            0 |              nan |        nan |           nan    |              43.7 |           0   |                35.9 |                        50.1 |
| rr_pass             | MISSING  |      179 |            0 |              nan |        nan |            -2.03 |              57   |         nan   |                58.1 |                        40.2 |
| rr_pass             | TRUE     |      215 |            0 |              nan |        nan |           nan    |              24.7 |         100   |                25.1 |                        37.7 |
| vol_gate            | FALSE    |      456 |            0 |              nan |        nan |            -1.61 |              26.5 |          42.3 |                 0   |                        43.4 |
| vol_gate            | TRUE     |      281 |            0 |              nan |        nan |            -2.33 |              65.5 |          30.5 |               100   |                        45.2 |
| contraction_gate    | FALSE    |      412 |            0 |              nan |        nan |            -2.61 |              32.3 |          43.9 |                37.4 |                         0   |
| contraction_gate    | TRUE     |      325 |            0 |              nan |        nan |            -1.18 |              52.9 |          32   |                39.1 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
