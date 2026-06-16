# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 9548
- SLINGSHOT signal rows: 2163
- Active `setup_family=SLINGSHOT` rows: 1735
- Precedence-absorbed SLINGSHOT signal rows: 428

## Gate-observation counts
- Range-break true: 1040 / 2163
- Contraction quality ≥ 50: 1083 / 2163
- Volume ratio ≥ 1.2x: 830 / 2163
- `custom_rs_rating` ≥ 70: 1382 / 2163
- R:R ≥ 2: 657 / 2163
- > 8% above 21EMA: 580 / 2163
- Resolved outcomes available: 0 / 2163

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
| contraction_quality | 30-40    |      306 |            0 |              nan |        nan |             1.88 |              29.7 |          45.1 |                35   |                         0   |
| contraction_quality | 40-50    |      465 |            0 |              nan |        nan |             0.18 |              41.3 |          38.1 |                37.6 |                         0   |
| contraction_quality | 50-60    |      622 |            0 |              nan |        nan |             0.83 |              54.3 |          27.8 |                37.9 |                       100   |
| contraction_quality | <30      |      309 |            0 |              nan |        nan |            -0.58 |              27.8 |          50.6 |                43.7 |                         0   |
| contraction_quality | >=60     |      461 |            0 |              nan |        nan |            -0.82 |              72.2 |          21.5 |                38.4 |                       100   |
| volume_ratio        | 0.8-1.0x |      432 |            0 |              nan |        nan |             1.37 |              41   |          35.1 |                 0   |                        49.8 |
| volume_ratio        | 1.0-1.2x |      287 |            0 |              nan |        nan |             2.06 |              42.9 |          37.6 |                 0   |                        51.6 |
| volume_ratio        | <0.8x    |      614 |            0 |              nan |        nan |             0.76 |              34.7 |          40.5 |                 0   |                        50   |
| volume_ratio        | >=1.2x   |      830 |            0 |              nan |        nan |            -1.21 |              63.5 |          27   |               100   |                        49.8 |
| distance_from_21ema | 3-5%     |      362 |            0 |              nan |        nan |             0.46 |              48.6 |          31.2 |                30.7 |                        55.2 |
| distance_from_21ema | 5-8%     |      329 |            0 |              nan |        nan |            -0.11 |              54.4 |          32.6 |                44.4 |                        54.7 |
| distance_from_21ema | 8-12%    |      236 |            0 |              nan |        nan |            -0.98 |              60.6 |          32.4 |                55.1 |                        44.9 |
| distance_from_21ema | <=3%     |      892 |            0 |              nan |        nan |             1.06 |              31.3 |          36.5 |                19.1 |                        51.1 |
| distance_from_21ema | >12%     |      344 |            0 |              nan |        nan |            -0.92 |              76.5 |          34   |                79.4 |                        41   |
| risk_pct            | 3-5%     |      545 |            0 |              nan |        nan |             1.11 |              39.4 |          29.2 |                23.1 |                        51.4 |
| risk_pct            | 5-8%     |      431 |            0 |              nan |        nan |             1.18 |              48.3 |          31.1 |                47.1 |                        45   |
| risk_pct            | 8-12%    |      217 |            0 |              nan |        nan |            -0.84 |              55.3 |          30.9 |                65   |                        45.2 |
| risk_pct            | <=3%     |      630 |            0 |              nan |        nan |             0.89 |              45.2 |          43.5 |                18.3 |                        57.9 |
| risk_pct            | >12%     |      160 |            0 |              nan |        nan |            -2.31 |              68.1 |          26.9 |                88.1 |                        46.2 |
| risk_pct            | MISSING  |      180 |            0 |              nan |        nan |            -2.02 |              57.2 |         nan   |                57.8 |                        40   |
| range_break         | FALSE    |     1123 |            0 |              nan |        nan |             0.77 |               0   |          44   |                27   |                        36.7 |
| range_break         | TRUE     |     1040 |            0 |              nan |        nan |            -0.33 |             100   |          22.6 |                50.7 |                        64.5 |
| custom_rs_rating    | 50-70    |      457 |            0 |              nan |        nan |             1.29 |              46   |          32   |                24.1 |                        58.2 |
| custom_rs_rating    | 70-90    |      795 |            0 |              nan |        nan |             0.48 |              49.4 |          35.1 |                40.4 |                        48.3 |
| custom_rs_rating    | <50      |      315 |            0 |              nan |        nan |             0.89 |              41.9 |          27.1 |                22.5 |                        50.5 |
| custom_rs_rating    | >=90     |      587 |            0 |              nan |        nan |            -1.27 |              50.8 |          39.1 |                54.9 |                        45.7 |
| custom_rs_rating    | MISSING  |        9 |            0 |              nan |        nan |            -0.08 |              77.8 |          37.5 |                66.7 |                        66.7 |
| rr_pass             | FALSE    |     1261 |            0 |              nan |        nan |             0.29 |              53.6 |           0   |                38.6 |                        57.6 |
| rr_pass             | MISSING  |      245 |            0 |              nan |        nan |            -2.31 |              68.2 |         nan   |                66.5 |                        46.1 |
| rr_pass             | TRUE     |      657 |            0 |              nan |        nan |             1.32 |              30   |         100   |                27.4 |                        37.1 |
| vol_gate            | FALSE    |     1333 |            0 |              nan |        nan |             1.22 |              38.5 |          38.1 |                 0   |                        50.3 |
| vol_gate            | TRUE     |      830 |            0 |              nan |        nan |            -1.21 |              63.5 |          27   |               100   |                        49.8 |
| contraction_gate    | FALSE    |     1080 |            0 |              nan |        nan |             0.41 |              34.2 |          43.6 |                38.6 |                         0   |
| contraction_gate    | TRUE     |     1083 |            0 |              nan |        nan |             0.13 |              62   |          25.2 |                38.1 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
