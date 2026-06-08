# SLINGSHOT Diagnostics Report — v4.13.14

Monitoring only. No trading rules, tiers, gates, or precedence rules were changed.

## Source
- Source frame: `decision_outcomes`
- Input rows: 841
- SLINGSHOT signal rows: 146
- Active `setup_family=SLINGSHOT` rows: 146
- Precedence-absorbed SLINGSHOT signal rows: 0

## Missing core columns
- `slingshot_flag`

## Gate-observation counts
- Range-break true: 55 / 146
- Contraction quality ≥ 50: 71 / 146
- Volume ratio ≥ 1.2x: 0 / 146
- `custom_rs_rating` ≥ 70: 0 / 146
- R:R ≥ 2: 37 / 146
- > 8% above 21EMA: 0 / 146
- Resolved outcomes available: 0 / 146

## Metric sources
- `sg_contraction_quality`: `slingshot_contraction_quality`
- `sg_volume_ratio`: `missing`
- `sg_custom_rs_rating`: `missing`
- `sg_quarterly_rs_score`: `missing`
- `sg_distance_21ema_pct`: `missing`
- `sg_distance_200sma_pct`: `missing`
- `sg_risk_pct`: `missing`
- `sg_today_pct`: `day1_move_pct`
- `sg_rr_value`: `planned_rr`
- `sg_range_break`: `slingshot_range_break_flag`
- `sg_ret_5d_pct`: `ret_5d_close_pct`
- `sg_ret_10d_pct`: `ret_10d_close_pct`
- `sg_mfe_5d_r`: `missing`
- `sg_mae_5d_r`: `missing`

## Row-level diagnostic sample
| ticker   | signal_date   | setup_family   | primary_setup   | sg_range_break   |   sg_contraction_quality |   sg_volume_ratio |   sg_custom_rs_rating |   sg_distance_21ema_pct |   sg_risk_pct |   sg_rr_value | sg_outcome_resolved   |   sg_realized_r |
|:---------|:--------------|:---------------|:----------------|:-----------------|-------------------------:|------------------:|----------------------:|------------------------:|--------------:|--------------:|:----------------------|----------------:|
| TBRG     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   84.788 |               nan |                   nan |                     nan |           nan |      nan      | False                 |             nan |
| MAC      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   70.289 |               nan |                   nan |                     nan |           nan |        0.7538 | False                 |             nan |
| ARLP     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   69.325 |               nan |                   nan |                     nan |           nan |        0.4458 | False                 |             nan |
| PRK      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   66.873 |               nan |                   nan |                     nan |           nan |        1.2199 | False                 |             nan |
| IRM      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   66.834 |               nan |                   nan |                     nan |           nan |        1.3248 | False                 |             nan |
| CAH      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   66.603 |               nan |                   nan |                     nan |           nan |        1.7715 | False                 |             nan |
| OZK      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   66.393 |               nan |                   nan |                     nan |           nan |        0.6146 | False                 |             nan |
| HFWA     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   65.433 |               nan |                   nan |                     nan |           nan |        1.0845 | False                 |             nan |
| BANC     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   65.256 |               nan |                   nan |                     nan |           nan |        0.557  | False                 |             nan |
| FMBH     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   65.161 |               nan |                   nan |                     nan |           nan |        0.7419 | False                 |             nan |
| UNF      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   64.741 |               nan |                   nan |                     nan |           nan |        0.634  | False                 |             nan |
| UNH      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   64.199 |               nan |                   nan |                     nan |           nan |        0.2093 | False                 |             nan |
| WABC     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   64.185 |               nan |                   nan |                     nan |           nan |        0.7111 | False                 |             nan |
| USB      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   63.73  |               nan |                   nan |                     nan |           nan |        0.5459 | False                 |             nan |
| CBAN     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   63.433 |               nan |                   nan |                     nan |           nan |        1.8965 | False                 |             nan |
| UNM      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   63.156 |               nan |                   nan |                     nan |           nan |        2.1739 | False                 |             nan |
| HOPE     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   62.586 |               nan |                   nan |                     nan |           nan |        1.4    | False                 |             nan |
| PRDO     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   62.309 |               nan |                   nan |                     nan |           nan |      nan      | False                 |             nan |
| OFG      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   61.65  |               nan |                   nan |                     nan |           nan |        2.6338 | False                 |             nan |
| CNS      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   61.292 |               nan |                   nan |                     nan |           nan |        1.1796 | False                 |             nan |
| FNB      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   61.273 |               nan |                   nan |                     nan |           nan |        1.6053 | False                 |             nan |
| TCBI     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   60.865 |               nan |                   nan |                     nan |           nan |        0.4831 | False                 |             nan |
| BHB      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   60.234 |               nan |                   nan |                     nan |           nan |        1.0303 | False                 |             nan |
| MG       | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   59.772 |               nan |                   nan |                     nan |           nan |        0.5761 | False                 |             nan |
| IRD      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   59.14  |               nan |                   nan |                     nan |           nan |        1.125  | False                 |             nan |
| CENT     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   58.89  |               nan |                   nan |                     nan |           nan |        0.9217 | False                 |             nan |
| ISSC     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   58.527 |               nan |                   nan |                     nan |           nan |        0.6076 | False                 |             nan |
| OII      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   58.195 |               nan |                   nan |                     nan |           nan |        1.0123 | False                 |             nan |
| AVB      | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   57.782 |               nan |                   nan |                     nan |           nan |        0.4717 | False                 |             nan |
| TROW     | 2026-06-04    | SLINGSHOT      | slingshot       | True             |                   57.485 |               nan |                   nan |                     nan |           nan |        0.5691 | False                 |             nan |

