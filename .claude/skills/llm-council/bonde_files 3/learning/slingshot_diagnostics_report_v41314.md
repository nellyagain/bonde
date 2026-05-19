# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 3491
- SLINGSHOT signal rows: 290
- Active `setup_family=SLINGSHOT` rows: 216
- Precedence-absorbed SLINGSHOT signal rows: 74

## Gate-observation counts
- Range-break true: 149 / 290
- Contraction quality ≥ 50: 123 / 290
- Volume ratio ≥ 1.2x: 136 / 290
- `custom_rs_rating` ≥ 70: 190 / 290
- R:R ≥ 2: 45 / 290
- > 8% above 21EMA: 110 / 290
- Resolved outcomes available: 0 / 290

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
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |    nan        | False                 |             nan |
| STRA     | 2026-05-18    | SLINGSHOT      | True             |                  70.6048 |          0.838977 |                    31 |                2.23565  |        4.3761 |      1.10112  | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| SEPN     | 2026-05-14    | SLINGSHOT      | True             |                  69.5089 |          1.80142  |                    89 |               13.951    |      nan      |    nan        | False                 |             nan |
| URI      | 2026-05-14    | SLINGSHOT      | True             |                  69.2132 |          0.651686 |                    69 |                6.61549  |      nan      |    nan        | False                 |             nan |
| PEN      | 2026-05-18    | SLINGSHOT      | True             |                  68.164  |          0.735292 |                    48 |                0.276773 |        1.0935 |      0.219572 | False                 |             nan |
| PHVS     | 2026-05-13    | SLINGSHOT      | True             |                  68.0884 |          0.86167  |                    85 |               10.7527   |      nan      |    nan        | False                 |             nan |
| MASI     | 2026-05-18    | SLINGSHOT      | True             |                  68.0289 |          1.28137  |                    51 |                0.264313 |        0.3241 |      0.482755 | False                 |             nan |
| NSC      | 2026-05-14    | SLINGSHOT      | True             |                  67.7412 |          0.471863 |                    59 |                2.35073  |      nan      |    nan        | False                 |             nan |
| VEON     | 2026-05-13    | EP_ACTIVE      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| VEON     | 2026-05-13    | SLINGSHOT      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| HIG      | 2026-05-18    | SLINGSHOT      | True             |                  66.1638 |          0.820699 |                    35 |                1.18642  |        2.5965 |      0.856546 | False                 |             nan |
| TYRA     | 2026-05-13    | SLINGSHOT      | True             |                  65.9616 |          0.566367 |                    94 |                3.16003  |      nan      |    nan        | False                 |             nan |
| TAL      | 2026-05-13    | SLINGSHOT      | True             |                  65.8323 |          1.52867  |                    48 |                2.04237  |      nan      |    nan        | False                 |             nan |
| AVA      | 2026-05-14    | SLINGSHOT      | True             |                  65.7782 |          0.594795 |                    38 |                0.687401 |      nan      |    nan        | False                 |             nan |
| SEDG     | 2026-05-14    | SLINGSHOT      | True             |                  64.9573 |          1.61388  |                    93 |               16.726    |      nan      |    nan        | False                 |             nan |
| PFG      | 2026-05-18    | SLINGSHOT      | True             |                  64.1279 |          0.786612 |                    65 |                3.17405  |        2.4012 |      0.894314 | False                 |             nan |
| LAUR     | 2026-05-18    | SLINGSHOT      | True             |                  64.0081 |          0.331115 |                    64 |                1.58123  |        2.7551 |      1.5055   | False                 |             nan |
| SHMD     | 2026-05-14    | SLINGSHOT      | True             |                  63.9266 |          1.34828  |                    87 |               10.1579   |      nan      |    nan        | False                 |             nan |
| SPIR     | 2026-05-15    | ACTIVE_BURST   | True             |                  62.4618 |          1.66785  |                    95 |               12.5805   |       13.4474 |      1.04364  | False                 |             nan |
| SPIR     | 2026-05-15    | SLINGSHOT      | True             |                  62.4618 |          1.66785  |                    95 |               12.5805   |       13.4474 |      1.04364  | False                 |             nan |
| AVGO     | 2026-05-14    | SLINGSHOT      | True             |                  60.9333 |          0.797759 |                    86 |                7.22288  |      nan      |    nan        | False                 |             nan |
| AVGO     | 2026-05-14    | EP9M           | True             |                  60.9333 |          0.797759 |                    86 |                7.22288  |      nan      |    nan        | False                 |             nan |
| GLRE     | 2026-05-18    | SLINGSHOT      | True             |                  60.6727 |          0.714056 |                    76 |                0.64402  |        3.2579 |      1.50847  | False                 |             nan |
| BNL      | 2026-05-18    | SLINGSHOT      | True             |                  60.4606 |          0.409417 |                    59 |                1.94616  |        1.6778 |      1.27942  | False                 |             nan |
| DEA      | 2026-05-18    | SLINGSHOT      | True             |                  59.6594 |          0.749912 |                    44 |                2.31387  |        2.5316 |      1.45     | False                 |             nan |
| JHG      | 2026-05-18    | SLINGSHOT      | True             |                  59.544  |          0.798582 |                    66 |                0.330406 |        0.3085 |      0.250006 | False                 |             nan |
| MAR      | 2026-05-18    | SLINGSHOT      | True             |                  59.4166 |          0.957039 |                    62 |                1.29806  |        2.7241 |      0.636727 | False                 |             nan |
| BE       | 2026-05-14    | SLINGSHOT      | True             |                  59.2784 |          0.762512 |                    99 |               18.0669   |      nan      |    nan        | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |       43 |            0 |              nan |        nan |              nan |              32.6 |          46.2 |                32.6 |                         0   |
| contraction_quality | 40-50    |       64 |            0 |              nan |        nan |              nan |              45.3 |          56   |                45.3 |                         0   |
| contraction_quality | 50-60    |       80 |            0 |              nan |        nan |              nan |              67.5 |          43.8 |                61.3 |                       100   |
| contraction_quality | <30      |       60 |            0 |              nan |        nan |              nan |              43.3 |          27.3 |                46.7 |                         0   |
| contraction_quality | >=60     |       43 |            0 |              nan |        nan |              nan |              60.5 |          26.3 |                37.2 |                       100   |
| volume_ratio        | 0.8-1.0x |       48 |            0 |              nan |        nan |              nan |              35.4 |          50   |                 0   |                        29.2 |
| volume_ratio        | 1.0-1.2x |       26 |            0 |              nan |        nan |              nan |              26.9 |          44.4 |                 0   |                        23.1 |
| volume_ratio        | <0.8x    |       80 |            0 |              nan |        nan |              nan |              37.5 |          34.8 |                 0   |                        47.5 |
| volume_ratio        | >=1.2x   |      136 |            0 |              nan |        nan |              nan |              69.9 |          40.6 |               100   |                        47.8 |
| distance_from_21ema | 3-5%     |       34 |            0 |              nan |        nan |              nan |              47.1 |          21.4 |                32.4 |                        50   |
| distance_from_21ema | 5-8%     |       48 |            0 |              nan |        nan |              nan |              64.6 |          40   |                50   |                        43.8 |
| distance_from_21ema | 8-12%    |       48 |            0 |              nan |        nan |              nan |              66.7 |          50   |                66.7 |                        43.8 |
| distance_from_21ema | <=3%     |       98 |            0 |              nan |        nan |              nan |              20.4 |          45.5 |                15.3 |                        42.9 |
| distance_from_21ema | >12%     |       62 |            0 |              nan |        nan |              nan |              80.6 |          30.8 |                87.1 |                        35.5 |
| risk_pct            | 3-5%     |       31 |            0 |              nan |        nan |              nan |              29   |          32.3 |                19.4 |                        51.6 |
| risk_pct            | 5-8%     |       10 |            0 |              nan |        nan |              nan |              60   |          30   |                60   |                        20   |
| risk_pct            | 8-12%    |        6 |            0 |              nan |        nan |              nan |              83.3 |          33.3 |                66.7 |                         0   |
| risk_pct            | <=3%     |       54 |            0 |              nan |        nan |              nan |              33.3 |          51.9 |                11.1 |                        46.3 |
| risk_pct            | >12%     |       10 |            0 |              nan |        nan |              nan |              90   |          20   |               100   |                        80   |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |              nan |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      141 |            0 |              nan |        nan |              nan |               0   |          48.4 |                29.1 |                        30.5 |
| range_break         | TRUE     |      149 |            0 |              nan |        nan |              nan |             100   |          29.8 |                63.8 |                        53.7 |
| custom_rs_rating    | 50-70    |       61 |            0 |              nan |        nan |              nan |              44.3 |          50   |                31.1 |                        55.7 |
| custom_rs_rating    | 70-90    |      123 |            0 |              nan |        nan |              nan |              52.8 |          38.5 |                53.7 |                        35   |
| custom_rs_rating    | <50      |       39 |            0 |              nan |        nan |              nan |              46.2 |          38.5 |                12.8 |                        38.5 |
| custom_rs_rating    | >=90     |       67 |            0 |              nan |        nan |              nan |              58.2 |          28.6 |                68.7 |                        46.3 |
| rr_pass             | FALSE    |       66 |            0 |              nan |        nan |              nan |              50   |           0   |                28.8 |                        48.5 |
| rr_pass             | MISSING  |      179 |            0 |              nan |        nan |              nan |              57   |         nan   |                58.1 |                        40.2 |
| rr_pass             | TRUE     |       45 |            0 |              nan |        nan |              nan |              31.1 |         100   |                28.9 |                        42.2 |
| vol_gate            | FALSE    |      154 |            0 |              nan |        nan |              nan |              35.1 |          40.5 |                 0   |                        37.7 |
| vol_gate            | TRUE     |      136 |            0 |              nan |        nan |              nan |              69.9 |          40.6 |               100   |                        47.8 |
| contraction_gate    | FALSE    |      167 |            0 |              nan |        nan |              nan |              41.3 |          43.3 |                42.5 |                         0   |
| contraction_gate    | TRUE     |      123 |            0 |              nan |        nan |              nan |              65   |          37.3 |                52.8 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
