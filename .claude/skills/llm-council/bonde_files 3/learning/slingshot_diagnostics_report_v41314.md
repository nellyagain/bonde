# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 8305
- SLINGSHOT signal rows: 1745
- Active `setup_family=SLINGSHOT` rows: 1394
- Precedence-absorbed SLINGSHOT signal rows: 351

## Gate-observation counts
- Range-break true: 819 / 1745
- Contraction quality ≥ 50: 872 / 1745
- Volume ratio ≥ 1.2x: 684 / 1745
- `custom_rs_rating` ≥ 70: 1059 / 1745
- R:R ≥ 2: 521 / 1745
- > 8% above 21EMA: 465 / 1745
- Resolved outcomes available: 0 / 1745

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
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| CWAN     | 2026-05-27    | SLINGSHOT      | True             |                  73.4129 |          0.25184  |                    44 |                0.530445 |        0.2866 |      1.57144  | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| MSGE     | 2026-06-01    | SLINGSHOT      | True             |                  73.2617 |          1.47848  |                    82 |                6.11944  |        2.1766 |      1.6095   | False                 |             nan |
| RAL      | 2026-06-09    | DELAYED_EP     | True             |                  72.777  |          1.31362  |                   nan |                7.80882  |        5.3797 |      0.7808   | False                 |             nan |
| RAL      | 2026-06-09    | SLINGSHOT      | True             |                  72.777  |          1.31362  |                   nan |                7.80882  |        5.3797 |      0.7808   | False                 |             nan |
| BHF      | 2026-06-09    | SLINGSHOT      | True             |                  72.7204 |          0.656263 |                    44 |                0.66925  |        0.6675 |      2.1905   | False                 |             nan |
| ACEL     | 2026-05-27    | SLINGSHOT      | True             |                  72.3597 |          0.966458 |                    46 |                1.71376  |        2.9046 |      0.971428 | False                 |             nan |
| AWR      | 2026-06-05    | SLINGSHOT      | True             |                  71.9531 |          0.727081 |                    35 |                1.99442  |        3.3523 |      0.1925   | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | True             |                  71.881  |          0.708931 |                    42 |                2.88983  |        1.3304 |      1.16456  | False                 |             nan |
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |
| DCO      | 2026-06-09    | SLINGSHOT      | True             |                  71.1887 |          0.974212 |                    87 |                5.57073  |        4.8152 |      0.7689   | False                 |             nan |
| AVA      | 2026-05-22    | SLINGSHOT      | True             |                  70.9952 |          0.65771  |                    35 |                1.26276  |        1.6555 |      1.34783  | False                 |             nan |
| WBD      | 2026-05-20    | SLINGSHOT      | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      241 |            0 |              nan |        nan |             2.5  |              29   |          45.8 |                36.9 |                         0   |
| contraction_quality | 40-50    |      367 |            0 |              nan |        nan |            -0.14 |              39.2 |          37.4 |                38.4 |                         0   |
| contraction_quality | 50-60    |      495 |            0 |              nan |        nan |             0.64 |              52.7 |          28.8 |                37.8 |                       100   |
| contraction_quality | <30      |      265 |            0 |              nan |        nan |             0.24 |              29.8 |          47.1 |                46   |                         0   |
| contraction_quality | >=60     |      377 |            0 |              nan |        nan |            -0.99 |              70.3 |          23.2 |                38.5 |                       100   |
| volume_ratio        | 0.8-1.0x |      329 |            0 |              nan |        nan |             1.13 |              39.8 |          34.5 |                 0   |                        51.4 |
| volume_ratio        | 1.0-1.2x |      227 |            0 |              nan |        nan |             2.21 |              40.5 |          35.4 |                 0   |                        49.8 |
| volume_ratio        | <0.8x    |      505 |            0 |              nan |        nan |             0.79 |              32.7 |          39.2 |                 0   |                        51.1 |
| volume_ratio        | >=1.2x   |      684 |            0 |              nan |        nan |            -0.83 |              63   |          29.6 |               100   |                        48.5 |
| distance_from_21ema | 3-5%     |      277 |            0 |              nan |        nan |             0.03 |              48.7 |          29.3 |                31   |                        56.3 |
| distance_from_21ema | 5-8%     |      244 |            0 |              nan |        nan |             0.1  |              54.9 |          35.8 |                46.3 |                        49.6 |
| distance_from_21ema | 8-12%    |      189 |            0 |              nan |        nan |            -1.24 |              60.3 |          36.1 |                61.4 |                        46   |
| distance_from_21ema | <=3%     |      759 |            0 |              nan |        nan |             0.75 |              29.5 |          34.2 |                19.4 |                        52   |
| distance_from_21ema | >12%     |      276 |            0 |              nan |        nan |             0.9  |              76.8 |          38.8 |                80.4 |                        40.9 |
| risk_pct            | 3-5%     |      440 |            0 |              nan |        nan |             1.1  |              37.3 |          28.3 |                22.3 |                        50.9 |
| risk_pct            | 5-8%     |      300 |            0 |              nan |        nan |             1.37 |              48.3 |          33.1 |                52.3 |                        41.7 |
| risk_pct            | 8-12%    |      158 |            0 |              nan |        nan |            -0.11 |              63.3 |          31.3 |                71.5 |                        44.3 |
| risk_pct            | <=3%     |      540 |            0 |              nan |        nan |             0.17 |              40.9 |          41.8 |                18   |                        58.9 |
| risk_pct            | >12%     |      127 |            0 |              nan |        nan |             0.71 |              67.7 |          29.9 |                90.6 |                        49.6 |
| risk_pct            | MISSING  |      180 |            0 |              nan |        nan |            -2.02 |              57.2 |         nan   |                57.8 |                        40   |
| range_break         | FALSE    |      926 |            0 |              nan |        nan |             1.02 |               0   |          43.4 |                27.3 |                        37.4 |
| range_break         | TRUE     |      819 |            0 |              nan |        nan |            -0.49 |             100   |          22.9 |                52.6 |                        64.2 |
| custom_rs_rating    | 50-70    |      406 |            0 |              nan |        nan |             0.73 |              43.1 |          31.8 |                23.6 |                        58.4 |
| custom_rs_rating    | 70-90    |      620 |            0 |              nan |        nan |             0.31 |              48.5 |          35.6 |                42.6 |                        47.6 |
| custom_rs_rating    | <50      |      273 |            0 |              nan |        nan |             0.47 |              38.8 |          25.3 |                22.3 |                        49.8 |
| custom_rs_rating    | >=90     |      439 |            0 |              nan |        nan |             0.03 |              52.6 |          41.6 |                58.5 |                        45.6 |
| custom_rs_rating    | MISSING  |        7 |            0 |              nan |        nan |            -0.08 |              85.7 |          33.3 |                85.7 |                        57.1 |
| rr_pass             | FALSE    |      995 |            0 |              nan |        nan |             0.58 |              51.8 |           0   |                38   |                        57   |
| rr_pass             | MISSING  |      229 |            0 |              nan |        nan |            -2.62 |              65.9 |         nan   |                64.2 |                        44.1 |
| rr_pass             | TRUE     |      521 |            0 |              nan |        nan |             1.31 |              29.4 |         100   |                30.5 |                        39.2 |
| vol_gate            | FALSE    |     1061 |            0 |              nan |        nan |             1.15 |              36.6 |          37   |                 0   |                        50.9 |
| vol_gate            | TRUE     |      684 |            0 |              nan |        nan |            -0.83 |              63   |          29.6 |               100   |                        48.5 |
| contraction_gate    | FALSE    |      873 |            0 |              nan |        nan |             0.67 |              33.6 |          42.6 |                40.3 |                         0   |
| contraction_gate    | TRUE     |      872 |            0 |              nan |        nan |            -0.04 |              60.3 |          26.5 |                38.1 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
