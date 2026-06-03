# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 6747
- SLINGSHOT signal rows: 1311
- Active `setup_family=SLINGSHOT` rows: 1021
- Precedence-absorbed SLINGSHOT signal rows: 290

## Gate-observation counts
- Range-break true: 594 / 1311
- Contraction quality ≥ 50: 628 / 1311
- Volume ratio ≥ 1.2x: 542 / 1311
- `custom_rs_rating` ≥ 70: 873 / 1311
- R:R ≥ 2: 413 / 1311
- > 8% above 21EMA: 404 / 1311
- Resolved outcomes available: 0 / 1311

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
| ANDE     | 2026-06-01    | SLINGSHOT      | True             |                  76.662  |          0.722028 |                    81 |                0.910587 |        3.3917 |      1.254    | False                 |             nan |
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
| MSGE     | 2026-06-01    | SLINGSHOT      | True             |                  73.2617 |          1.47848  |                    82 |                6.11944  |        2.1766 |      1.6095   | False                 |             nan |
| ACEL     | 2026-05-27    | SLINGSHOT      | True             |                  72.3597 |          0.966458 |                    46 |                1.71376  |        2.9046 |      0.971428 | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | True             |                  71.881  |          0.708931 |                    42 |                2.88983  |        1.3304 |      1.16456  | False                 |             nan |
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |
| AVA      | 2026-05-22    | SLINGSHOT      | True             |                  70.9952 |          0.65771  |                    35 |                1.26276  |        1.6555 |      1.34783  | False                 |             nan |
| WBD      | 2026-05-20    | SLINGSHOT      | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| WBD      | 2026-05-20    | EP9M           | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| IFS      | 2026-05-19    | SLINGSHOT      | True             |                  70.9804 |          1.60272  |                    58 |                2.11166  |        4.0291 |      0.644563 | False                 |             nan |
| SNEX     | 2026-06-01    | SLINGSHOT      | True             |                  70.8804 |          0.997637 |                    88 |                3.84413  |        4.7901 |      0.9857   | False                 |             nan |
| GTY      | 2026-05-20    | SLINGSHOT      | True             |                  70.7307 |          1.22781  |                    53 |                1.70789  |        2.9447 |      0.412055 | False                 |             nan |
| STRA     | 2026-05-18    | SLINGSHOT      | True             |                  70.6048 |          0.838977 |                    31 |                2.23565  |        4.3761 |      1.10112  | False                 |             nan |
| CYTK     | 2026-05-20    | SLINGSHOT      | True             |                  69.9326 |          0.911393 |                    89 |                8.6242   |        3.5642 |      1.97163  | False                 |             nan |
| KALV     | 2026-05-29    | SLINGSHOT      | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| KALV     | 2026-05-29    | PAUSE          | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| KALV     | 2026-05-29    | ANTICIPATION   | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      179 |            0 |              nan |        nan |             3.43 |              29.1 |          45.9 |                38   |                         0   |
| contraction_quality | 40-50    |      288 |            0 |              nan |        nan |             1.3  |              39.6 |          39.9 |                39.9 |                         0   |
| contraction_quality | 50-60    |      363 |            0 |              nan |        nan |             1.68 |              52.9 |          31.7 |                42.1 |                       100   |
| contraction_quality | <30      |      216 |            0 |              nan |        nan |             0.98 |              30.6 |          49.4 |                46.8 |                         0   |
| contraction_quality | >=60     |      265 |            0 |              nan |        nan |             0.65 |              64.2 |          26.1 |                39.6 |                       100   |
| volume_ratio        | 0.8-1.0x |      226 |            0 |              nan |        nan |             1.87 |              36.3 |          37.1 |                 0   |                        47.3 |
| volume_ratio        | 1.0-1.2x |      142 |            0 |              nan |        nan |             3.72 |              37.3 |          37.6 |                 0   |                        45.8 |
| volume_ratio        | <0.8x    |      401 |            0 |              nan |        nan |             1.3  |              29.7 |          41.1 |                 0   |                        49.4 |
| volume_ratio        | >=1.2x   |      542 |            0 |              nan |        nan |             1.05 |              62.7 |          33.3 |               100   |                        47.6 |
| distance_from_21ema | 3-5%     |      195 |            0 |              nan |        nan |             0.4  |              39   |          32   |                29.2 |                        49.7 |
| distance_from_21ema | 5-8%     |      190 |            0 |              nan |        nan |             1.38 |              53.7 |          39.5 |                49.5 |                        48.4 |
| distance_from_21ema | 8-12%    |      163 |            0 |              nan |        nan |             0.38 |              55.8 |          38.5 |                61.3 |                        47.2 |
| distance_from_21ema | <=3%     |      522 |            0 |              nan |        nan |             1.51 |              26.4 |          35.7 |                19.2 |                        50.8 |
| distance_from_21ema | >12%     |      241 |            0 |              nan |        nan |             3.49 |              77.6 |          42.6 |                79.3 |                        40.2 |
| risk_pct            | 3-5%     |      328 |            0 |              nan |        nan |             1.99 |              32.9 |          31.4 |                22.9 |                        50   |
| risk_pct            | 5-8%     |      241 |            0 |              nan |        nan |             4.34 |              45.6 |          38.4 |                51.9 |                        36.1 |
| risk_pct            | 8-12%    |      142 |            0 |              nan |        nan |             4.7  |              59.9 |          34.3 |                71.8 |                        39.4 |
| risk_pct            | <=3%     |      328 |            0 |              nan |        nan |             0.09 |              36.9 |          43.6 |                16.2 |                        60.1 |
| risk_pct            | >12%     |       93 |            0 |              nan |        nan |             4.17 |              73.1 |          34.1 |                89.2 |                        55.9 |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -2.02 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      717 |            0 |              nan |        nan |             1.91 |               0   |          44.8 |                28.2 |                        37.1 |
| range_break         | TRUE     |      594 |            0 |              nan |        nan |             1.06 |             100   |          26.5 |                57.2 |                        60.9 |
| custom_rs_rating    | 50-70    |      276 |            0 |              nan |        nan |             0.59 |              39.5 |          31.2 |                26.4 |                        53.3 |
| custom_rs_rating    | 70-90    |      487 |            0 |              nan |        nan |             1.43 |              45.2 |          39.9 |                44.1 |                        45.2 |
| custom_rs_rating    | <50      |      158 |            0 |              nan |        nan |             0.53 |              38   |          24.8 |                19.6 |                        53.2 |
| custom_rs_rating    | >=90     |      386 |            0 |              nan |        nan |             3    |              52.3 |          43.4 |                56.7 |                        45.3 |
| custom_rs_rating    | MISSING  |        4 |            0 |              nan |        nan |             3.29 |              75   |          50   |               100   |                        50   |
| rr_pass             | FALSE    |      702 |            0 |              nan |        nan |             2.17 |              49.7 |           0   |                40   |                        54.8 |
| rr_pass             | MISSING  |      196 |            0 |              nan |        nan |            -2.02 |              60.7 |         nan   |                61.7 |                        42.3 |
| rr_pass             | TRUE     |      413 |            0 |              nan |        nan |             2.66 |              30.5 |         100   |                33.9 |                        38.7 |
| vol_gate            | FALSE    |      769 |            0 |              nan |        nan |             1.89 |              33   |          39.3 |                 0   |                        48.1 |
| vol_gate            | TRUE     |      542 |            0 |              nan |        nan |             1.05 |              62.7 |          33.3 |               100   |                        47.6 |
| contraction_gate    | FALSE    |      683 |            0 |              nan |        nan |             1.8  |              34   |          44.4 |                41.6 |                         0   |
| contraction_gate    | TRUE     |      628 |            0 |              nan |        nan |             1.27 |              57.6 |          29.4 |                41.1 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
