# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 10910
- SLINGSHOT signal rows: 2443
- Active `setup_family=SLINGSHOT` rows: 1955
- Precedence-absorbed SLINGSHOT signal rows: 488

## Gate-observation counts
- Range-break true: 1249 / 2443
- Contraction quality ≥ 50: 1217 / 2443
- Volume ratio ≥ 1.2x: 975 / 2443
- `custom_rs_rating` ≥ 70: 1587 / 2443
- R:R ≥ 2: 753 / 2443
- > 8% above 21EMA: 676 / 2443
- Resolved outcomes available: 0 / 2443

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
| MSM      | 2026-06-18    | SLINGSHOT      | True             |                  72.7041 |          0.745027 |                    78 |                4.66002  |        2.2105 |      1.3574   | False                 |             nan |
| ACEL     | 2026-05-27    | SLINGSHOT      | True             |                  72.3597 |          0.966458 |                    46 |                1.71376  |        2.9046 |      0.971428 | False                 |             nan |
| BHF      | 2026-06-10    | SLINGSHOT      | True             |                  72.2521 |          1.1234   |                    45 |                0.989006 |        0.9305 |      0.7288   | False                 |             nan |
| TEN      | 2026-06-12    | SLINGSHOT      | True             |                  71.9938 |          0.639031 |                    83 |               -0.252072 |        4.6134 |      0.9888   | False                 |             nan |
| AWR      | 2026-06-05    | SLINGSHOT      | True             |                  71.9531 |          0.727081 |                    35 |                1.99442  |        3.3523 |      0.1925   | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      352 |            0 |              nan |        nan |             2.41 |              34.4 |          45.2 |                36.4 |                         0   |
| contraction_quality | 40-50    |      536 |            0 |              nan |        nan |             0.43 |              45   |          39.5 |                39.7 |                         0   |
| contraction_quality | 50-60    |      706 |            0 |              nan |        nan |             0.9  |              57.2 |          27.7 |                39.8 |                       100   |
| contraction_quality | <30      |      338 |            0 |              nan |        nan |            -0.55 |              32.2 |          51.4 |                45.3 |                         0   |
| contraction_quality | >=60     |      511 |            0 |              nan |        nan |            -0.29 |              73.2 |          21   |                39.1 |                       100   |
| volume_ratio        | 0.8-1.0x |      479 |            0 |              nan |        nan |             1.64 |              43.4 |          35.9 |                 0   |                        49.7 |
| volume_ratio        | 1.0-1.2x |      330 |            0 |              nan |        nan |             1.79 |              47.6 |          35.6 |                 0   |                        51.2 |
| volume_ratio        | <0.8x    |      659 |            0 |              nan |        nan |             0.94 |              36.9 |          42   |                 0   |                        49.9 |
| volume_ratio        | >=1.2x   |      975 |            0 |              nan |        nan |            -0.73 |              65.7 |          27.7 |               100   |                        49.3 |
| distance_from_21ema | 3-5%     |      410 |            0 |              nan |        nan |             0.43 |              52.7 |          32.7 |                31.7 |                        55.1 |
| distance_from_21ema | 5-8%     |      387 |            0 |              nan |        nan |             0.82 |              58.7 |          34.4 |                45.7 |                        52.2 |
| distance_from_21ema | 8-12%    |      287 |            0 |              nan |        nan |            -0.33 |              65.9 |          30.2 |                56.1 |                        44.9 |
| distance_from_21ema | <=3%     |      970 |            0 |              nan |        nan |             1    |              32.1 |          37   |                20.2 |                        51.4 |
| distance_from_21ema | >12%     |      389 |            0 |              nan |        nan |            -0.1  |              78.7 |          33.1 |                79.9 |                        41.4 |
| risk_pct            | 3-5%     |      627 |            0 |              nan |        nan |             1.01 |              44   |          30.6 |                26.3 |                        50.9 |
| risk_pct            | 5-8%     |      504 |            0 |              nan |        nan |             2.24 |              53.4 |          29.6 |                48   |                        45.2 |
| risk_pct            | 8-12%    |      249 |            0 |              nan |        nan |            -0.07 |              57   |          29.6 |                66.7 |                        46.2 |
| risk_pct            | <=3%     |      701 |            0 |              nan |        nan |             0.63 |              47.5 |          45.6 |                19.5 |                        56.8 |
| risk_pct            | >12%     |      181 |            0 |              nan |        nan |            -2.09 |              69.6 |          24.6 |                88.4 |                        47   |
| risk_pct            | MISSING  |      181 |            0 |              nan |        nan |            -2.01 |              56.9 |         nan   |                58   |                        39.8 |
| range_break         | FALSE    |     1194 |            0 |              nan |        nan |             1.02 |               0   |          44.8 |                28   |                        36.8 |
| range_break         | TRUE     |     1249 |            0 |              nan |        nan |             0.05 |             100   |          23.8 |                51.3 |                        62.3 |
| custom_rs_rating    | 50-70    |      506 |            0 |              nan |        nan |             1.12 |              49.2 |          32.2 |                26.5 |                        57.5 |
| custom_rs_rating    | 70-90    |      915 |            0 |              nan |        nan |             0.66 |              52.3 |          35.8 |                41.6 |                        47.3 |
| custom_rs_rating    | <50      |      339 |            0 |              nan |        nan |             0.5  |              43.7 |          28.6 |                22.7 |                        50.7 |
| custom_rs_rating    | >=90     |      672 |            0 |              nan |        nan |            -0.02 |              54.2 |          38.3 |                55.8 |                        46.6 |
| custom_rs_rating    | MISSING  |       11 |            0 |              nan |        nan |             2.16 |              81.8 |          30   |                72.7 |                        72.7 |
| rr_pass             | FALSE    |     1423 |            0 |              nan |        nan |             0.66 |              56.8 |           0   |                40.2 |                        57.6 |
| rr_pass             | MISSING  |      267 |            0 |              nan |        nan |            -2.16 |              70.4 |         nan   |                68.9 |                        47.2 |
| rr_pass             | TRUE     |      753 |            0 |              nan |        nan |             1.39 |              33.6 |         100   |                29.1 |                        36.1 |
| vol_gate            | FALSE    |     1468 |            0 |              nan |        nan |             1.35 |              41.4 |          38.6 |                 0   |                        50.1 |
| vol_gate            | TRUE     |      975 |            0 |              nan |        nan |            -0.73 |              65.7 |          27.7 |               100   |                        49.3 |
| contraction_gate    | FALSE    |     1226 |            0 |              nan |        nan |             0.72 |              38.4 |          44.3 |                40.3 |                         0   |
| contraction_gate    | TRUE     |     1217 |            0 |              nan |        nan |             0.4  |              63.9 |          24.9 |                39.5 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
