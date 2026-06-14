# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 9333
- SLINGSHOT signal rows: 2130
- Active `setup_family=SLINGSHOT` rows: 1711
- Precedence-absorbed SLINGSHOT signal rows: 419

## Gate-observation counts
- Range-break true: 1026 / 2130
- Contraction quality ≥ 50: 1073 / 2130
- Volume ratio ≥ 1.2x: 815 / 2130
- `custom_rs_rating` ≥ 70: 1358 / 2130
- R:R ≥ 2: 641 / 2130
- > 8% above 21EMA: 572 / 2130
- Resolved outcomes available: 0 / 2130

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
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      302 |            0 |              nan |        nan |             1.87 |              29.8 |          44.7 |                34.8 |                         0   |
| contraction_quality | 40-50    |      451 |            0 |              nan |        nan |             0.12 |              41.5 |          39.2 |                36.8 |                         0   |
| contraction_quality | 50-60    |      615 |            0 |              nan |        nan |             0.84 |              54.3 |          27.1 |                38.4 |                       100   |
| contraction_quality | <30      |      304 |            0 |              nan |        nan |            -0.58 |              28   |          50   |                43.1 |                         0   |
| contraction_quality | >=60     |      458 |            0 |              nan |        nan |            -0.91 |              72.1 |          21.1 |                38.6 |                       100   |
| volume_ratio        | 0.8-1.0x |      428 |            0 |              nan |        nan |             1.37 |              40.9 |          34.7 |                 0   |                        49.8 |
| volume_ratio        | 1.0-1.2x |      280 |            0 |              nan |        nan |             2.02 |              43.2 |          36.7 |                 0   |                        51.1 |
| volume_ratio        | <0.8x    |      607 |            0 |              nan |        nan |             0.76 |              34.3 |          40.3 |                 0   |                        50.1 |
| volume_ratio        | >=1.2x   |      815 |            0 |              nan |        nan |            -1.29 |              64   |          27   |               100   |                        50.7 |
| distance_from_21ema | 3-5%     |      357 |            0 |              nan |        nan |             0.42 |              48.7 |          31   |                30.8 |                        55.5 |
| distance_from_21ema | 5-8%     |      323 |            0 |              nan |        nan |            -0.14 |              55.4 |          32.3 |                44   |                        55.1 |
| distance_from_21ema | 8-12%    |      235 |            0 |              nan |        nan |            -1.04 |              60.4 |          32.1 |                55.3 |                        45.1 |
| distance_from_21ema | <=3%     |      878 |            0 |              nan |        nan |             1.07 |              30.9 |          36.2 |                19   |                        51.3 |
| distance_from_21ema | >12%     |      337 |            0 |              nan |        nan |            -1.03 |              77.2 |          34.1 |                78.9 |                        41.8 |
| risk_pct            | 3-5%     |      540 |            0 |              nan |        nan |             1.08 |              39.3 |          28.9 |                23.1 |                        51.5 |
| risk_pct            | 5-8%     |      425 |            0 |              nan |        nan |             1.2  |              48.9 |          30.9 |                46.6 |                        45.4 |
| risk_pct            | 8-12%    |      210 |            0 |              nan |        nan |            -0.84 |              57.1 |          31   |                65.2 |                        45.7 |
| risk_pct            | <=3%     |      619 |            0 |              nan |        nan |             0.88 |              44.7 |          42.9 |                18.3 |                        58.2 |
| risk_pct            | >12%     |      156 |            0 |              nan |        nan |            -2.74 |              67.9 |          27.8 |                88.5 |                        47.4 |
| risk_pct            | MISSING  |      180 |            0 |              nan |        nan |            -2.02 |              57.2 |         nan   |                57.8 |                        40   |
| range_break         | FALSE    |     1104 |            0 |              nan |        nan |             0.77 |               0   |          44   |                26.5 |                        37   |
| range_break         | TRUE     |     1026 |            0 |              nan |        nan |            -0.39 |             100   |          22.1 |                50.9 |                        64.7 |
| custom_rs_rating    | 50-70    |      454 |            0 |              nan |        nan |             1.24 |              45.8 |          31.7 |                24   |                        58.4 |
| custom_rs_rating    | 70-90    |      781 |            0 |              nan |        nan |             0.49 |              49.3 |          35.1 |                40.2 |                        48.5 |
| custom_rs_rating    | <50      |      310 |            0 |              nan |        nan |             0.89 |              41.6 |          26.9 |                22.3 |                        51   |
| custom_rs_rating    | >=90     |      577 |            0 |              nan |        nan |            -1.34 |              51.6 |          38.7 |                54.9 |                        46.1 |
| custom_rs_rating    | MISSING  |        8 |            0 |              nan |        nan |            -0.08 |              75   |          28.6 |                75   |                        62.5 |
| rr_pass             | FALSE    |     1244 |            0 |              nan |        nan |             0.27 |              53.8 |           0   |                38.3 |                        58.2 |
| rr_pass             | MISSING  |      245 |            0 |              nan |        nan |            -2.5  |              68.2 |         nan   |                66.5 |                        46.1 |
| rr_pass             | TRUE     |      641 |            0 |              nan |        nan |             1.32 |              29.6 |         100   |                27.5 |                        36.8 |
| vol_gate            | FALSE    |     1315 |            0 |              nan |        nan |             1.22 |              38.3 |          37.7 |                 0   |                        50.2 |
| vol_gate            | TRUE     |      815 |            0 |              nan |        nan |            -1.29 |              64   |          27   |               100   |                        50.7 |
| contraction_gate    | FALSE    |     1057 |            0 |              nan |        nan |             0.39 |              34.2 |          43.8 |                38   |                         0   |
| contraction_gate    | TRUE     |     1073 |            0 |              nan |        nan |             0.09 |              61.9 |          24.6 |                38.5 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
