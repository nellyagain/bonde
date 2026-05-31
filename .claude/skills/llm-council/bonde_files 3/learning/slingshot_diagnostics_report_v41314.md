# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 5935
- SLINGSHOT signal rows: 1068
- Active `setup_family=SLINGSHOT` rows: 838
- Precedence-absorbed SLINGSHOT signal rows: 230

## Gate-observation counts
- Range-break true: 448 / 1068
- Contraction quality ≥ 50: 505 / 1068
- Volume ratio ≥ 1.2x: 427 / 1068
- `custom_rs_rating` ≥ 70: 703 / 1068
- R:R ≥ 2: 342 / 1068
- > 8% above 21EMA: 328 / 1068
- Resolved outcomes available: 0 / 1068

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
| NLCP     | 2026-05-26    | SLINGSHOT      | True             |                  75.6705 |          4.1058   |                    39 |                4.76783  |        7.5364 |      2        | False                 |             nan |
| MRK      | 2026-05-19    | SLINGSHOT      | True             |                  75.6409 |          0.561273 |                    67 |                0.819765 |        2.5804 |      0.70707  | False                 |             nan |
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |    nan        | False                 |             nan |
| SPHR     | 2026-05-29    | SLINGSHOT      | True             |                  74.7683 |          0.751612 |                    93 |                3.62376  |        5.0354 |      0.848747 | False                 |             nan |
| CDP      | 2026-05-21    | SLINGSHOT      | True             |                  74.5696 |          1.33224  |                    46 |                1.75993  |        3.478  |      0.575217 | False                 |             nan |
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| CWAN     | 2026-05-27    | SLINGSHOT      | True             |                  73.4129 |          0.25184  |                    44 |                0.530445 |        0.2866 |      1.57144  | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| ACEL     | 2026-05-27    | SLINGSHOT      | True             |                  72.3597 |          0.966458 |                    46 |                1.71376  |        2.9046 |      0.971428 | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | True             |                  71.881  |          0.708931 |                    42 |                2.88983  |        1.3304 |      1.16456  | False                 |             nan |
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |
| AVA      | 2026-05-22    | SLINGSHOT      | True             |                  70.9952 |          0.65771  |                    35 |                1.26276  |        1.6555 |      1.34783  | False                 |             nan |
| WBD      | 2026-05-20    | SLINGSHOT      | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| WBD      | 2026-05-20    | EP9M           | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| IFS      | 2026-05-19    | SLINGSHOT      | True             |                  70.9804 |          1.60272  |                    58 |                2.11166  |        4.0291 |      0.644563 | False                 |             nan |
| GTY      | 2026-05-20    | SLINGSHOT      | True             |                  70.7307 |          1.22781  |                    53 |                1.70789  |        2.9447 |      0.412055 | False                 |             nan |
| STRA     | 2026-05-18    | SLINGSHOT      | True             |                  70.6048 |          0.838977 |                    31 |                2.23565  |        4.3761 |      1.10112  | False                 |             nan |
| CYTK     | 2026-05-20    | SLINGSHOT      | True             |                  69.9326 |          0.911393 |                    89 |                8.6242   |        3.5642 |      1.97163  | False                 |             nan |
| KALV     | 2026-05-29    | SLINGSHOT      | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| KALV     | 2026-05-29    | PAUSE          | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| KALV     | 2026-05-29    | ANTICIPATION   | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| H        | 2026-05-20    | SLINGSHOT      | True             |                  69.6637 |          0.886654 |                    59 |                4.42163  |        6.0897 |      0.75127  | False                 |             nan |
| SEPN     | 2026-05-14    | SLINGSHOT      | True             |                  69.5089 |          1.80142  |                    89 |               13.951    |      nan      |    nan        | False                 |             nan |
| XIFR     | 2026-05-29    | ACTIVE_BURST   | True             |                  69.3263 |          1.45953  |                    73 |                9.17813  |        6.52   |      0.319018 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      157 |            0 |              nan |        nan |             3.66 |              25.5 |          45.7 |                37.6 |                         0   |
| contraction_quality | 40-50    |      220 |            0 |              nan |        nan |             1.66 |              35   |          39.8 |                36.4 |                         0   |
| contraction_quality | 50-60    |      303 |            0 |              nan |        nan |             2.49 |              51.2 |          33.7 |                43.9 |                       100   |
| contraction_quality | <30      |      186 |            0 |              nan |        nan |             0.31 |              28   |          47.3 |                45.7 |                         0   |
| contraction_quality | >=60     |      202 |            0 |              nan |        nan |             0.88 |              61.4 |          31.5 |                34.7 |                       100   |
| volume_ratio        | 0.8-1.0x |      180 |            0 |              nan |        nan |             2.76 |              31.7 |          39.7 |                 0   |                        46.1 |
| volume_ratio        | 1.0-1.2x |      111 |            0 |              nan |        nan |             4.1  |              30.6 |          43.6 |                 0   |                        40.5 |
| volume_ratio        | <0.8x    |      350 |            0 |              nan |        nan |             1.31 |              27.7 |          40.5 |                 0   |                        49.7 |
| volume_ratio        | >=1.2x   |      427 |            0 |              nan |        nan |             1.31 |              60.9 |          34.4 |               100   |                        47.5 |
| distance_from_21ema | 3-5%     |      155 |            0 |              nan |        nan |             0.41 |              36.8 |          30.4 |                26.5 |                        52.3 |
| distance_from_21ema | 5-8%     |      151 |            0 |              nan |        nan |             0.57 |              51.7 |          40.7 |                49   |                        47   |
| distance_from_21ema | 8-12%    |      136 |            0 |              nan |        nan |             0.02 |              51.5 |          43.8 |                62.5 |                        50   |
| distance_from_21ema | <=3%     |      434 |            0 |              nan |        nan |             1.93 |              22.6 |          36.3 |                18   |                        48.4 |
| distance_from_21ema | >12%     |      192 |            0 |              nan |        nan |             4.57 |              75.5 |          46.9 |                77.6 |                        39.1 |
| risk_pct            | 3-5%     |      253 |            0 |              nan |        nan |             2.28 |              28.1 |          31.6 |                22.1 |                        50.6 |
| risk_pct            | 5-8%     |      190 |            0 |              nan |        nan |             4.6  |              37.9 |          39.5 |                50   |                        36.8 |
| risk_pct            | 8-12%    |      111 |            0 |              nan |        nan |             7.36 |              54.1 |          36.9 |                68.5 |                        36.9 |
| risk_pct            | <=3%     |      272 |            0 |              nan |        nan |             0.52 |              35.3 |          44.9 |                14.7 |                        59.9 |
| risk_pct            | >12%     |       63 |            0 |              nan |        nan |             5.56 |              74.6 |          38.1 |                88.9 |                        49.2 |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -2.02 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      620 |            0 |              nan |        nan |             2.12 |               0   |          42.5 |                26.9 |                        36.5 |
| range_break         | TRUE     |      448 |            0 |              nan |        nan |             1.46 |             100   |          32.1 |                58   |                        62.3 |
| custom_rs_rating    | 50-70    |      226 |            0 |              nan |        nan |             1.32 |              35.8 |          31.5 |                27   |                        52.7 |
| custom_rs_rating    | 70-90    |      412 |            0 |              nan |        nan |             1.01 |              43.9 |          41.2 |                44.4 |                        44.9 |
| custom_rs_rating    | <50      |      136 |            0 |              nan |        nan |             0.98 |              34.6 |          25.2 |                16.2 |                        51.5 |
| custom_rs_rating    | >=90     |      291 |            0 |              nan |        nan |             3.82 |              46.7 |          47.5 |                54.3 |                        44.3 |
| custom_rs_rating    | MISSING  |        3 |            0 |              nan |        nan |             3.29 |             100   |          33.3 |               100   |                        66.7 |
| rr_pass             | FALSE    |      547 |            0 |              nan |        nan |             3.29 |              43   |           0   |                38.8 |                        53.2 |
| rr_pass             | MISSING  |      179 |            0 |              nan |        nan |            -2.02 |              57   |         nan   |                58.1 |                        40.2 |
| rr_pass             | TRUE     |      342 |            0 |              nan |        nan |             2.77 |              32.5 |         100   |                32.5 |                        41.5 |
| vol_gate            | FALSE    |      641 |            0 |              nan |        nan |             2.19 |              29.3 |          40.8 |                 0   |                        47.1 |
| vol_gate            | TRUE     |      427 |            0 |              nan |        nan |             1.31 |              60.9 |          34.4 |               100   |                        47.5 |
| contraction_gate    | FALSE    |      563 |            0 |              nan |        nan |             1.84 |              30   |          43.9 |                39.8 |                         0   |
| contraction_gate    | TRUE     |      505 |            0 |              nan |        nan |             1.86 |              55.2 |          32.8 |                40.2 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
