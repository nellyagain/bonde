# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 4850
- SLINGSHOT signal rows: 808
- Active `setup_family=SLINGSHOT` rows: 642
- Precedence-absorbed SLINGSHOT signal rows: 166

## Gate-observation counts
- Range-break true: 333 / 808
- Contraction quality ≥ 50: 367 / 808
- Volume ratio ≥ 1.2x: 309 / 808
- `custom_rs_rating` ≥ 70: 515 / 808
- R:R ≥ 2: 250 / 808
- > 8% above 21EMA: 267 / 808
- Resolved outcomes available: 0 / 808

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
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |
| AVA      | 2026-05-22    | SLINGSHOT      | True             |                  70.9952 |          0.65771  |                    35 |                1.26276  |        1.6555 |      1.34783  | False                 |             nan |
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
| DAO      | 2026-05-22    | ACTIVE_BURST   | True             |                  67.8078 |          3.61445  |                    76 |               10.2017   |       24.4267 |      0.600018 | False                 |             nan |
| DAO      | 2026-05-22    | SLINGSHOT      | True             |                  67.8078 |          3.61445  |                    76 |               10.2017   |       24.4267 |      0.600018 | False                 |             nan |
| NSC      | 2026-05-14    | SLINGSHOT      | True             |                  67.7412 |          0.471863 |                    59 |                2.35073  |      nan      |    nan        | False                 |             nan |
| ESS      | 2026-05-19    | SLINGSHOT      | True             |                  67.6196 |          0.742452 |                    38 |                2.96872  |        1.3087 |      2.7535   | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      129 |            0 |              nan |        nan |            -1.66 |              24.8 |          44.4 |                34.9 |                         0   |
| contraction_quality | 40-50    |      176 |            0 |              nan |        nan |            -1.92 |              34.7 |          41.6 |                34.7 |                         0   |
| contraction_quality | 50-60    |      222 |            0 |              nan |        nan |            -1.08 |              50.9 |          35.1 |                43.2 |                       100   |
| contraction_quality | <30      |      136 |            0 |              nan |        nan |            -3.2  |              33.8 |          50   |                44.9 |                         0   |
| contraction_quality | >=60     |      145 |            0 |              nan |        nan |            -0.7  |              55.9 |          32.2 |                31.7 |                       100   |
| volume_ratio        | 0.8-1.0x |      138 |            0 |              nan |        nan |            -1.36 |              31.2 |          43.9 |                 0   |                        42.8 |
| volume_ratio        | 1.0-1.2x |       83 |            0 |              nan |        nan |            -0.44 |              28.9 |          48.5 |                 0   |                        38.6 |
| volume_ratio        | <0.8x    |      278 |            0 |              nan |        nan |            -1.8  |              25.5 |          40.2 |                 0   |                        48.2 |
| volume_ratio        | >=1.2x   |      309 |            0 |              nan |        nan |            -2.17 |              63.1 |          34.1 |               100   |                        46   |
| distance_from_21ema | 3-5%     |       97 |            0 |              nan |        nan |            -1.61 |              35.1 |          36.4 |                24.7 |                        51.5 |
| distance_from_21ema | 5-8%     |      105 |            0 |              nan |        nan |            -0.17 |              49.5 |          46.3 |                44.8 |                        41.9 |
| distance_from_21ema | 8-12%    |      110 |            0 |              nan |        nan |            -3.74 |              54.5 |          54.3 |                57.3 |                        50   |
| distance_from_21ema | <=3%     |      339 |            0 |              nan |        nan |             0.68 |              21.2 |          35.2 |                16.2 |                        48.4 |
| distance_from_21ema | >12%     |      157 |            0 |              nan |        nan |            -3.73 |              73.2 |          41.7 |                76.4 |                        34.4 |
| risk_pct            | 3-5%     |      190 |            0 |              nan |        nan |             0.74 |              27.9 |          30.5 |                17.4 |                        48.9 |
| risk_pct            | 5-8%     |      130 |            0 |              nan |        nan |           nan    |              31.5 |          46.2 |                41.5 |                        29.2 |
| risk_pct            | 8-12%    |       75 |            0 |              nan |        nan |            -3.68 |              56   |          40   |                64   |                        33.3 |
| risk_pct            | <=3%     |      181 |            0 |              nan |        nan |            -0.51 |              30.9 |          46.4 |                13.3 |                        61.3 |
| risk_pct            | >12%     |       53 |            0 |              nan |        nan |             2.48 |              73.6 |          34   |                86.8 |                        52.8 |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -2.03 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      475 |            0 |              nan |        nan |            -0.13 |               0   |          46.2 |                24   |                        36.4 |
| range_break         | TRUE     |      333 |            0 |              nan |        nan |            -3.25 |             100   |          28.6 |                58.6 |                        58.3 |
| custom_rs_rating    | 50-70    |      184 |            0 |              nan |        nan |            -0.15 |              33.7 |          30.3 |                26.1 |                        51.1 |
| custom_rs_rating    | 70-90    |      288 |            0 |              nan |        nan |            -2.19 |              45.1 |          43.1 |                43.4 |                        40.3 |
| custom_rs_rating    | <50      |      107 |            0 |              nan |        nan |            -0.68 |              29.9 |          27.7 |                13.1 |                        48.6 |
| custom_rs_rating    | >=90     |      227 |            0 |              nan |        nan |            -2.29 |              47.1 |          51.1 |                52.9 |                        45.4 |
| custom_rs_rating    | MISSING  |        2 |            0 |              nan |        nan |           nan    |             100   |           0   |               100   |                       100   |
| rr_pass             | FALSE    |      379 |            0 |              nan |        nan |             0.57 |              43.5 |           0   |                35.6 |                        51.5 |
| rr_pass             | MISSING  |      179 |            0 |              nan |        nan |            -2.03 |              57   |         nan   |                58.1 |                        40.2 |
| rr_pass             | TRUE     |      250 |            0 |              nan |        nan |            -1.27 |              26.4 |         100   |                28   |                        40   |
| vol_gate            | FALSE    |      499 |            0 |              nan |        nan |            -1.34 |              27.7 |          42.5 |                 0   |                        45.1 |
| vol_gate            | TRUE     |      309 |            0 |              nan |        nan |            -2.17 |              63.1 |          34.1 |               100   |                        46   |
| contraction_gate    | FALSE    |      441 |            0 |              nan |        nan |            -2.32 |              31.5 |          44.9 |                37.9 |                         0   |
| contraction_gate    | TRUE     |      367 |            0 |              nan |        nan |            -0.94 |              52.9 |          33.9 |                38.7 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
