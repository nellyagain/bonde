# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 10068
- SLINGSHOT signal rows: 2216
- Active `setup_family=SLINGSHOT` rows: 1769
- Precedence-absorbed SLINGSHOT signal rows: 447

## Gate-observation counts
- Range-break true: 1079 / 2216
- Contraction quality ≥ 50: 1111 / 2216
- Volume ratio ≥ 1.2x: 860 / 2216
- `custom_rs_rating` ≥ 70: 1423 / 2216
- R:R ≥ 2: 664 / 2216
- > 8% above 21EMA: 599 / 2216
- Resolved outcomes available: 0 / 2216

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
| TBRG     | 2026-06-04    | SLINGSHOT      | True             |                  84.7879 |          1.32941  |                    73 |                1.86441  |        0.4219 |    nan        | False                 |             nan |
| TBRG     | 2026-06-04    | PAUSE          | True             |                  84.7879 |          1.32941  |                    73 |                1.86441  |        0.4219 |    nan        | False                 |             nan |
| CCRN     | 2026-06-03    | SLINGSHOT      | True             |                  78.7182 |          0.42593  |                    65 |                4.15578  |        0.457  |      1.1667   | False                 |             nan |
| CCRN     | 2026-06-03    | PAUSE          | True             |                  78.7182 |          0.42593  |                    65 |                4.15578  |        0.457  |      1.1667   | False                 |             nan |
| CCRN     | 2026-06-03    | ANTICIPATION   | True             |                  78.7182 |          0.42593  |                    65 |                4.15578  |        0.457  |      1.1667   | False                 |             nan |
| DSGN     | 2026-06-15    | SLINGSHOT      | True             |                  77.7752 |          0.967057 |                    89 |               -0.562491 |        2.8169 |      2.4688   | False                 |             nan |
| ANDE     | 2026-06-01    | SLINGSHOT      | True             |                  76.662  |          0.722028 |                    81 |                0.910587 |        3.3917 |      1.254    | False                 |             nan |
| UDR      | 2026-05-20    | SLINGSHOT      | True             |                  75.8082 |          0.709406 |                    27 |                3.04948  |        1.951  |      1.14864  | False                 |             nan |
| NLCP     | 2026-05-26    | SLINGSHOT      | True             |                  75.6705 |          4.1058   |                    39 |                4.76783  |        7.5364 |      2        | False                 |             nan |
| MRK      | 2026-05-19    | SLINGSHOT      | True             |                  75.6409 |          0.561273 |                    67 |                0.819765 |        2.5804 |      0.70707  | False                 |             nan |
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |    nan        | False                 |             nan |
| SPHR     | 2026-05-29    | SLINGSHOT      | True             |                  74.7683 |          0.751612 |                    93 |                3.62376  |        5.0354 |      0.848747 | False                 |             nan |
| CDP      | 2026-05-21    | SLINGSHOT      | True             |                  74.5696 |          1.33224  |                    46 |                1.75993  |        3.478  |      0.575217 | False                 |             nan |
| GNK      | 2026-06-05    | SLINGSHOT      | True             |                  74.3957 |          0.859985 |                    82 |                1.84898  |        4.2557 |      0.1315   | False                 |             nan |
| MFIN     | 2026-06-10    | SLINGSHOT      | True             |                  73.6754 |          8.19276  |                    39 |                3.44906  |        2.7136 |      0.7778   | False                 |             nan |
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| FLS      | 2026-06-11    | SLINGSHOT      | True             |                  73.5126 |          0.78988  |                    72 |                5.54592  |        6.4594 |      0.4951   | False                 |             nan |
| CWAN     | 2026-05-27    | SLINGSHOT      | True             |                  73.4129 |          0.25184  |                    44 |                0.530445 |        0.2866 |      1.57144  | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| MSGE     | 2026-06-01    | SLINGSHOT      | True             |                  73.2617 |          1.47848  |                    82 |                6.11944  |        2.1766 |      1.6095   | False                 |             nan |
| RAL      | 2026-06-09    | DELAYED_EP     | True             |                  72.777  |          1.31362  |                   nan |                7.80882  |        5.3797 |      0.7808   | False                 |             nan |
| RAL      | 2026-06-09    | SLINGSHOT      | True             |                  72.777  |          1.31362  |                   nan |                7.80882  |        5.3797 |      0.7808   | False                 |             nan |
| BHF      | 2026-06-09    | SLINGSHOT      | True             |                  72.7204 |          0.656263 |                    44 |                0.66925  |        0.6675 |      2.1905   | False                 |             nan |
| ACEL     | 2026-05-27    | SLINGSHOT      | True             |                  72.3597 |          0.966458 |                    46 |                1.71376  |        2.9046 |      0.971428 | False                 |             nan |
| BHF      | 2026-06-10    | SLINGSHOT      | True             |                  72.2521 |          1.1234   |                    45 |                0.989006 |        0.9305 |      0.7288   | False                 |             nan |
| TEN      | 2026-06-12    | SLINGSHOT      | True             |                  71.9938 |          0.639031 |                    83 |               -0.252072 |        4.6134 |      0.9888   | False                 |             nan |
| AWR      | 2026-06-05    | SLINGSHOT      | True             |                  71.9531 |          0.727081 |                    35 |                1.99442  |        3.3523 |      0.1925   | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | True             |                  71.881  |          0.708931 |                    42 |                2.88983  |        1.3304 |      1.16456  | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      315 |            0 |              nan |        nan |             1.94 |              29.5 |          44   |                35.9 |                         0   |
| contraction_quality | 40-50    |      477 |            0 |              nan |        nan |             0.36 |              41.9 |          37.7 |                37.7 |                         0   |
| contraction_quality | 50-60    |      640 |            0 |              nan |        nan |             0.75 |              55.3 |          27.6 |                38.6 |                       100   |
| contraction_quality | <30      |      313 |            0 |              nan |        nan |            -0.38 |              28.4 |          50.8 |                44.1 |                         0   |
| contraction_quality | >=60     |      471 |            0 |              nan |        nan |            -0.54 |              72.8 |          21.2 |                38.6 |                       100   |
| volume_ratio        | 0.8-1.0x |      437 |            0 |              nan |        nan |             1.37 |              41   |          35.2 |                 0   |                        49.4 |
| volume_ratio        | 1.0-1.2x |      299 |            0 |              nan |        nan |             1.87 |              44.1 |          36   |                 0   |                        52.5 |
| volume_ratio        | <0.8x    |      620 |            0 |              nan |        nan |             0.71 |              34.8 |          40.3 |                 0   |                        49.8 |
| volume_ratio        | >=1.2x   |      860 |            0 |              nan |        nan |            -0.84 |              64.2 |          26.8 |               100   |                        49.9 |
| distance_from_21ema | 3-5%     |      372 |            0 |              nan |        nan |             0.43 |              49.5 |          30.6 |                31.2 |                        55.6 |
| distance_from_21ema | 5-8%     |      335 |            0 |              nan |        nan |             0.43 |              54   |          32   |                44.8 |                        54   |
| distance_from_21ema | 8-12%    |      241 |            0 |              nan |        nan |            -0.69 |              61.4 |          31.6 |                55.6 |                        45.2 |
| distance_from_21ema | <=3%     |      910 |            0 |              nan |        nan |             1    |              31.8 |          36.2 |                19.1 |                        51.1 |
| distance_from_21ema | >12%     |      358 |            0 |              nan |        nan |            -0.7  |              77.4 |          34.5 |                79.9 |                        41.6 |
| risk_pct            | 3-5%     |      549 |            0 |              nan |        nan |             1.18 |              39.3 |          29.2 |                23.3 |                        51.5 |
| risk_pct            | 5-8%     |      441 |            0 |              nan |        nan |             1.21 |              49.2 |          30.6 |                47.4 |                        45.1 |
| risk_pct            | 8-12%    |      227 |            0 |              nan |        nan |            -0.76 |              55.5 |          30.4 |                65.2 |                        44.5 |
| risk_pct            | <=3%     |      646 |            0 |              nan |        nan |             0.76 |              46.3 |          43.1 |                18.4 |                        58.2 |
| risk_pct            | >12%     |      173 |            0 |              nan |        nan |            -1.31 |              68.2 |          25.9 |                87.9 |                        46.2 |
| risk_pct            | MISSING  |      180 |            0 |              nan |        nan |            -2.01 |              57.2 |         nan   |                57.8 |                        40   |
| range_break         | FALSE    |     1137 |            0 |              nan |        nan |             0.89 |               0   |          43.7 |                27.1 |                        36.4 |
| range_break         | TRUE     |     1079 |            0 |              nan |        nan |            -0.18 |             100   |          22.3 |                51.2 |                        64.6 |
| custom_rs_rating    | 50-70    |      463 |            0 |              nan |        nan |             1.27 |              46.4 |          31.5 |                24.2 |                        58.1 |
| custom_rs_rating    | 70-90    |      817 |            0 |              nan |        nan |             0.63 |              49.9 |          35   |                40.6 |                        48.5 |
| custom_rs_rating    | <50      |      321 |            0 |              nan |        nan |             0.72 |              42.7 |          27.2 |                22.1 |                        50.8 |
| custom_rs_rating    | >=90     |      606 |            0 |              nan |        nan |            -1.05 |              51.5 |          38.2 |                55.9 |                        45.7 |
| custom_rs_rating    | MISSING  |        9 |            0 |              nan |        nan |             2.2  |              77.8 |          37.5 |                66.7 |                        66.7 |
| rr_pass             | FALSE    |     1295 |            0 |              nan |        nan |             0.44 |              54   |           0   |                38.8 |                        57.5 |
| rr_pass             | MISSING  |      257 |            0 |              nan |        nan |            -1.95 |              69.6 |         nan   |                67.7 |                        46.3 |
| rr_pass             | TRUE     |      664 |            0 |              nan |        nan |             1.29 |              30.3 |         100   |                27.7 |                        37.2 |
| vol_gate            | FALSE    |     1356 |            0 |              nan |        nan |             1.17 |              38.9 |          37.7 |                 0   |                        50.3 |
| vol_gate            | TRUE     |      860 |            0 |              nan |        nan |            -0.84 |              64.2 |          26.8 |               100   |                        49.9 |
| contraction_gate    | FALSE    |     1105 |            0 |              nan |        nan |             0.58 |              34.6 |          43.1 |                39   |                         0   |
| contraction_gate    | TRUE     |     1111 |            0 |              nan |        nan |             0.19 |              62.7 |          24.9 |                38.6 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
