# Sugar Babies Overlay Report — 2026-05-17

_v4.13.3 additive context overlay. This is monitoring only, not rule evidence._

## Guardrail

**SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE.** Do not change trading rules from this section alone. Sugar Babies is a context overlay, not an automatic trade signal or gate.

## Data-quality diagnostics

| metric | value |
|---|---|
| `sugar_babies_file_used` | /content/drive/MyDrive/bonde_screener_cache/sugar_babies/sugar_babies.csv |
| `sugar_babies_source_rows` | 399 |
| `sugar_babies_unique_tickers` | 399 |
| `ticker_rows_loaded` | 2826 |
| `ticker_rows_matched` | 1817 |
| `candidate_rows_loaded` | 3202 |
| `candidate_rows_matched` | 2024 |
| `decision_rows_loaded` | 729 |
| `decision_rows_matched` | 396 |
| `outputs_written` | /content/drive/MyDrive/bonde_screener_cache/learning_outputs/skill_pack_ticker_outcomes_sugar_enriched_v410.csv; /content/drive/MyDrive/bonde_screener_cache/learning_outputs/skill_pack_candidate_outcomes_sugar_enriched_v410.csv; /content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_outcomes_sugar_enriched_v410.csv |

- Search paths: `['/content/drive/MyDrive/bonde_screener_cache/sugar_babies', '/content/drive/MyDrive/bonde_screener_cache', '/content']`
- Files found: `['/content/drive/MyDrive/bonde_screener_cache/sugar_babies/sugar_babies.csv']`

## Summary

- Summary rows: **71**

- Max rows with T+1 data in any slice: **2569**

- Max rows with T+3 data in any slice: **1944**

- Max rows with T+5 data in any slice: **1431**

- Max rows with T+10 data in any slice: **0**

- Max rows with T+20 data in any slice: **0**

- Evidence use: **monitoring only; no rule changes.**

## A. Sugar Baby vs non-Sugar Baby

| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     2024 |                1813 |           -0.0156081 |               43.85   |                1382 |             0.888376 |               45.9479 |                 993 |              1.73584 |               45.0151 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     1817 |                1619 |            0.113219  |               44.4719 |                1249 |             0.741472 |               45.7966 |                 898 |              1.61599 |               44.6548 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     1178 |                1100 |           -0.113127  |               44.6364 |                 798 |            -0.110879 |               44.9875 |                 613 |             -1.18492 |               42.2512 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     1009 |                 950 |           -0.214191  |               43.3684 |                 695 |            -0.147111 |               44.4604 |                 533 |             -1.13341 |               41.0882 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## B. Sugar Baby recurrence buckets

| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 8+            |     1186 |                1052 |             0.244822 |               45.5323 |                 813 |             0.988642 |               46.6175 |                 565 |             2.10328  |               44.7788 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 0             |     1009 |                 950 |            -0.214191 |               43.3684 |                 695 |            -0.147111 |               44.4604 |                 533 |            -1.13341  |               41.0882 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      294 |                 259 |            -0.111906 |               42.471  |                 196 |             0.322216 |               50      |                 137 |             0.748263 |               48.9051 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      192 |                 166 |             0.524085 |               41.5663 |                 126 |             0.906318 |               38.0952 |                 100 |             2.32293  |               42      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      145 |                 142 |            -0.931452 |               43.662  |                 114 |            -0.482607 |               41.2281 |                  96 |            -0.74999  |               40.625  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## C. Action-label × Sugar Baby

| row_level   | slice_name                       | slice_value     |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:---------------------------------|:----------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | action_label__x__sugar_baby_flag | UNKNOWN | True  |     1441 |                1250 |            0.239751  |               45.12   |                 881 |             0.688096 |               46.311  |                 536 |             2.13765  |               46.8284 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | C | True        |      331 |                 324 |           -0.311998  |               42.9012 |                 323 |             0.355965 |               43.6533 |                 322 |             0.157401 |               40.0621 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | UNKNOWN | False |      692 |                 661 |            0.0212618 |               44.1755 |                 407 |             0.180113 |               44.4717 |                 288 |            -0.930528 |               40.9722 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | C | False       |      128 |                 112 |           -1.0057    |               42.8571 |                 111 |            -0.251491 |               54.0541 |                 101 |            -0.752755 |               47.5248 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | B | False       |      116 |                 106 |           -0.916641  |               32.0755 |                 106 |            -0.855918 |               35.8491 |                  78 |            -1.31684  |               34.6154 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | D | False       |       67 |                  67 |            0.112727  |               55.2239 |                  67 |            -0.515489 |               44.7761 |                  63 |            -2.14542  |               41.2698 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | D | True        |       25 |                  25 |           -0.417035  |               36      |                  25 |             3.05744  |               56      |                  25 |             3.24337  |               52      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | B | True        |       19 |                  19 |           -0.102909  |               42.1053 |                  19 |             6.77404  |               47.3684 |                  14 |            12.6122   |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | A2 | False      |        4 |                   4 |           -3.82144   |               25      |                   4 |            -5.59184  |                0      |                   3 |            -7.40338  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | A2 | True       |        1 |                   1 |           -2.91867   |                0      |                   1 |            -0.233484 |                0      |                   1 |            -2.95758  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | B+_C1 | False   |        2 |                   0 |          nan         |              nan      |                   0 |           nan        |              nan      |                   0 |           nan        |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## D. Primary-setup × Sugar Baby

