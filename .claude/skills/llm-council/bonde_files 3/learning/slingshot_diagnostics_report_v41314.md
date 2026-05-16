# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `skill_pack_candidate_outcomes`
- Input rows: 3208
- SLINGSHOT signal rows: 208
- Active `setup_family=SLINGSHOT` rows: 144
- Precedence-absorbed SLINGSHOT signal rows: 64

## Gate-observation counts
- Range-break true: 109 / 208
- Contraction quality ≥ 50: 82 / 208
- Volume ratio ≥ 1.2x: 114 / 208
- `custom_rs_rating` ≥ 70: 160 / 208
- R:R ≥ 2: 11 / 208
- > 8% above 21EMA: 95 / 208
- Resolved outcomes available: 0 / 208

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
| WKC      | 2026-05-14    | SLINGSHOT      | True             |                  75.3165 |          0.962545 |                    41 |                6.52633  |      nan      |     nan       | False                 |             nan |
| CSX      | 2026-05-14    | SLINGSHOT      | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |     nan       | False                 |             nan |
| CSX      | 2026-05-14    | EP9M           | True             |                  69.6711 |          1.21252  |                    72 |                3.48956  |      nan      |     nan       | False                 |             nan |
| SEPN     | 2026-05-14    | SLINGSHOT      | True             |                  69.5089 |          1.80142  |                    89 |               13.951    |      nan      |     nan       | False                 |             nan |
| URI      | 2026-05-14    | SLINGSHOT      | True             |                  69.2132 |          0.651686 |                    69 |                6.61549  |      nan      |     nan       | False                 |             nan |
| PHVS     | 2026-05-13    | SLINGSHOT      | True             |                  68.0884 |          0.86167  |                    85 |               10.7527   |      nan      |     nan       | False                 |             nan |
| NSC      | 2026-05-14    | SLINGSHOT      | True             |                  67.7412 |          0.471863 |                    59 |                2.35073  |      nan      |     nan       | False                 |             nan |
| VEON     | 2026-05-13    | EP_ACTIVE      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |     nan       | False                 |             nan |
| VEON     | 2026-05-13    | SLINGSHOT      | True             |                  67.4352 |          2.5048   |                    51 |               11.5813   |      nan      |     nan       | False                 |             nan |
| TYRA     | 2026-05-13    | SLINGSHOT      | True             |                  65.9616 |          0.566367 |                    94 |                3.16003  |      nan      |     nan       | False                 |             nan |
| TAL      | 2026-05-13    | SLINGSHOT      | True             |                  65.8323 |          1.52867  |                    48 |                2.04237  |      nan      |     nan       | False                 |             nan |
| AVA      | 2026-05-14    | SLINGSHOT      | True             |                  65.7782 |          0.594795 |                    38 |                0.687401 |      nan      |     nan       | False                 |             nan |
| SEDG     | 2026-05-14    | SLINGSHOT      | True             |                  64.9573 |          1.61388  |                    93 |               16.726    |      nan      |     nan       | False                 |             nan |
| SHMD     | 2026-05-14    | SLINGSHOT      | True             |                  63.9266 |          1.34828  |                    87 |               10.1579   |      nan      |     nan       | False                 |             nan |
| SPIR     | 2026-05-15    | ACTIVE_BURST   | True             |                  62.4273 |          1.66554  |                    95 |               12.5805   |       13.2763 |       1.05709 | False                 |             nan |
| SPIR     | 2026-05-15    | SLINGSHOT      | True             |                  62.4273 |          1.66554  |                    95 |               12.5805   |       13.2763 |       1.05709 | False                 |             nan |
| AVGO     | 2026-05-14    | SLINGSHOT      | True             |                  60.9333 |          0.797759 |                    86 |                7.22288  |      nan      |     nan       | False                 |             nan |
| AVGO     | 2026-05-14    | EP9M           | True             |                  60.9333 |          0.797759 |                    86 |                7.22288  |      nan      |     nan       | False                 |             nan |
| BE       | 2026-05-14    | SLINGSHOT      | True             |                  59.2784 |          0.762512 |                    99 |               18.0669   |      nan      |     nan       | False                 |             nan |
| MS       | 2026-05-13    | SLINGSHOT      | True             |                  58.8065 |          0.701249 |                    74 |                3.09424  |      nan      |     nan       | False                 |             nan |
| FIHL     | 2026-05-14    | ACTIVE_BURST   | True             |                  58.6581 |          2.44563  |                    72 |               12.4644   |      nan      |     nan       | False                 |             nan |
| FIHL     | 2026-05-14    | SLINGSHOT      | True             |                  58.6581 |          2.44563  |                    72 |               12.4644   |      nan      |     nan       | False                 |             nan |
| OUST     | 2026-05-13    | EP_SPIKE       | True             |                  57.8891 |          5.7851   |                    97 |               28.6284   |      nan      |     nan       | False                 |             nan |
| OUST     | 2026-05-13    | EP_SPIKE       | True             |                  57.8891 |          5.7851   |                    97 |               28.6284   |      nan      |     nan       | False                 |             nan |
| ONDS     | 2026-05-14    | EP_SPIKE       | True             |                  57.82   |          3.60324  |                    99 |               14.7406   |      nan      |     nan       | False                 |             nan |
| ONDS     | 2026-05-14    | EP_SPIKE       | True             |                  57.82   |          3.60324  |                    99 |               14.7406   |      nan      |     nan       | False                 |             nan |
| ONDS     | 2026-05-14    | EP_SPIKE       | True             |                  57.82   |          3.60324  |                    99 |               14.7406   |      nan      |     nan       | False                 |             nan |
| SRRK     | 2026-05-13    | DELAYED_EP     | True             |                  57.4959 |          1.06009  |                    76 |                5.11117  |      nan      |     nan       | False                 |             nan |
| SRRK     | 2026-05-13    | SLINGSHOT      | True             |                  57.4959 |          1.06009  |                    76 |                5.11117  |      nan      |     nan       | False                 |             nan |
| FENC     | 2026-05-14    | EP_SPIKE       | True             |                  56.9314 |         12.2663   |                    72 |               32.1204   |      nan      |     nan       | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |       35 |            0 |              nan |        nan |              nan |              34.3 |          80   |                40   |                         0   |
| contraction_quality | 40-50    |       45 |            0 |              nan |        nan |              nan |              51.1 |          33.3 |                51.1 |                         0   |
| contraction_quality | 50-60    |       51 |            0 |              nan |        nan |              nan |              76.5 |          66.7 |                70.6 |                       100   |
| contraction_quality | <30      |       46 |            0 |              nan |        nan |              nan |              37   |          37.5 |                50   |                         0   |
| contraction_quality | >=60     |       31 |            0 |              nan |        nan |              nan |              58.1 |           0   |                58.1 |                       100   |
| volume_ratio        | 0.8-1.0x |       33 |            0 |              nan |        nan |              nan |              33.3 |          55.6 |                 0   |                        21.2 |
| volume_ratio        | 1.0-1.2x |       21 |            0 |              nan |        nan |              nan |              33.3 |           0   |                 0   |                        23.8 |
| volume_ratio        | <0.8x    |       40 |            0 |              nan |        nan |              nan |              37.5 |          50   |                 0   |                        40   |
| volume_ratio        | >=1.2x   |      114 |            0 |              nan |        nan |              nan |              66.7 |          42.9 |               100   |                        47.4 |
| distance_from_21ema | 3-5%     |       23 |            0 |              nan |        nan |              nan |              52.2 |          66.7 |                39.1 |                        47.8 |
| distance_from_21ema | 5-8%     |       39 |            0 |              nan |        nan |              nan |              59   |           0   |                48.7 |                        46.2 |
| distance_from_21ema | 8-12%    |       41 |            0 |              nan |        nan |              nan |              61   |           0   |                65.9 |                        39   |
| distance_from_21ema | <=3%     |       51 |            0 |              nan |        nan |              nan |              13.7 |          43.8 |                25.5 |                        33.3 |
| distance_from_21ema | >12%     |       54 |            0 |              nan |        nan |              nan |              77.8 |          40   |                85.2 |                        37   |
| risk_pct            | 3-5%     |        4 |            0 |              nan |        nan |              nan |              25   |           0   |                 0   |                         0   |
| risk_pct            | 8-12%    |        2 |            0 |              nan |        nan |              nan |             100   |         100   |               100   |                         0   |
| risk_pct            | <=3%     |       17 |            0 |              nan |        nan |              nan |              11.8 |          52.9 |                11.8 |                        23.5 |
| risk_pct            | >12%     |        3 |            0 |              nan |        nan |              nan |             100   |           0   |               100   |                       100   |
| risk_pct            | MISSING  |      182 |            0 |              nan |        nan |              nan |              55.5 |         nan   |                58.8 |                        41.2 |
| range_break         | FALSE    |       99 |            0 |              nan |        nan |              nan |               0   |          44.4 |                38.4 |                        25.3 |
| range_break         | TRUE     |      109 |            0 |              nan |        nan |              nan |             100   |          37.5 |                69.7 |                        52.3 |
| custom_rs_rating    | 50-70    |       32 |            0 |              nan |        nan |              nan |              50   |           0   |                37.5 |                        43.8 |
| custom_rs_rating    | 70-90    |       98 |            0 |              nan |        nan |              nan |              54.1 |          57.1 |                57.1 |                        34.7 |
| custom_rs_rating    | <50      |       15 |            0 |              nan |        nan |              nan |              46.7 |          33.3 |                26.7 |                        33.3 |
| custom_rs_rating    | >=90     |       62 |            0 |              nan |        nan |              nan |              53.2 |          33.3 |                67.7 |                        46.8 |
| custom_rs_rating    | MISSING  |        1 |            0 |              nan |        nan |              nan |               0   |         nan   |                 0   |                         0   |
| rr_pass             | FALSE    |       15 |            0 |              nan |        nan |              nan |              33.3 |           0   |                26.7 |                        33.3 |
| rr_pass             | MISSING  |      182 |            0 |              nan |        nan |              nan |              55.5 |         nan   |                58.8 |                        41.2 |
| rr_pass             | TRUE     |       11 |            0 |              nan |        nan |              nan |              27.3 |         100   |                27.3 |                        18.2 |
| vol_gate            | FALSE    |       94 |            0 |              nan |        nan |              nan |              35.1 |          42.1 |                 0   |                        29.8 |
| vol_gate            | TRUE     |      114 |            0 |              nan |        nan |              nan |              66.7 |          42.9 |               100   |                        47.4 |
| contraction_gate    | FALSE    |      126 |            0 |              nan |        nan |              nan |              41.3 |          47.4 |                47.6 |                         0   |
| contraction_gate    | TRUE     |       82 |            0 |              nan |        nan |              nan |              69.5 |          28.6 |                65.9 |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
