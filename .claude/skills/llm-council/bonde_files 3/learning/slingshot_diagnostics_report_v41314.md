# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 6320
- SLINGSHOT signal rows: 1150
- Active `setup_family=SLINGSHOT` rows: 893
- Precedence-absorbed SLINGSHOT signal rows: 257

## Gate-observation counts
- Range-break true: 495 / 1150
- Contraction quality ≥ 50: 553 / 1150
- Volume ratio ≥ 1.2x: 468 / 1150
- `custom_rs_rating` ≥ 70: 766 / 1150
- R:R ≥ 2: 357 / 1150
- > 8% above 21EMA: 352 / 1150
- Resolved outcomes available: 0 / 1150

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
| CYTK     | 2026-05-20    | SLINGSHOT      | True             |                  69.9326 |          0.911393 |                    89 |                8.6242   |        3.5642 |      1.97163  | False                 |             nan |
| KALV     | 2026-05-29    | SLINGSHOT      | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| KALV     | 2026-05-29    | PAUSE          | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| KALV     | 2026-05-29    | ANTICIPATION   | True             |                  69.7232 |          0.344292 |                    92 |                3.91431  |        0.2977 |      0.249982 | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |      160 |            0 |              nan |        nan |             3.58 |              25.6 |          44.6 |                37.5 |                         0   |
| contraction_quality | 40-50    |      237 |            0 |              nan |        nan |             1.57 |              35.9 |          37.4 |                37.6 |                         0   |
| contraction_quality | 50-60    |      319 |            0 |              nan |        nan |             2.2  |              52.4 |          32.1 |                43.6 |                       100   |
| contraction_quality | <30      |      200 |            0 |              nan |        nan |             1.02 |              27.5 |          50.6 |                47   |                         0   |
| contraction_quality | >=60     |      234 |            0 |              nan |        nan |             1    |              62.8 |          28.2 |                36.8 |                       100   |
| volume_ratio        | 0.8-1.0x |      196 |            0 |              nan |        nan |             2.51 |              32.7 |          37.8 |                 0   |                        47.4 |
| volume_ratio        | 1.0-1.2x |      124 |            0 |              nan |        nan |             4.21 |              34.7 |          38.3 |                 0   |                        45.2 |
| volume_ratio        | <0.8x    |      362 |            0 |              nan |        nan |             1.49 |              28.2 |          40.2 |                 0   |                        49.4 |
| volume_ratio        | >=1.2x   |      468 |            0 |              nan |        nan |             1.29 |              61.1 |          33.6 |               100   |                        48.1 |
| distance_from_21ema | 3-5%     |      167 |            0 |              nan |        nan |             0.63 |              35.9 |          29.9 |                27.5 |                        51.5 |
| distance_from_21ema | 5-8%     |      171 |            0 |              nan |        nan |             1.47 |              53.8 |          36.1 |                49.1 |                        49.1 |
| distance_from_21ema | 8-12%    |      142 |            0 |              nan |        nan |            -0.06 |              53.5 |          41.2 |                62   |                        50.7 |
| distance_from_21ema | <=3%     |      460 |            0 |              nan |        nan |             1.9  |              23   |          35.7 |                18.3 |                        48.7 |
| distance_from_21ema | >12%     |      210 |            0 |              nan |        nan |             4.19 |              76.7 |          46.4 |                79   |                        41.4 |
| risk_pct            | 3-5%     |      279 |            0 |              nan |        nan |             2.59 |              29   |          30.1 |                22.6 |                        50.2 |
| risk_pct            | 5-8%     |      208 |            0 |              nan |        nan |             4.38 |              39.4 |          38.8 |                51.4 |                        37.5 |
| risk_pct            | 8-12%    |      124 |            0 |              nan |        nan |             5.74 |              58.1 |          35.5 |                69.4 |                        38.7 |
| risk_pct            | <=3%     |      286 |            0 |              nan |        nan |             0.51 |              35.7 |          44.1 |                15   |                        60.8 |
| risk_pct            | >12%     |       74 |            0 |              nan |        nan |             5.45 |              75.7 |          34.8 |                87.8 |                        55.4 |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |            -2.02 |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      655 |            0 |              nan |        nan |             2.24 |               0   |          42.4 |                27.8 |                        36.5 |
| range_break         | TRUE     |      495 |            0 |              nan |        nan |             1.34 |             100   |          29.2 |                57.8 |                        63.4 |
| custom_rs_rating    | 50-70    |      238 |            0 |              nan |        nan |             1.37 |              36.1 |          31.6 |                28.2 |                        52.5 |
| custom_rs_rating    | 70-90    |      452 |            0 |              nan |        nan |             1.38 |              44.2 |          39.1 |                43.8 |                        45.1 |
| custom_rs_rating    | <50      |      142 |            0 |              nan |        nan |             0.76 |              35.2 |          25.6 |                18.3 |                        52.1 |
| custom_rs_rating    | >=90     |      314 |            0 |              nan |        nan |             3.4  |              49.7 |          44.7 |                55.1 |                        47.1 |
| custom_rs_rating    | MISSING  |        4 |            0 |              nan |        nan |             3.29 |              75   |          50   |               100   |                        50   |
| rr_pass             | FALSE    |      604 |            0 |              nan |        nan |             2.93 |              44.9 |           0   |                38.9 |                        54.5 |
| rr_pass             | MISSING  |      189 |            0 |              nan |        nan |            -2.02 |              59.3 |         nan   |                60.3 |                        42.3 |
| rr_pass             | TRUE     |      357 |            0 |              nan |        nan |             3.05 |              31.4 |         100   |                33.3 |                        40.3 |
| vol_gate            | FALSE    |      682 |            0 |              nan |        nan |             2.23 |              30.6 |          39.2 |                 0   |                        48.1 |
| vol_gate            | TRUE     |      468 |            0 |              nan |        nan |             1.29 |              61.1 |          33.6 |               100   |                        48.1 |
| contraction_gate    | FALSE    |      597 |            0 |              nan |        nan |             1.99 |              30.3 |          43.6 |                40.7 |                         0   |
| contraction_gate    | TRUE     |      553 |            0 |              nan |        nan |             1.73 |              56.8 |          30.4 |                40.7 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