| row_level   | slice_name                        | slice_value          |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------------------------|:---------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | primary_setup__x__sugar_baby_flag | EP9M | True          |     1527 |                1344 |            0.185494  |               45.3125 |                1048 |             0.266852 |               45.3244 |                 751 |            1.01858   |               43.5419 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ACTIVE_BURST | False |      401 |                 392 |           -0.405551  |               43.3673 |                 325 |             0.437499 |               45.2308 |                 260 |           -0.823552  |               38.8462 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PAUSE | False        |      234 |                 215 |           -0.122893  |               37.6744 |                 169 |            -0.784743 |               39.645  |                 115 |           -0.903232  |               42.6087 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ACTIVE_BURST | True  |      139 |                 133 |           -1.1558    |               38.3459 |                 102 |             3.13751  |               47.0588 |                  77 |            4.73624   |               48.0519 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_ACTIVE | False    |      100 |                  96 |           -0.0290324 |               48.9583 |                  78 |            -1.57181  |               34.6154 |                  62 |           -2.9307    |               33.871  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_SPIKE | False     |       61 |                  59 |            1.13379   |               61.0169 |                  53 |            -0.57907  |               49.0566 |                  45 |           -2.60269   |               42.2222 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_SPIKE | True      |       45 |                  45 |            0.0715203 |               37.7778 |                  35 |             2.16703  |               54.2857 |                  26 |            3.35653   |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | DELAYED_EP | False   |       40 |                  38 |           -0.385566  |               44.7368 |                  30 |             1.11831  |               56.6667 |                  22 |            0.662484  |               59.0909 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PAUSE | True         |       43 |                  39 |            1.38151   |               48.7179 |                  29 |             4.37533  |               51.7241 |                  19 |            8.28078   |               63.1579 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_ACTIVE | True     |       29 |                  28 |            2.26724   |               53.5714 |                  23 |             6.37349  |               43.4783 |                  17 |            5.90288   |               47.0588 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ANTICIPATION | False |       23 |                  22 |            0.131094  |               63.6364 |                  20 |             1.01114  |               75      |                  17 |           -0.118469  |               58.8235 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PRE_BURST | False    |       26 |                  25 |            0.303701  |               48      |                  20 |            -0.614375 |               50      |                  12 |            0.0128345 |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | DELAYED_EP | True    |       11 |                  11 |           -0.474339  |               27.2727 |                  10 |            -1.76574  |               40      |                   7 |           -2.43556   |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PRE_BURST | True     |        2 |                   2 |           -1.27254   |                0      |                   2 |            -2.62597  |               50      |                   1 |           -6.39038   |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | SLINGSHOT | False    |      122 |                 103 |           -0.75743   |               33.9806 |                   0 |           nan        |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | SLINGSHOT | True     |       20 |                  17 |           -1.47642   |               35.2941 |                   0 |           nan        |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | DIAGNOSTICS | False  |        2 |                   0 |          nan         |              nan      |                   0 |           nan        |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ANTICIPATION | True  |        1 |                   0 |          nan         |              nan      |                   0 |           nan        |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## E. Setup-family × Sugar Baby

