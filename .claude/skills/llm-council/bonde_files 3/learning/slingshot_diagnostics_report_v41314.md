# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 7936
- SLINGSHOT signal rows: 1612
- Active `setup_family=SLINGSHOT` rows: 1276
- Precedence-absorbed SLINGSHOT signal rows: 336

## Gate-observation counts
- Range-break true: 736 / 1612
- Contraction quality ≥ 50: 791 / 1612
- Volume ratio ≥ 1.2x: 638 / 1612
- `custom_rs_rating` ≥ 70: 994 / 1612
- R:R ≥ 2: 497 / 1612
- > 8% above 21EMA: 443 / 1612
- Resolved outcomes available: 0 / 1612

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
| ACEL     | 2026-05-27    | SLINGSHOT      | True             |                  72.3597 |          0.966458 |                    46 |                1.71376  |        2.9046 |      0.971428 | False                 |             nan |
| AWR      | 2026-06-05    | SLINGSHOT      | True             |                  71.9531 |          0.727081 |                    35 |                1.99442  |        3.3523 |      0.1925   | False                 |             nan |
| EPR      | 2026-05-26    | SLINGSHOT      | True             |                  71.881  |          0.708931 |                    42 |                2.88983  |        1.3304 |      1.16456  | False                 |             nan |
| DTE      | 2026-05-22    | SLINGSHOT      | True             |                  71.8431 |          0.581559 |                    36 |                0.944113 |        1.3061 |      1.65263  | False                 |             nan |
| TENX     | 2026-05-21    | SLINGSHOT      | True             |                  71.4525 |          0.795033 |                    83 |               -1.18026  |        6.902  |      1.18182  | False                 |             nan |
| AVA      | 2026-05-22    | SLINGSHOT      | True             |                  70.9952 |          0.65771  |                    35 |                1.26276  |        1.6555 |      1.34783  | False                 |             nan |
| WBD      | 2026-05-20    | SLINGSHOT      | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| WBD      | 2026-05-20    | EP9M           | True             |                  70.9894 |          0.801557 |                    91 |                0.897394 |        1.3484 |      0.702697 | False                 |             nan |
| IFS      | 2026-05-19    | SLINGSHOT      | True             |                  70.9804 |          1.60272  |                    58 |                2.11166  |        4.0291 |      0.644563 | False                 |             nan |
| SNEX     | 2026-06-01    | SLINGSHOT      | True             |                  70.8804 |          0.997637 |                    88 |                3.84413  |        4.7901 |      0.9857   | False                 |             nan |
| GTY      | 2026-05-20    | SLINGSHOT      | True             |                  70.7307 |          1.22781  |                    53 |                1.70789  |        2.9447 |      0.412055 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      225 |            0 |              nan |        nan |             2.5  |              28.9 |          47.4 |                36   |                         0   |
| contraction_quality | 40-50    |      343 |            0 |              nan |        nan |            -0.14 |              38.5 |          38.5 |                38.5 |                         0   |
| contraction_quality | 50-60    |      450 |            0 |              nan |        nan |             0.64 |              52   |          30.5 |                38.2 |                       100   |
| contraction_quality | <30      |      253 |            0 |              nan |        nan |             0.24 |              28.9 |          47.2 |                45.5 |                         0   |
| contraction_quality | >=60     |      341 |            0 |              nan |        nan |            -0.98 |              68   |          23.6 |                40.5 |                       100   |
| volume_ratio        | 0.8-1.0x |      300 |            0 |              nan |        nan |             1.13 |              37.3 |          35.9 |                 0   |                        50.7 |
| volume_ratio        | 1.0-1.2x |      209 |            0 |              nan |        nan |             2.21 |              38.3 |          38.1 |                 0   |                        48.8 |
| volume_ratio        | <0.8x    |      465 |            0 |              nan |        nan |             0.78 |              30.1 |          40.5 |                 0   |                        48.8 |
| volume_ratio        | >=1.2x   |      638 |            0 |              nan |        nan |            -0.83 |              63.3 |          30.3 |               100   |                        48.6 |
| distance_from_21ema | 3-5%     |      252 |            0 |              nan |        nan |             0.03 |              47.2 |          30.2 |                31   |                        53.2 |
| distance_from_21ema | 5-8%     |      212 |            0 |              nan |        nan |             0.1  |              53.3 |          39.7 |                49.5 |                        44.3 |
| distance_from_21ema | 8-12%    |      173 |            0 |              nan |        nan |            -1.24 |              57.2 |          37.1 |                61.8 |                        45.1 |
| distance_from_21ema | <=3%     |      705 |            0 |              nan |        nan |             0.75 |              28.2 |          35.1 |                18.7 |                        52.8 |
| distance_from_21ema | >12%     |      270 |            0 |              nan |        nan |             0.9  |              76.3 |          39   |                80   |                        41.9 |
| risk_pct            | 3-5%     |      397 |            0 |              nan |        nan |             1.1  |              35   |          29.5 |                22.2 |                        48.9 |
| risk_pct            | 5-8%     |      272 |            0 |              nan |        nan |             1.37 |              47.4 |          35.4 |                51.1 |                        39.7 |
| risk_pct            | 8-12%    |      154 |            0 |              nan |        nan |            -0.11 |              63   |          31.5 |                71.4 |                        43.5 |
| risk_pct            | <=3%     |      486 |            0 |              nan |        nan |             0.16 |              38.3 |          43   |                17.7 |                        59.3 |
| risk_pct            | >12%     |      123 |            0 |              nan |        nan |             0.71 |              66.7 |          30.5 |                90.2 |                        50.4 |
| risk_pct            | MISSING  |      180 |            0 |              nan |        nan |            -2.02 |              57.2 |         nan   |                57.8 |                        40   |
| range_break         | FALSE    |      876 |            0 |              nan |        nan |             1.01 |               0   |          44.7 |                26.7 |                        37.1 |
| range_break         | TRUE     |      736 |            0 |              nan |        nan |            -0.49 |             100   |          23.4 |                54.9 |                        63.3 |
| custom_rs_rating    | 50-70    |      376 |            0 |              nan |        nan |             0.73 |              41.8 |          31.6 |                23.4 |                        57.4 |
| custom_rs_rating    | 70-90    |      569 |            0 |              nan |        nan |             0.31 |              46.9 |          37.2 |                43.6 |                        45.9 |
| custom_rs_rating    | <50      |      237 |            0 |              nan |        nan |             0.46 |              36.3 |          27.7 |                21.5 |                        50.6 |
| custom_rs_rating    | >=90     |      425 |            0 |              nan |        nan |             0.03 |              52.2 |          42.1 |                58.1 |                        45.2 |
| custom_rs_rating    | MISSING  |        5 |            0 |              nan |        nan |            -0.08 |              80   |          50   |                80   |                        40   |
| rr_pass             | FALSE    |      900 |            0 |              nan |        nan |             0.58 |              50.9 |           0   |                38.9 |                        56   |
| rr_pass             | MISSING  |      215 |            0 |              nan |        nan |            -2.62 |              64.2 |         nan   |                63.3 |                        44.2 |
| rr_pass             | TRUE     |      497 |            0 |              nan |        nan |             1.3  |              28.2 |         100   |                30.6 |                        38.6 |
| vol_gate            | FALSE    |      974 |            0 |              nan |        nan |             1.15 |              34.1 |          38.5 |                 0   |                        49.4 |
| vol_gate            | TRUE     |      638 |            0 |              nan |        nan |            -0.83 |              63.3 |          30.3 |               100   |                        48.6 |
| contraction_gate    | FALSE    |      821 |            0 |              nan |        nan |             0.67 |              32.9 |          43.5 |                40   |                         0   |
| contraction_gate    | TRUE     |      791 |            0 |              nan |        nan |            -0.04 |              58.9 |          27.6 |                39.2 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
