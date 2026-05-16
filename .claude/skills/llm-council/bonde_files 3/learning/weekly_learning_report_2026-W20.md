# Bonde Weekly Cohort Report — 2026-W20

_Cohort = signals generated within an ISO calendar week, evaluated only after their forward-return windows have matured. This is the report to consult for rule-change evidence._

## Maturity rules

- T+5 metrics appear once cohort is ≥ 7 calendar days old
- T+10 metrics appear once cohort is ≥ 14 calendar days old
- T+20 metrics appear once cohort is ≥ 28 calendar days old

Most recent fully-mature cohort (T+20 mature): **_none yet_**

## Cohort × Setup-Family Summary

_Triggered-view metrics only. `mature_tN` columns indicate whether the corresponding window has matured for that cohort. Blank metrics mean the cohort is too recent to evaluate at that horizon._

| cohort_week   |   cohort_age_days | setup_family   |   n_rows |   n_triggered |   pct_triggered | mature_t5   |   n_evaluable_5d |   avg_ret_5d_trig |   win_rate_5d_trig | mature_t10   |   avg_ret_10d_trig |   win_rate_10d_trig | mature_t20   |   avg_ret_20d_trig |   win_rate_20d_trig |
|:--------------|------------------:|:---------------|---------:|--------------:|----------------:|:------------|-----------------:|------------------:|-------------------:|:-------------|-------------------:|--------------------:|:-------------|-------------------:|--------------------:|
| 2026-W20      |                -1 | ACTIVE_BURST   |        7 |             4 |           57.14 | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W20      |                -1 | ANTICIPATION   |        1 |             1 |          100    | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W20      |                -1 | DELAYED_EP     |        8 |             5 |           62.5  | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W20      |                -1 | EP_ACTIVE      |       15 |            12 |           80    | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W20      |                -1 | PAUSE          |       27 |            18 |           66.67 | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W20      |                -1 | PRE_BURST      |        2 |             0 |            0    | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W20      |                -1 | SLINGSHOT      |       23 |             2 |            8.7  | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W19      |                 6 | ACTIVE_BURST   |       81 |            78 |           96.3  | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W19      |                 6 | ANTICIPATION   |        6 |             6 |          100    | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W19      |                 6 | DELAYED_EP     |        6 |             6 |          100    | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W19      |                 6 | EP_ACTIVE      |       26 |            23 |           88.46 | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W19      |                 6 | PAUSE          |       35 |            33 |           94.29 | False       |              nan |            nan    |             nan    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W18      |                13 | ACTIVE_BURST   |        7 |             7 |          100    | True        |                7 |              1.02 |              85.71 | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W18      |                13 | EP_ACTIVE      |        3 |             3 |          100    | True        |                3 |              2.2  |              66.67 | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W18      |                13 | PAUSE          |        6 |             6 |          100    | True        |                5 |              0.35 |              60    | False        |                nan |                 nan | False        |                nan |                 nan |
| 2026-W17      |                20 | PAUSE          |        1 |             1 |          100    | True        |                0 |            nan    |             nan    | True         |                nan |                 nan | False        |                nan |                 nan |

## Reading guidance

- Look for **patterns that repeat across multiple cohorts**, not single-cohort spikes.
- A setup family with 3+ consecutive mature cohorts showing positive `avg_ret_5d_trig` is evidence. A single cohort is not.
- If `pct_triggered` is consistently low (< 30%) for a setup family, the setup may be promoting candidates that rarely actually fire.
- Win rates and averages here use dropna() — pending rows do not bias the result.

## Notes

- This report does NOT replace the daily report. Use the daily for monitoring; use this for evidence.
- Catalyst × setup-family stratification is in the daily report. It is not duplicated here.
- A future version may add rolling cohort comparisons (cohort N vs N-1 vs N-2) to surface trend changes.
