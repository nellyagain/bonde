# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 3754
- SLINGSHOT signal rows: 337
- Active `setup_family=SLINGSHOT` rows: 256
- Precedence-absorbed SLINGSHOT signal rows: 81

## Gate-observation counts
- Range-break true: 169 / 337
- Contraction quality ≥ 50: 153 / 337
- Volume ratio ≥ 1.2x: 152 / 337
- `custom_rs_rating` ≥ 70: 209 / 337
- R:R ≥ 2: 62 / 337
- > 8% above 21EMA: 118 / 337
- Resolved outcomes available: 0 / 337

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
| MRK      | 2026-05-19    | SLINGSHOT      | True             |                  75.6409 |          0.561273 |                    67 |                0.819765 |        2.5804 |      0.70707  | False                 |             nan |
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |    nan        | False                 |             nan |
| SHEN     | 2026-05-19    | SLINGSHOT      | True             |                  73.5563 |          1.02562  |                    81 |                3.08042  |        2.3678 |      2.22278  | False                 |             nan |
| IFS      | 2026-05-19    | SLINGSHOT      | True             |                  70.9804 |          1.60272  |                    58 |                2.11166  |        4.0291 |      0.644563 | False                 |             nan |
| STRA     | 2026-05-18    | SLINGSHOT      | True             |                  70.6048 |          0.838977 |                    31 |                2.23565  |        4.3761 |      1.10112  | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |    nan        | False                 |             nan |
| SEPN     | 2026-05-14    | SLINGSHOT      | True             |                  69.5089 |          1.80142  |                    89 |               13.951    |      nan      |    nan        | False                 |             nan |
| URI      | 2026-05-14    | SLINGSHOT      | True             |                  69.2132 |          0.651686 |                    69 |                6.61549  |      nan      |    nan        | False                 |             nan |
| PEN      | 2026-05-18    | SLINGSHOT      | True             |                  68.164  |          0.735292 |                    48 |                0.276773 |        1.0935 |      0.219572 | False                 |             nan |
| PHVS     | 2026-05-13    | SLINGSHOT      | True             |                  68.0884 |          0.86167  |                    85 |               10.7527   |      nan      |    nan        | False                 |             nan |
| MASI     | 2026-05-18    | SLINGSHOT      | True             |                  68.0289 |          1.28137  |                    51 |                0.264313 |        0.3241 |      0.482755 | False                 |             nan |
| NSC      | 2026-05-14    | SLINGSHOT      | True             |                  67.7412 |          0.471863 |                    59 |                2.35073  |      nan      |    nan        | False                 |             nan |
| ESS      | 2026-05-19    | SLINGSHOT      | True             |                  67.6196 |          0.742452 |                    38 |                2.96872  |        1.3087 |      2.7535   | False                 |             nan |
| VEON     | 2026-05-13    | EP_ACTIVE      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| VEON     | 2026-05-13    | SLINGSHOT      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |    nan        | False                 |             nan |
| HIG      | 2026-05-18    | SLINGSHOT      | True             |                  66.1638 |          0.820699 |                    35 |                1.18642  |        2.5965 |      0.856546 | False                 |             nan |
| TYRA     | 2026-05-13    | SLINGSHOT      | True             |                  65.9616 |          0.566367 |                    94 |                3.16003  |      nan      |    nan        | False                 |             nan |
| AAT      | 2026-05-19    | SLINGSHOT      | True             |                  65.9091 |          0.575003 |                    53 |                2.46504  |        1.3634 |      2.20689  | False                 |             nan |
| TAL      | 2026-05-13    | SLINGSHOT      | True             |                  65.8323 |          1.52867  |                    48 |                2.04237  |      nan      |    nan        | False                 |             nan |
| AVA      | 2026-05-14    | SLINGSHOT      | True             |                  65.7782 |          0.594795 |                    38 |                0.687401 |      nan      |    nan        | False                 |             nan |
| SEDG     | 2026-05-14    | SLINGSHOT      | True             |                  64.9573 |          1.61388  |                    93 |               16.726    |      nan      |    nan        | False                 |             nan |
| PFG      | 2026-05-18    | SLINGSHOT      | True             |                  64.1279 |          0.786612 |                    65 |                3.17405  |        2.4012 |      0.894314 | False                 |             nan |
| LAUR     | 2026-05-18    | SLINGSHOT      | True             |                  64.0081 |          0.331115 |                    64 |                1.58123  |        2.7551 |      1.5055   | False                 |             nan |
| SHMD     | 2026-05-14    | SLINGSHOT      | True             |                  63.9266 |          1.34828  |                    87 |               10.1579   |      nan      |    nan        | False                 |             nan |
| SPIR     | 2026-05-15    | ACTIVE_BURST   | True             |                  62.4618 |          1.66785  |                    95 |               12.5805   |       13.4474 |      1.04364  | False                 |             nan |
| SPIR     | 2026-05-15    | SLINGSHOT      | True             |                  62.4618 |          1.66785  |                    95 |               12.5805   |       13.4474 |      1.04364  | False                 |             nan |
| NNN      | 2026-05-19    | SLINGSHOT      | True             |                  61.7085 |          1.08354  |                    44 |                1.56759  |        1.9248 |      1.10392  | False                 |             nan |
| CGCT     | 2026-05-19    | SLINGSHOT      | True             |                  61.561  |          6.99404  |                   nan |                0.539081 |        0.4798 |      0.199985 | False                 |             nan |
| AVGO     | 2026-05-14    | SLINGSHOT      | True             |                  60.9333 |          0.797759 |                    86 |                7.22288  |      nan      |    nan        | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |       46 |            0 |              nan |        nan |              nan |              30.4 |          50   |                32.6 |                         0   |
| contraction_quality | 40-50    |       68 |            0 |              nan |        nan |              nan |              42.6 |          58.6 |                42.6 |                         0   |
| contraction_quality | 50-60    |       98 |            0 |              nan |        nan |              nan |              65.3 |          38   |                56.1 |                       100   |
| contraction_quality | <30      |       70 |            0 |              nan |        nan |              nan |              41.4 |          25   |                47.1 |                         0   |
| contraction_quality | >=60     |       55 |            0 |              nan |        nan |              nan |              60   |          32.3 |                36.4 |                       100   |
| volume_ratio        | 0.8-1.0x |       53 |            0 |              nan |        nan |              nan |              34   |          48.3 |                 0   |                        32.1 |
| volume_ratio        | 1.0-1.2x |       32 |            0 |              nan |        nan |              nan |              34.4 |          46.7 |                 0   |                        25   |
| volume_ratio        | <0.8x    |      100 |            0 |              nan |        nan |              nan |              38   |          39.4 |                 0   |                        53   |
| volume_ratio        | >=1.2x   |      152 |            0 |              nan |        nan |              nan |              67.1 |          31.2 |               100   |                        49.3 |
| distance_from_21ema | 3-5%     |       38 |            0 |              nan |        nan |              nan |              44.7 |          27.8 |                34.2 |                        47.4 |
| distance_from_21ema | 5-8%     |       50 |            0 |              nan |        nan |              nan |              64   |          41.7 |                50   |                        46   |
| distance_from_21ema | 8-12%    |       51 |            0 |              nan |        nan |              nan |              64.7 |          45.5 |                66.7 |                        41.2 |
| distance_from_21ema | <=3%     |      131 |            0 |              nan |        nan |              nan |              24.4 |          43.4 |                17.6 |                        50.4 |
| distance_from_21ema | >12%     |       67 |            0 |              nan |        nan |              nan |              82.1 |          22.2 |                85.1 |                        37.3 |
| risk_pct            | 3-5%     |       41 |            0 |              nan |        nan |              nan |              26.8 |          31.7 |                24.4 |                        46.3 |
| risk_pct            | 5-8%     |       16 |            0 |              nan |        nan |              nan |              50   |          25   |                50   |                        25   |
| risk_pct            | 8-12%    |       10 |            0 |              nan |        nan |              nan |              80   |          20   |                80   |                        30   |
| risk_pct            | <=3%     |       81 |            0 |              nan |        nan |              nan |              38.3 |          50.6 |                14.8 |                        58   |
| risk_pct            | >12%     |       10 |            0 |              nan |        nan |              nan |              90   |          20   |               100   |                        80   |
| risk_pct            | MISSING  |      179 |            0 |              nan |        nan |              nan |              57   |         nan   |                58.1 |                        40.2 |
| range_break         | FALSE    |      168 |            0 |              nan |        nan |              nan |               0   |          48.4 |                29.8 |                        33.3 |
| range_break         | TRUE     |      169 |            0 |              nan |        nan |              nan |             100   |          26.9 |                60.4 |                        57.4 |
| custom_rs_rating    | 50-70    |       76 |            0 |              nan |        nan |              nan |              42.1 |          44.7 |                32.9 |                        59.2 |
| custom_rs_rating    | 70-90    |      137 |            0 |              nan |        nan |              nan |              51.8 |          37.7 |                53.3 |                        35   |
| custom_rs_rating    | <50      |       51 |            0 |              nan |        nan |              nan |              45.1 |          42.1 |                11.8 |                        47.1 |
| custom_rs_rating    | >=90     |       72 |            0 |              nan |        nan |              nan |              58.3 |          26.3 |                65.3 |                        48.6 |
| custom_rs_rating    | MISSING  |        1 |            0 |              nan |        nan |              nan |             100   |           0   |               100   |                       100   |
| rr_pass             | FALSE    |       96 |            0 |              nan |        nan |              nan |              51   |           0   |                34.4 |                        54.2 |
| rr_pass             | MISSING  |      179 |            0 |              nan |        nan |              nan |              57   |         nan   |                58.1 |                        40.2 |
| rr_pass             | TRUE     |       62 |            0 |              nan |        nan |              nan |              29   |         100   |                24.2 |                        46.8 |
| vol_gate            | FALSE    |      185 |            0 |              nan |        nan |              nan |              36.2 |          42.7 |                 0   |                        42.2 |
| vol_gate            | TRUE     |      152 |            0 |              nan |        nan |              nan |              67.1 |          31.2 |               100   |                        49.3 |
| contraction_gate    | FALSE    |      184 |            0 |              nan |        nan |              nan |              39.1 |          42.9 |                41.8 |                         0   |
| contraction_gate    | TRUE     |      153 |            0 |              nan |        nan |              nan |              63.4 |          35.8 |                49   |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
