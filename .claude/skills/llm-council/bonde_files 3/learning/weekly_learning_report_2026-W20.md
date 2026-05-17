# Bonde Weekly Cohort Report — 2026-W20

_Cohort = signals generated within an ISO calendar week, evaluated only after their forward-return windows have matured. This is the report to consult for rule-change evidence._

## Maturity rules

- T+5 metrics appear once cohort is ≥ 7 calendar days old
- T+10 metrics appear once cohort is ≥ 14 calendar days old
- T+20 metrics appear once cohort is ≥ 28 calendar days old

Most recent fully-mature cohort (T+20 mature): **_none yet_**

## Cohort × Setup-Family Summary

_Triggered-view metrics only. `n_evaluable_*d_trig` counts triggered rows with mature return data. `mature_tN` columns indicate whether the corresponding window has matured for that cohort. Blank metrics mean the cohort is too recent to evaluate at that horizon._

| cohort_week   |   cohort_age_days | setup_family   |   n_rows |   n_triggered |   pct_triggered | mature_t5   |   n_evaluable_5d_trig |   avg_ret_5d_trig |   win_rate_5d_trig | mature_t10   |   n_evaluable_10d_trig |   avg_ret_10d_trig |   win_rate_10d_trig | mature_t20   |   n_evaluable_20d_trig |   avg_ret_20d_trig |   win_rate_20d_trig |
|:--------------|------------------:|:---------------|---------:|--------------:|----------------:|:------------|----------------------:|------------------:|-------------------:|:-------------|-----------------------:|-------------------:|--------------------:|:-------------|-----------------------:|-------------------:|--------------------:|
| 2026-W20      |                 0 | ACTIVE_BURST   |        7 |             4 |           57.14 | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                 0 | ANTICIPATION   |        1 |             1 |          100    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                 0 | DELAYED_EP     |        8 |             5 |           62.5  | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                 0 | EP_ACTIVE      |       15 |            12 |           80    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                 0 | PAUSE          |       27 |            18 |           66.67 | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                 0 | PRE_BURST      |        2 |             0 |            0    | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W20      |                 0 | SLINGSHOT      |       23 |             2 |            8.7  | False       |                   nan |            nan    |             nan    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W19      |                 7 | ACTIVE_BURST   |       81 |            78 |           96.3  | True        |                    78 |             -0.72 |              34.62 | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W19      |                 7 | ANTICIPATION   |        6 |             6 |          100    | True        |                     6 |             -0.06 |              50    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W19      |                 7 | DELAYED_EP     |        6 |             6 |          100    | True        |                     6 |              1.31 |              83.33 | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W19      |                 7 | EP_ACTIVE      |       26 |            23 |           88.46 | True        |                    23 |              0.43 |              47.83 | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W19      |                 7 | PAUSE          |       35 |            33 |           94.29 | True        |                    32 |              1.34 |              50    | False        |                    nan |             nan    |              nan    | False        |                    nan |                nan |                 nan |
| 2026-W18      |                14 | ACTIVE_BURST   |        7 |             7 |          100    | True        |                     7 |              1.02 |              85.71 | True         |                      7 |              34.7  |               85.71 | False        |                    nan |                nan |                 nan |
| 2026-W18      |                14 | EP_ACTIVE      |        3 |             3 |          100    | True        |                     3 |              2.2  |              66.67 | True         |                      3 |              43.56 |              100    | False        |                    nan |                nan |                 nan |
| 2026-W18      |                14 | PAUSE          |        6 |             6 |          100    | True        |                     5 |              0.35 |              60    | True         |                      5 |               3.5  |               80    | False        |                    nan |                nan |                 nan |
| 2026-W17      |                21 | PAUSE          |        1 |             1 |          100    | True        |                     0 |            nan    |             nan    | True         |                      0 |             nan    |              nan    | False        |                    nan |                nan |                 nan |

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
