# Bonde Weekly Cohort Report — 2026-W23

_Cohort = signals generated within an ISO calendar week, evaluated only after their forward-return windows have matured. This is the report to consult for rule-change evidence._

## Maturity rules

- T+5 metrics appear once cohort is ≥ 7 calendar days old
- T+10 metrics appear once cohort is ≥ 14 calendar days old
- T+20 metrics appear once cohort is ≥ 28 calendar days old

Most recent fully-mature cohort (T+20 mature): **2026-W18**

## Cohort × Setup-Family Summary

_Triggered-view metrics only. `n_evaluable_*d_trig` counts triggered rows with mature return data. `mature_tN` columns indicate whether the corresponding window has matured for that cohort. Blank metrics mean the cohort is too recent to evaluate at that horizon._

| cohort_week   |   cohort_age_days | setup_family   |   n_rows |   n_triggered |   pct_triggered | mature_t5   |   n_evaluable_5d_trig |   avg_ret_5d_trig |   win_rate_5d_trig | mature_t10   |   n_evaluable_10d_trig |   avg_ret_10d_trig |   win_rate_10d_trig | mature_t20   |   n_evaluable_20d_trig |   avg_ret_20d_trig |   win_rate_20d_trig |
|:--------------|------------------:|:---------------|---------:|--------------:|----------------:|:------------|----------------------:|------------------:|-------------------:|:-------------|-----------------------:|-------------------:|--------------------:|:-------------|-----------------------:|-------------------:|--------------------:|
| 2026-W22      |                 2 | ACTIVE_BURST   |       35 |            33 |           94.29 | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | ANTICIPATION   |        4 |             2 |           50    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | DELAYED_EP     |        3 |             2 |           66.67 | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | EP_ACTIVE      |        7 |             7 |          100    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | EP_SPIKE       |        4 |             4 |          100    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | PAUSE          |       30 |            18 |           60    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | PRE_BURST      |        2 |             2 |          100    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W22      |                 2 | SLINGSHOT      |       30 |            27 |           90    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W21      |                 9 | PAUSE          |        1 |             0 |            0    | True        |                     0 |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | ACTIVE_BURST   |       15 |            13 |           86.67 | True        |                    13 |             -4.31 |              30.77 | True         |                     13 |               5.21 |               61.54 | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | ANTICIPATION   |        2 |             2 |          100    | True        |                     2 |             -0.16 |              50    | True         |                      2 |               1.08 |              100    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | DELAYED_EP     |       11 |            10 |           90.91 | True        |                    10 |             -1.38 |              50    | True         |                     10 |               0.75 |               50    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | EP_ACTIVE      |        7 |             7 |          100    | True        |                     7 |             -4.55 |              42.86 | True         |                      7 |              -1.99 |               57.14 | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | MOMENTUM_BURST |        1 |             0 |            0    | True        |                     0 |            nan    |             nan    | True         |                      0 |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | PAUSE          |       12 |            10 |           83.33 | True        |                    10 |              0.07 |              40    | True         |                     10 |              -0.19 |               60    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | PRE_BURST      |        1 |             0 |            0    | True        |                     0 |            nan    |             nan    | True         |                      0 |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                16 | SLINGSHOT      |       41 |            41 |          100    | True        |                    41 |             -2.44 |              26.83 | True         |                     41 |               2.51 |               43.9  | False        |                    nan |                nan |                 nan |
| 2026-W19      |                23 | ACTIVE_BURST   |       81 |            78 |           96.3  | True        |                    78 |             -0.72 |              34.62 | True         |                     78 |              -4.51 |               30.77 | False        |                    nan |                nan |                 nan |
| 2026-W19      |                23 | ANTICIPATION   |        6 |             6 |          100    | True        |                     6 |             -0.06 |              50    | True         |                      5 |              -0.33 |               40    | False        |                    nan |                nan |                 nan |
| 2026-W19      |                23 | DELAYED_EP     |        6 |             6 |          100    | True        |                     6 |              1.31 |              83.33 | True         |                      6 |              -1.5  |               33.33 | False        |                    nan |                nan |                 nan |
| 2026-W19      |                23 | EP_ACTIVE      |       26 |            23 |           88.46 | True        |                    23 |              0.43 |              47.83 | True         |                     23 |               0.41 |               34.78 | False        |                    nan |                nan |                 nan |
| 2026-W19      |                23 | PAUSE          |       35 |            33 |           94.29 | True        |                    32 |              1.34 |              50    | True         |                     31 |               0.04 |               67.74 | False        |                    nan |                nan |                 nan |
| 2026-W18      |                30 | PAUSE          |        2 |             1 |           50    | True        |                     0 |            nan    |             nan    | True         |                      0 |             nan    |              nan    | True         |                      0 |                nan |                 nan |
| 2026-W17      |                37 | PAUSE          |        2 |             1 |           50    | True        |                     0 |            nan    |             nan    | True         |                      0 |             nan    |              nan    | True         |                      0 |                nan |                 nan |

## Reading guidance

- Look for **patterns that repeat across multiple cohorts**, not single-cohort spikes.
- A setup family with 3+ consecutive mature cohorts showing positive `avg_ret_5d_trig` is evidence. A single cohort is not.
- If `pct_triggered` is consistently low (< 30%) for a setup family, the setup may be promoting candidates that rarely actually fire.
- Win rates and averages here use dropna() — pending rows do not bias the result.
- The CSV also stores all-row counts as `n_evaluable_*d_all`; the markdown table shows triggered-view counts only.

## Notes

- This report does NOT replace the daily report. Use the daily for monitoring; use this for evidence.
- Catalyst × setup-family stratification is in the daily report. It is not duplicated here.
- A future version may add rolling cohort comparisons (cohort N vs N-1 vs N-2) to surface trend changes.
