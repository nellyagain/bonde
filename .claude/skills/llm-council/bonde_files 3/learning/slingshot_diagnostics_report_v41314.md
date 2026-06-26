# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 12001
- SLINGSHOT signal rows: 2813
- Active `setup_family=SLINGSHOT` rows: 2280
- Precedence-absorbed SLINGSHOT signal rows: 533

## Gate-observation counts
- Range-break true: 1500 / 2813
- Contraction quality ≥ 50: 1432 / 2813
- Volume ratio ≥ 1.2x: 1119 / 2813
- `custom_rs_rating` ≥ 70: 1731 / 2813
- R:R ≥ 2: 872 / 2813
- > 8% above 21EMA: 756 / 2813
- Resolved outcomes available: 0 / 2813

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
| PRA      | 2026-06-24    | SLINGSHOT      | True             |                  78.1911 |          6.11973  |                    35 |                1.59522  |        0.1599 |    nan        | False                 |             nan |
| DSGN     | 2026-06-15    | SLINGSHOT      | True             |                  77.7752 |          0.967057 |                    89 |               -0.562491 |        2.8169 |      2.4688   | False                 |             nan |
| CCRN     | 2026-06-24    | SLINGSHOT      | True             |                  76.9045 |          0.33955  |                    67 |                1.33075  |        0.0758 |      5.9999   | False                 |             nan |
| CCRN     | 2026-06-24    | PAUSE          | True             |                  76.9045 |          0.33955  |                    67 |                1.33075  |        0.0758 |      5.9999   | False                 |             nan |
| ANDE     | 2026-06-01    | SLINGSHOT      | True             |                  76.662  |          0.722028 |                    81 |                0.910587 |        3.3917 |      1.254    | False                 |             nan |
| UDR      | 2026-05-20    | SLINGSHOT      | True             |                  75.8082 |          0.709406 |                    27 |                3.04948  |        1.951  |      1.14864  | False                 |             nan |
| NLCP     | 2026-05-26    | SLINGSHOT      | True             |                  75.6705 |          4.1058   |                    39 |                4.76783  |        7.5364 |      2        | False                 |             nan |
| MRK      | 2026-05-19    | SLINGSHOT      | True             |                  75.6409 |          0.561273 |                    67 |                0.819765 |        2.5804 |      0.70707  | False                 |             nan |
| XPEL     | 2026-06-25    | SLINGSHOT      | True             |                  75.6037 |          1.54592  |                    73 |                5.1094   |        4.9791 |      0.6457   | False                 |             nan |
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |    nan        | False                 |             nan |
| NTB      | 2026-06-25    | SLINGSHOT      | True             |                  75.0223 |          0.738968 |                    62 |                2.65648  |        1.7299 |      1.4612   | False                 |             nan |
| SPHR     | 2026-05-29    | SLINGSHOT      | True             |                  74.7683 |          0.751612 |                    93 |                3.62376  |        5.0354 |      0.848747 | False                 |             nan |
| CDP      | 2026-05-21    | SLINGSHOT      | True             |                  74.5696 |          1.33224  |                    46 |                1.75993  |        3.478  |      0.575217 | False                 |             nan |
| GNK      | 2026-06-05    | SLINGSHOT      | True             |                  74.3957 |          0.859985 |                    82 |                1.84898  |        4.2557 |      0.1315   | False                 |             nan |
| QUAD     | 2026-06-23    | SLINGSHOT      | True             |                  74.1399 |          0.961672 |                    72 |                6.24866  |        5.8458 |    nan        | False                 |             nan |
| MFIN     | 2026-06-10    | SLINGSHOT      | True             |                  73.6754 |          8.19276  |                    39 |                3.44906  |        2.7136 |      0.7778   | False                 |             nan |
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| FLS      | 2026-06-11    | SLINGSHOT      | True             |                  73.5126 |          0.78988  |                    72 |                5.54592  |        6.4594 |      0.4951   | False                 |             nan |
| CTO      | 2026-06-24    | SLINGSHOT      | True             |                  73.4797 |          1.77626  |                    54 |                2.92958  |        2.5641 |    nan        | False                 |             nan |
| CWAN     | 2026-05-27    | SLINGSHOT      | True             |                  73.4129 |          0.25184  |                    44 |                0.530445 |        0.2866 |      1.57144  | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| REPL     | 2026-05-29    | EP_SPIKE       | True             |                  73.3859 |          6.98289  |                    72 |               80.5504   |       15.4019 |      2        | False                 |             nan |
| MSGE     | 2026-06-01    | SLINGSHOT      | True             |                  73.2617 |          1.47848  |                    82 |                6.11944  |        2.1766 |      1.6095   | False                 |             nan |
| NNI      | 2026-06-24    | SLINGSHOT      | True             |                  73.1562 |          1.07748  |                    40 |                2.43896  |        2.5885 |      0.5867   | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      411 |            0 |              nan |        nan |             2.62 |              36.5 |          44.3 |                37.2 |                         0   |
| contraction_quality | 40-50    |      606 |            0 |              nan |        nan |             0.89 |              46.2 |          40.9 |                38.8 |                         0   |
| contraction_quality | 50-60    |      812 |            0 |              nan |        nan |             0.86 |              59   |          28   |                38.7 |                       100   |
| contraction_quality | <30      |      364 |            0 |              nan |        nan |            -0.75 |              34.3 |          51.3 |                43.1 |                         0   |
| contraction_quality | >=60     |      620 |            0 |              nan |        nan |            -0.18 |              75.2 |          21.1 |                41.9 |                       100   |
| volume_ratio        | 0.8-1.0x |      568 |            0 |              nan |        nan |             2.14 |              46.3 |          37.5 |                 0   |                        50.7 |
| volume_ratio        | 1.0-1.2x |      395 |            0 |              nan |        nan |             1.68 |              49.9 |          33.2 |                 0   |                        51.4 |
| volume_ratio        | <0.8x    |      731 |            0 |              nan |        nan |             0.96 |              38.7 |          42   |                 0   |                        50.2 |
| volume_ratio        | >=1.2x   |     1119 |            0 |              nan |        nan |            -0.63 |              67.6 |          27.9 |               100   |                        51.3 |
| distance_from_21ema | 3-5%     |      488 |            0 |              nan |        nan |             0.45 |              56.4 |          33   |                32.6 |                        56.8 |
| distance_from_21ema | 5-8%     |      455 |            0 |              nan |        nan |             0.65 |              63.3 |          32.2 |                44.2 |                        53.6 |
| distance_from_21ema | 8-12%    |      335 |            0 |              nan |        nan |            -0.12 |              69.6 |          28.8 |                55.5 |                        44.5 |
| distance_from_21ema | <=3%     |     1114 |            0 |              nan |        nan |             1.29 |              32.9 |          38.3 |                21.4 |                        52.3 |
| distance_from_21ema | >12%     |      421 |            0 |              nan |        nan |            -0.14 |              80   |          32.3 |                79.6 |                        42.5 |
| risk_pct            | 3-5%     |      738 |            0 |              nan |        nan |             1    |              46.7 |          30.2 |                28   |                        51.6 |
| risk_pct            | 5-8%     |      579 |            0 |              nan |        nan |             2.25 |              56.3 |          27.9 |                48.2 |                        45.3 |
| risk_pct            | 8-12%    |      272 |            0 |              nan |        nan |             0.05 |              60.3 |          28.2 |                68   |                        50   |
| risk_pct            | <=3%     |      857 |            0 |              nan |        nan |             0.96 |              50.4 |          46.6 |                20.8 |                        57.4 |
| risk_pct            | >12%     |      186 |            0 |              nan |        nan |            -1.87 |              69.9 |          23.8 |                88.7 |                        47.8 |
| risk_pct            | MISSING  |      181 |            0 |              nan |        nan |            -2.01 |              56.9 |         nan   |                58   |                        39.8 |
| range_break         | FALSE    |     1313 |            0 |              nan |        nan |             1.18 |               0   |          46.1 |                27.6 |                        37.1 |
| range_break         | TRUE     |     1500 |            0 |              nan |        nan |             0.13 |             100   |          23.6 |                50.5 |                        63   |
| custom_rs_rating    | 50-70    |      623 |            0 |              nan |        nan |             1.09 |              53.9 |          33.3 |                28.7 |                        56   |
| custom_rs_rating    | 70-90    |     1019 |            0 |              nan |        nan |             0.99 |              53.9 |          35.3 |                42   |                        48.4 |
| custom_rs_rating    | <50      |      445 |            0 |              nan |        nan |             0.53 |              47   |          32   |                24.5 |                        54.4 |
| custom_rs_rating    | >=90     |      712 |            0 |              nan |        nan |            -0.01 |              55.3 |          36.9 |                55.1 |                        47.8 |
| custom_rs_rating    | MISSING  |       14 |            0 |              nan |        nan |             1.82 |              85.7 |          23.1 |                78.6 |                        57.1 |
| rr_pass             | FALSE    |     1648 |            0 |              nan |        nan |             0.74 |              59.6 |           0   |                39.9 |                        58.6 |
| rr_pass             | MISSING  |      293 |            0 |              nan |        nan |            -2.06 |              73   |         nan   |                70.6 |                        49.1 |
| rr_pass             | TRUE     |      872 |            0 |              nan |        nan |             1.59 |              34.7 |         100   |                29.1 |                        37   |
| vol_gate            | FALSE    |     1694 |            0 |              nan |        nan |             1.5  |              43.9 |          38.4 |                 0   |                        50.6 |
| vol_gate            | TRUE     |     1119 |            0 |              nan |        nan |            -0.63 |              67.6 |          27.9 |               100   |                        51.3 |
| contraction_gate    | FALSE    |     1381 |            0 |              nan |        nan |             0.92 |              40.2 |          44.6 |                39.5 |                         0   |
| contraction_gate    | TRUE     |     1432 |            0 |              nan |        nan |             0.42 |              66   |          25.1 |                40.1 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