| row_level   | slice_name                       | slice_value          |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:---------------------------------|:---------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | setup_family__x__sugar_baby_flag | EP9M | True          |     1648 |                1460 |            0.125973  |               44.7945 |                1128 |            0.446799  |               45.3014 |                 807 |            1.26968   |               43.8662 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ACTIVE_BURST | False |      428 |                 417 |           -0.422427  |               44.3645 |                 329 |            0.404903  |               44.9848 |                 263 |           -0.885732  |               38.7833 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PAUSE | False        |      249 |                 217 |           -0.120867  |               37.788  |                 171 |           -0.77307   |               39.7661 |                 116 |           -0.893439  |               43.1034 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_ACTIVE | False    |      168 |                 164 |           -0.16731   |               49.3902 |                 134 |           -1.01975   |               36.5672 |                 106 |           -2.5653    |               38.6792 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ACTIVE_BURST | True  |      143 |                 137 |           -1.09135   |               38.6861 |                 103 |            3.2482    |               47.5728 |                  78 |            4.7581    |               48.7179 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_SPIKE | False     |       98 |                  95 |            1.95605   |               64.2105 |                  83 |            0.0681828 |               55.4217 |                  70 |           -1.86247   |               47.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_SPIKE | True      |       99 |                  99 |           -0.89802   |               37.3737 |                  73 |            2.50692   |               54.7945 |                  52 |            1.89756   |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_ACTIVE | True     |       48 |                  47 |            0.376265  |               48.9362 |                  36 |            3.75387   |               41.6667 |                  28 |            4.84145   |               46.4286 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ANTICIPATION | False |       44 |                  40 |            0.0603984 |               42.5    |                  31 |            0.652454  |               67.7419 |                  24 |           -0.0918027 |               58.3333 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | DELAYED_EP | False   |       40 |                  38 |           -0.385566  |               44.7368 |                  30 |            1.11831   |               56.6667 |                  22 |            0.662484  |               59.0909 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PAUSE | True         |       52 |                  40 |            1.03447   |               47.5    |                  30 |            3.13151   |               50      |                  20 |            5.8566    |               60      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PRE_BURST | False    |       26 |                  25 |            0.303701  |               48      |                  20 |           -0.614375  |               50      |                  12 |            0.0128345 |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | DELAYED_EP | True    |       11 |                  11 |           -0.474339  |               27.2727 |                  10 |           -1.76574   |               40      |                   7 |           -2.43556   |               57.1429 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PRE_BURST | True     |        2 |                   2 |           -1.27254   |                0      |                   2 |           -2.62597   |               50      |                   1 |           -6.39038   |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | SLINGSHOT | False    |      123 |                 104 |           -0.728874  |               34.6154 |                   0 |          nan         |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | SLINGSHOT | True     |       20 |                  17 |           -1.47642   |               35.2941 |                   0 |          nan         |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | DIAGNOSTICS | False  |        2 |                   0 |          nan         |              nan      |                   0 |          nan         |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ANTICIPATION | True  |        1 |                   0 |          nan         |              nan      |                   0 |          nan         |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## F. B+ blocker × Sugar Baby

| row_level   | slice_name                             | slice_value           |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:---------------------------------------|:----------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | bplus_blocker_type__x__sugar_baby_flag | NOT_BPLUS | True      |     1815 |                1617 |             0.115807 |               44.4651 |                1247 |            0.750901  |               45.8701 |                 896 |              1.63398 |               44.7545 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | NOT_BPLUS | False     |      992 |                 935 |            -0.191189 |               43.6364 |                 680 |           -0.0778123 |               45.1471 |                 524 |             -1.08309 |               41.4122 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | BPLUS_UNKNOWN | False |        5 |                   5 |            -0.984624 |               40      |                   5 |           -3.16698   |                0      |                   5 |             -2.83395 |               20      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | C1 | False            |       12 |                  10 |            -1.9797   |               20      |                  10 |           -3.34947   |               20      |                   4 |             -5.59952 |               25      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | BPLUS_UNKNOWN | True  |        1 |                   1 |             4.38024  |              100      |                   1 |           -0.931961  |                0      |                   1 |             -5.68499 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | C1 | True             |        1 |                   1 |            -8.3391   |                0      |                   1 |           -9.34256   |                0      |                   1 |             -7.19723 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## G. Council-verdict × Sugar Baby

| row_level   | slice_name                          | slice_value             |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:------------------------------------|:------------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | council_verdict__x__sugar_baby_flag | NOT_COUNCIL | True      |     1814 |                1616 |             0.117685 |               44.4926 |                1246 |             0.751691 |              45.9069  |                 895 |             1.63911  |               44.8045 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | NOT_COUNCIL | False     |      988 |                 931 |            -0.175591 |               43.7164 |                 676 |            -0.045185 |              45.4142  |                 521 |            -1.04669  |               41.6507 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | PENDING_COUNCIL | False |       14 |                  14 |            -2.14718  |               28.5714 |                  14 |            -3.49177  |               7.14286 |                   7 |            -4.59606  |               14.2857 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | DEFER | False           |        4 |                   3 |            -4.20975  |                0      |                   3 |            -6.47469  |               0       |                   3 |            -7.5769   |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | PENDING_COUNCIL | True  |        2 |                   2 |             0.730789 |               50      |                   2 |            -0.582722 |               0       |                   2 |            -4.32129  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | CANCEL | False          |        2 |                   1 |             3.47276  |              100      |                   1 |             1.08242  |             100       |                   1 |             0.332617 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | CANCEL | True           |        1 |                   1 |            -8.3391   |                0      |                   1 |            -9.34256  |               0       |                   1 |            -7.19723  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | PROMOTE | False         |        1 |                   1 |            -0.788912 |                0      |                   1 |            -4.47048  |               0       |                   1 |            -4.20751  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## Reading rules

- `sugar_baby_flag=True` means the ticker appeared in the Sugar Babies CSV, not that it is automatically tradeable.
- Use this report to test whether Sugar Baby context improves A2/B+/setup-family outcomes over time.
- Missing future bars are excluded from T+N metrics, not treated as zero.
- Rule changes still require mature, repeated weekly cohort evidence.