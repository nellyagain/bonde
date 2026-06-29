# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 12653
- SLINGSHOT signal rows: 2973
- Active `setup_family=SLINGSHOT` rows: 2382
- Precedence-absorbed SLINGSHOT signal rows: 591

## Gate-observation counts
- Range-break true: 1620 / 2973
- Contraction quality ≥ 50: 1537 / 2973
- Volume ratio ≥ 1.2x: 1264 / 2973
- `custom_rs_rating` ≥ 70: 1842 / 2973
- R:R ≥ 2: 890 / 2973
- > 8% above 21EMA: 821 / 2973
- Resolved outcomes available: 0 / 2973

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
| TRIN     | 2026-06-26    | SLINGSHOT      | True             |                  74.3291 |          1.02211  |                    52 |                0.976907 |        1.5205 |      1.3269   | False                 |             nan |
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

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      425 |            0 |              nan |        nan |             2.68 |              36.7 |          42.9 |                39.3 |                         0   |
| contraction_quality | 40-50    |      638 |            0 |              nan |        nan |             0.58 |              46.9 |          39.5 |                41.1 |                         0   |
| contraction_quality | 50-60    |      862 |            0 |              nan |        nan |             0.84 |              59.5 |          27.3 |                41.8 |                       100   |
| contraction_quality | <30      |      373 |            0 |              nan |        nan |            -0.49 |              35.7 |          50.2 |                44.5 |                         0   |
| contraction_quality | >=60     |      675 |            0 |              nan |        nan |             0.29 |              76.9 |          19.9 |                45.8 |                       100   |
| volume_ratio        | 0.8-1.0x |      570 |            0 |              nan |        nan |             1.74 |              46.5 |          37.6 |                 0   |                        50.7 |
| volume_ratio        | 1.0-1.2x |      403 |            0 |              nan |        nan |             1.52 |              49.6 |          33.2 |                 0   |                        52.1 |
| volume_ratio        | <0.8x    |      736 |            0 |              nan |        nan |             0.99 |              38.7 |          41.7 |                 0   |                        50.1 |
| volume_ratio        | >=1.2x   |     1264 |            0 |              nan |        nan |            -0.18 |              68.8 |          25.6 |               100   |                        52.9 |
| distance_from_21ema | 3-5%     |      516 |            0 |              nan |        nan |             0.5  |              57.4 |          31.6 |                35.7 |                        58.1 |
| distance_from_21ema | 5-8%     |      482 |            0 |              nan |        nan |             1.08 |              64.9 |          30.9 |                46.9 |                        55.4 |
| distance_from_21ema | 8-12%    |      365 |            0 |              nan |        nan |             0.35 |              71.8 |          26.5 |                58.9 |                        46.6 |
| distance_from_21ema | <=3%     |     1154 |            0 |              nan |        nan |             1.21 |              32.8 |          37.9 |                23.3 |                        52.3 |
| distance_from_21ema | >12%     |      456 |            0 |              nan |        nan |            -0.21 |              81.1 |          30.2 |                81.1 |                        43   |
| risk_pct            | 3-5%     |      775 |            0 |              nan |        nan |             1.09 |              48.1 |          28.8 |                31   |                        52.8 |
| risk_pct            | 5-8%     |      631 |            0 |              nan |        nan |             2.79 |              58.2 |          26.2 |                51.8 |                        46.4 |
| risk_pct            | 8-12%    |      309 |            0 |              nan |        nan |            -0.28 |              62.8 |          25.9 |                71.8 |                        51.8 |
| risk_pct            | <=3%     |      881 |            0 |              nan |        nan |             0.66 |              50.3 |          46.5 |                22.1 |                        57.7 |
| risk_pct            | >12%     |      196 |            0 |              nan |        nan |            -1.43 |              71.4 |          22.9 |                89.3 |                        48.5 |
| risk_pct            | MISSING  |      181 |            0 |              nan |        nan |            -2    |              56.9 |         nan   |                58   |                        39.8 |
| range_break         | FALSE    |     1353 |            0 |              nan |        nan |             1.05 |               0   |          45.5 |                29.1 |                        37.3 |
| range_break         | TRUE     |     1620 |            0 |              nan |        nan |             0.44 |             100   |          22.2 |                53.7 |                        63.7 |
| custom_rs_rating    | 50-70    |      646 |            0 |              nan |        nan |             1.14 |              54.8 |          32.7 |                30.5 |                        56.8 |
| custom_rs_rating    | 70-90    |     1090 |            0 |              nan |        nan |             0.81 |              55   |          33.7 |                45.2 |                        49.5 |
| custom_rs_rating    | <50      |      470 |            0 |              nan |        nan |             0.95 |              48.1 |          30.8 |                27.9 |                        54.9 |
| custom_rs_rating    | >=90     |      752 |            0 |              nan |        nan |             0.27 |              56.8 |          35   |                57.3 |                        48.3 |
| custom_rs_rating    | MISSING  |       15 |            0 |              nan |        nan |            -0.83 |              86.7 |          28.6 |                80   |                        60   |
| rr_pass             | FALSE    |     1781 |            0 |              nan |        nan |             0.85 |              61   |           0   |                43.8 |                        59   |
| rr_pass             | MISSING  |      302 |            0 |              nan |        nan |            -1.75 |              73.8 |         nan   |                71.5 |                        50.7 |
| rr_pass             | TRUE     |      890 |            0 |              nan |        nan |             1.47 |              34.8 |         100   |                30.1 |                        37.5 |
| vol_gate            | FALSE    |     1709 |            0 |              nan |        nan |             1.35 |              43.9 |          38.3 |                 0   |                        50.8 |
| vol_gate            | TRUE     |     1264 |            0 |              nan |        nan |            -0.18 |              68.8 |          25.6 |               100   |                        52.9 |
| contraction_gate    | FALSE    |     1436 |            0 |              nan |        nan |             0.88 |              40.9 |          43.2 |                41.4 |                         0   |
| contraction_gate    | TRUE     |     1537 |            0 |              nan |        nan |             0.61 |              67.1 |          24.1 |                43.5 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
