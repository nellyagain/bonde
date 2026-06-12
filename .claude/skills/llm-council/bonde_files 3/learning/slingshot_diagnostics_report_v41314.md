# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 9012
- SLINGSHOT signal rows: 2006
- Active `setup_family=SLINGSHOT` rows: 1605
- Precedence-absorbed SLINGSHOT signal rows: 401

## Gate-observation counts
- Range-break true: 967 / 2006
- Contraction quality ≥ 50: 1022 / 2006
- Volume ratio ≥ 1.2x: 785 / 2006
- `custom_rs_rating` ≥ 70: 1266 / 2006
- R:R ≥ 2: 592 / 2006
- > 8% above 21EMA: 551 / 2006
- Resolved outcomes available: 0 / 2006

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
| AWR      | 2026-06-05    | SLINGSHOT      | True             |                  71.9531 |          0.727081 |                    35 |                1.99442  |        3.3523 |      0.1925   | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | True             |                  71.881  |          0.708931 |                    42 |                2.88983  |        1.3304 |      1.16456  | False                 |             nan |
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      275 |            0 |              nan |        nan |             1.87 |              29.8 |          45.1 |                36.4 |                         0   |
| contraction_quality | 40-50    |      419 |            0 |              nan |        nan |             0.13 |              41.1 |          37.5 |                37.5 |                         0   |
| contraction_quality | 50-60    |      586 |            0 |              nan |        nan |             0.85 |              54.4 |          26.8 |                38.9 |                       100   |
| contraction_quality | <30      |      290 |            0 |              nan |        nan |            -0.58 |              29   |          49.6 |                44.8 |                         0   |
| contraction_quality | >=60     |      436 |            0 |              nan |        nan |            -0.9  |              71.1 |          21.3 |                39   |                       100   |
| volume_ratio        | 0.8-1.0x |      393 |            0 |              nan |        nan |             1.37 |              40.7 |          34.2 |                 0   |                        51.7 |
| volume_ratio        | 1.0-1.2x |      271 |            0 |              nan |        nan |             2.02 |              42.4 |          36   |                 0   |                        50.6 |
| volume_ratio        | <0.8x    |      557 |            0 |              nan |        nan |             0.78 |              33.8 |          39.2 |                 0   |                        51   |
| volume_ratio        | >=1.2x   |      785 |            0 |              nan |        nan |            -1.29 |              64.2 |          27.4 |               100   |                        50.7 |
| distance_from_21ema | 3-5%     |      327 |            0 |              nan |        nan |             0.44 |              47.7 |          30.2 |                32.1 |                        56.3 |
| distance_from_21ema | 5-8%     |      303 |            0 |              nan |        nan |            -0.14 |              55.8 |          31.7 |                44.6 |                        55.4 |
| distance_from_21ema | 8-12%    |      223 |            0 |              nan |        nan |            -1.04 |              62.3 |          33.1 |                57.4 |                        46.2 |
| distance_from_21ema | <=3%     |      825 |            0 |              nan |        nan |             1.08 |              30.2 |          35.2 |                19.4 |                        51.8 |
| distance_from_21ema | >12%     |      328 |            0 |              nan |        nan |            -1.03 |              77.4 |          34.7 |                78.4 |                        42.7 |
| risk_pct            | 3-5%     |      503 |            0 |              nan |        nan |             1.08 |              40   |          28   |                23.1 |                        52.7 |
| risk_pct            | 5-8%     |      399 |            0 |              nan |        nan |             1.2  |              49.4 |          31.9 |                48.4 |                        45.1 |
| risk_pct            | 8-12%    |      197 |            0 |              nan |        nan |            -0.84 |              59.9 |          31.6 |                66.5 |                        47.2 |
| risk_pct            | <=3%     |      577 |            0 |              nan |        nan |             0.9  |              43   |          41.3 |                18.9 |                        58.8 |
| risk_pct            | >12%     |      150 |            0 |              nan |        nan |            -2.74 |              66.7 |          28   |                88   |                        48.7 |
| risk_pct            | MISSING  |      180 |            0 |              nan |        nan |            -2.02 |              57.2 |         nan   |                57.8 |                        40   |
| range_break         | FALSE    |     1039 |            0 |              nan |        nan |             0.77 |               0   |          43.7 |                27   |                        37.8 |
| range_break         | TRUE     |      967 |            0 |              nan |        nan |            -0.38 |             100   |          21.4 |                52.1 |                        65   |
| custom_rs_rating    | 50-70    |      434 |            0 |              nan |        nan |             1.25 |              44   |          31.1 |                24   |                        59.2 |
| custom_rs_rating    | 70-90    |      724 |            0 |              nan |        nan |             0.48 |              49.4 |          34.7 |                41.3 |                        49.2 |
| custom_rs_rating    | <50      |      298 |            0 |              nan |        nan |             0.94 |              40.3 |          25.2 |                23.2 |                        49.7 |
| custom_rs_rating    | >=90     |      542 |            0 |              nan |        nan |            -1.34 |              53.9 |          39.2 |                56.6 |                        47.2 |
| custom_rs_rating    | MISSING  |        8 |            0 |              nan |        nan |            -0.08 |              75   |          28.6 |                75   |                        62.5 |
| rr_pass             | FALSE    |     1174 |            0 |              nan |        nan |             0.28 |              53.9 |           0   |                38.8 |                        58.5 |
| rr_pass             | MISSING  |      240 |            0 |              nan |        nan |            -2.5  |              67.5 |         nan   |                65.8 |                        46.7 |
| rr_pass             | TRUE     |      592 |            0 |              nan |        nan |             1.34 |              29.1 |         100   |                29.1 |                        37.7 |
| vol_gate            | FALSE    |     1221 |            0 |              nan |        nan |             1.23 |              37.9 |          36.9 |                 0   |                        51.1 |
| vol_gate            | TRUE     |      785 |            0 |              nan |        nan |            -1.29 |              64.2 |          27.4 |               100   |                        50.7 |
| contraction_gate    | FALSE    |      984 |            0 |              nan |        nan |             0.39 |              34.3 |          43.1 |                39.3 |                         0   |
| contraction_gate    | TRUE     |     1022 |            0 |              nan |        nan |             0.11 |              61.5 |          24.5 |                38.9 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