## Bucket performance summary
| metric              | bucket   |   n_rows |   n_resolved |   avg_realized_r |   win_rate |   avg_ret_5d_pct |   pct_range_break |   pct_rr_pass |   pct_vol_gate_pass |   pct_contraction_gate_pass |
|:--------------------|:---------|---------:|-------------:|-----------------:|-----------:|-----------------:|------------------:|--------------:|--------------------:|----------------------------:|
| contraction_quality | 30-40    |       12 |            0 |              nan |        nan |           nan    |              16.7 |          75   |                 nan |                         0   |
| contraction_quality | 40-50    |       13 |            0 |              nan |        nan |           nan    |              38.5 |          46.2 |                 nan |                         0   |
| contraction_quality | 50-60    |       42 |            0 |              nan |        nan |           nan    |              52.4 |          26.8 |                 nan |                       100   |
| contraction_quality | <30      |        9 |            0 |              nan |        nan |           nan    |              33.3 |          66.7 |                 nan |                         0   |
| contraction_quality | >=60     |       29 |            0 |              nan |        nan |           nan    |              79.3 |          18.5 |                 nan |                       100   |
| contraction_quality | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| volume_ratio        | MISSING  |      146 |            0 |              nan |        nan |            -2.44 |              52.4 |          36.3 |                 nan |                        67.6 |
| distance_from_21ema | MISSING  |      146 |            0 |              nan |        nan |            -2.44 |              52.4 |          36.3 |                 nan |                        67.6 |
| risk_pct            | MISSING  |      146 |            0 |              nan |        nan |            -2.44 |              52.4 |          36.3 |                 nan |                        67.6 |
| range_break         | FALSE    |       50 |            0 |              nan |        nan |           nan    |               0   |          60   |                 nan |                        52   |
| range_break         | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| range_break         | TRUE     |       55 |            0 |              nan |        nan |           nan    |             100   |          13.5 |                 nan |                        81.8 |
| custom_rs_rating    | MISSING  |      146 |            0 |              nan |        nan |            -2.44 |              52.4 |          36.3 |                 nan |                        67.6 |
| rr_pass             | FALSE    |       65 |            0 |              nan |        nan |           nan    |              69.2 |           0   |                 nan |                        80   |
| rr_pass             | MISSING  |       44 |            0 |              nan |        nan |            -2.44 |             100   |         nan   |                 nan |                       100   |
| rr_pass             | TRUE     |       37 |            0 |              nan |        nan |           nan    |              18.9 |         100   |                 nan |                        43.2 |
| vol_gate            | MISSING  |      146 |            0 |              nan |        nan |            -2.44 |              52.4 |          36.3 |                 nan |                        67.6 |
| contraction_gate    | FALSE    |       34 |            0 |              nan |        nan |           nan    |              29.4 |          61.8 |                 nan |                         0   |
| contraction_gate    | MISSING  |       41 |            0 |              nan |        nan |            -2.44 |             nan   |         nan   |                 nan |                       nan   |
| contraction_gate    | TRUE     |       71 |            0 |              nan |        nan |           nan    |              63.4 |          23.5 |                 nan |                       100   |

## Interpretation discipline
- Do not relax SLINGSHOT gates from this report alone.
- Reassess after at least 30 resolved SLINGSHOT cases.
- Use bucket performance to test whether contraction 50, volume 1.2x, and R:R filters are predictive or over-suppressive.
