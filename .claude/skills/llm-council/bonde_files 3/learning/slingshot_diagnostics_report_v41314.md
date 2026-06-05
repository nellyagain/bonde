# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 7034
- SLINGSHOT signal rows: 1366
- Active `setup_family=SLINGSHOT` rows: 1067
- Precedence-absorbed SLINGSHOT signal rows: 299

## Gate-observation counts
- Range-break true: 621 / 1366
- Contraction quality ≥ 50: 656 / 1366
- Volume ratio ≥ 1.2x: 561 / 1366
- `custom_rs_rating` ≥ 70: 903 / 1366
- R:R ≥ 2: 431 / 1366
- > 8% above 21EMA: 415 / 1366
- Resolved outcomes available: 0 / 1366

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
| CCRN     | 2026-06-03    | SLINGSHOT      | True             |                  78.7182 |          0.42593  |                    65 |                4.15578  |        0.457  |      1.1667   | False                 |             nan |
| CCRN     | 2026-06-03    | PAUSE          | True             |                  78.7182 |          0.42593  |                    65 |                4.15578  |        0.457  |      1.1667   | False                 |             nan |
| CCRN     | 2026-06-03    | ANTICIPATION   | True             |                  78.7182 |          0.42593  |                    65 |                4.15578  |        0.457  |      1.1667   | False                 |             nan |
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
| MRNA     | 2026-06-03    | SLINGSHOT      | True             |                  69.943  |          1.05995  |                    83 |                1.83834  |        8.5772 |      1.1929   | False                 |             nan |
| CYTK     | 2026-05-20    | SLINGSHOT      | True             |                  69.9326 |          0.911393 |                    89 |                8.6242   |        3.5642 |      1.97163  | False                 |             nan |
| KALV     | 2026-05-29    | SLINGSHOT      | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      190 |            0 |              nan |        nan |             3.48 |              30.5 |          46.8 |                36.8 |                         0   |
| contraction_quality | 40-50    |      295 |            0 |              nan |        nan |             1.3  |              39   |          40   |                39   |                         0   |
| contraction_quality | 50-60    |      377 |            0 |              nan |        nan |             1.32 |              53.1 |          31.6 |                41.9 |                       100   |
| contraction_quality | <30      |      225 |            0 |              nan |        nan |             0.83 |              29.8 |          48.6 |                47.1 |                         0   |
| contraction_quality | >=60     |      279 |            0 |              nan |        nan |             0.47 |              64.9 |          25.4 |                40.1 |                       100   |
| volume_ratio        | 0.8-1.0x |      234 |            0 |              nan |        nan |             1.8  |              36.8 |          37.1 |                 0   |                        47.9 |
| volume_ratio        | 1.0-1.2x |      157 |            0 |              nan |        nan |             3.52 |              36.9 |          39.3 |                 0   |                        45.2 |
| volume_ratio        | <0.8x    |      414 |            0 |              nan |        nan |             1.13 |              30.2 |          41.1 |                 0   |                        49   |
| volume_ratio        | >=1.2x   |      561 |            0 |              nan |        nan |             0.87 |              62.7 |          32.3 |               100   |                        48.1 |
| distance_from_21ema | 3-5%     |      207 |            0 |              nan |        nan |             0.38 |              40.6 |          31.6 |                29   |                        51.7 |
| distance_from_21ema | 5-8%     |      196 |            0 |              nan |        nan |             1.35 |              54.6 |          39.2 |                48   |                        46.9 |
| distance_from_21ema | 8-12%    |      164 |            0 |              nan |        nan |             0.34 |              55.5 |          39   |                61   |                        47   |
| distance_from_21ema | <=3%     |      548 |            0 |              nan |        nan |             1.34 |              26.6 |          36.3 |                19.5 |                        50.7 |
| distance_from_21ema | >12%     |      251 |            0 |              nan |        nan |             3.12 |              76.9 |          40.3 |                79.7 |                        40.6 |
| risk_pct            | 3-5%     |      341 |            0 |              nan |        nan |             1.85 |              32.8 |          32.3 |                22   |                        48.7 |
| risk_pct            | 5-8%     |      251 |            0 |              nan |        nan |             4.25 |              46.2 |          37.2 |                51   |                        37.8 |
| risk_pct            | 8-12%    |      148 |            0 |              nan |        nan |             3.56 |              61.5 |          32.9 |                72.3 |                        41.2 |
| risk_pct            | <=3%     |      348 |            0 |              nan |        nan |            -0.01 |              37.4 |          44.1 |                16.7 |                        59.8 |
| risk_pct            | >12%     |       99 |            0 |              nan |        nan |             4.28 |              70.7 |          31.9 |                89.9 |                        54.5 |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -2.02 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      745 |            0 |              nan |        nan |             1.8  |               0   |          45.4 |                28.1 |                        36.9 |
| range_break         | TRUE     |      621 |            0 |              nan |        nan |             0.83 |             100   |          25.5 |                56.7 |                        61.4 |
| custom_rs_rating    | 50-70    |      289 |            0 |              nan |        nan |             0.58 |              39.8 |          31.9 |                25.6 |                        54   |
| custom_rs_rating    | 70-90    |      502 |            0 |              nan |        nan |             1.19 |              45.6 |          39.4 |                43.6 |                        45.2 |
| custom_rs_rating    | <50      |      170 |            0 |              nan |        nan |             0.29 |              38.2 |          25.6 |                21.2 |                        52.9 |
| custom_rs_rating    | >=90     |      401 |            0 |              nan |        nan |             2.89 |              52.1 |          42.6 |                56.9 |                        45.1 |
| custom_rs_rating    | MISSING  |        4 |            0 |              nan |        nan |             2.01 |              75   |          50   |               100   |                        50   |
| rr_pass             | FALSE    |      738 |            0 |              nan |        nan |             1.91 |              50.5 |           0   |                40.2 |                        55.1 |
| rr_pass             | MISSING  |      197 |            0 |              nan |        nan |            -2.02 |              60.9 |         nan   |                61.9 |                        42.1 |
| rr_pass             | TRUE     |      431 |            0 |              nan |        nan |             2.48 |              29.7 |         100   |                32.9 |                        38.5 |
| vol_gate            | FALSE    |      805 |            0 |              nan |        nan |             1.74 |              33.4 |          39.6 |                 0   |                        48   |
| vol_gate            | TRUE     |      561 |            0 |              nan |        nan |             0.87 |              62.7 |          32.3 |               100   |                        48.1 |
| contraction_gate    | FALSE    |      710 |            0 |              nan |        nan |             1.76 |              33.8 |          44.5 |                41   |                         0   |
| contraction_gate    | TRUE     |      656 |            0 |              nan |        nan |             0.98 |              58.1 |          29   |                41.2 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
