# Sugar Babies Overlay Report — 2026-05-19

_v4.13.3 additive context overlay. This is monitoring only, not rule evidence._

## Guardrail

**SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE.** Do not change trading rules from this section alone. Sugar Babies is a context overlay, not an automatic trade signal or gate.

## Data-quality diagnostics

| metric | value |
|---|---|
| `sugar_babies_file_used` | /content/drive/MyDrive/bonde_screener_cache/sugar_babies/sugar_babies.csv |
| `sugar_babies_source_rows` | 406 |
| `sugar_babies_unique_tickers` | 406 |
| `ticker_rows_loaded` | 3086 |
| `ticker_rows_matched` | 1979 |
| `candidate_rows_loaded` | 3491 |
| `candidate_rows_matched` | 2199 |
| `decision_rows_loaded` | 859 |
| `decision_rows_matched` | 414 |
| `outputs_written` | /content/drive/MyDrive/bonde_screener_cache/learning_outputs/skill_pack_ticker_outcomes_sugar_enriched_v410.csv; /content/drive/MyDrive/bonde_screener_cache/learning_outputs/skill_pack_candidate_outcomes_sugar_enriched_v410.csv; /content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_outcomes_sugar_enriched_v410.csv |

- Search paths: `['/content/drive/MyDrive/bonde_screener_cache/sugar_babies', '/content/drive/MyDrive/bonde_screener_cache', '/content']`
- Files found: `['/content/drive/MyDrive/bonde_screener_cache/sugar_babies/sugar_babies.csv']`

## Summary

- Summary rows: **72**

- Max rows with T+1 data in any slice: **2819**

- Max rows with T+3 data in any slice: **2254**

- Max rows with T+5 data in any slice: **1711**

- Max rows with T+10 data in any slice: **213**

- Max rows with T+20 data in any slice: **0**

- Evidence use: **monitoring only; no rule changes.**

## A. Sugar Baby vs non-Sugar Baby

| row_level   | slice_name      | slice_value   |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | sugar_baby_flag | True          |     2199 |                2016 |          -0.104713   |               44.494  |                1616 |             0.377544 |               44.1213 |                1215 |             0.684054 |               43.2922 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | True          |     1979 |                1817 |          -0.00593929 |               44.9642 |                1451 |             0.351889 |               44.3832 |                1088 |             0.738128 |               43.1985 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | sugar_baby_flag | False         |     1292 |                1158 |          -0.166612   |               44.6459 |                 926 |            -0.715201 |               42.0086 |                 714 |            -1.6059   |               41.0364 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_flag | False         |     1107 |                1002 |          -0.231687   |               43.8124 |                 803 |            -0.729169 |               41.8431 |                 623 |            -1.5482   |               39.9679 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## B. Sugar Baby recurrence buckets

| row_level   | slice_name             | slice_value   |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:-----------------------|:--------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | sugar_baby_runs_bucket | 8+            |     1315 |                1203 |             0.112345 |               45.719  |                 953 |             0.624442 |               45.4355 |                 707 |            1.18102   |               43.4229 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 0             |     1107 |                1002 |            -0.231687 |               43.8124 |                 803 |            -0.729169 |               41.8431 |                 623 |           -1.5482    |               39.9679 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 4-7           |      307 |                 289 |            -0.211935 |               42.9066 |                 224 |             0.250165 |               47.3214 |                 164 |            0.575958  |               46.9512 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 1             |      157 |                 142 |            -0.999192 |               45.0704 |                 129 |            -1.21643  |               38.7597 |                 105 |           -1.2933    |               40      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | sugar_baby_runs_bucket | 2-3           |      200 |                 183 |             0.312522 |               43.1694 |                 145 |             0.112969 |               37.931  |                 112 |            0.0842993 |               39.2857 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## C. Action-label × Sugar Baby

| row_level   | slice_name                       | slice_value     |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:---------------------------------|:----------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | action_label__x__sugar_baby_flag | UNKNOWN | True  |     1585 |                1437 |            0.0428438 |               45.2331 |                1075 |             0.186362 |               44.4651 |                 722 |             0.685964 |               44.0443 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | UNKNOWN | False |      682 |                 656 |           -0.0349487 |               43.75   |                 485 |            -0.568627 |               41.0309 |                 358 |            -1.55968  |               39.6648 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | D | False       |       71 |                  71 |           -0.0526763 |               53.5211 |                  71 |            -1.08801  |               40.8451 |                  66 |            -2.3291   |               40.9091 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | C | True        |      337 |                 335 |           -0.196177  |               44.4776 |                 331 |             0.307039 |               42.9003 |                 324 |             0.158928 |               40.1235 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | C | False       |      155 |                 153 |           -0.820842  |               47.0588 |                 137 |            -0.899124 |               49.635  |                 106 |            -0.948934 |               46.2264 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | B | False       |      184 |                 108 |           -0.50608   |               35.1852 |                  98 |            -0.787491 |               37.7551 |                  86 |            -1.40708  |               34.8837 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | D | True        |       25 |                  25 |           -0.417035  |               36      |                  25 |             3.05744  |               56      |                  25 |             3.24337  |               52      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | B | True        |       31 |                  19 |            0.352921  |               47.3684 |                  19 |             6.96946  |               52.6316 |                  16 |            11.1374   |               56.25   | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | A2 | False      |       12 |                  11 |           -2.03147   |               27.2727 |                  11 |            -3.19513  |               18.1818 |                   6 |            -5.12376  |               16.6667 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | A1 | False      |        1 |                   1 |            1.43434   |              100      |                   1 |             3.0101   |              100      |                   1 |            -0.101009 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | A2 | True       |        1 |                   1 |           -2.91867   |                0      |                   1 |            -0.233484 |                0      |                   1 |            -2.95758  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | action_label__x__sugar_baby_flag | B+_C1 | False   |        2 |                   2 |           -2.16321   |                0      |                   0 |           nan        |              nan      |                   0 |           nan        |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## D. Primary-setup × Sugar Baby

| row_level   | slice_name                        | slice_value          |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:----------------------------------|:---------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | primary_setup__x__sugar_baby_flag | EP9M | True          |     1666 |                1526 |            0.032849  |               45.4784 |                1211 |            0.0920308 |               44.5912 |                 901 |             0.406463 |               42.3973 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ACTIVE_BURST | False |      412 |                 399 |           -0.399086  |               43.3584 |                 362 |           -0.450253  |               41.4365 |                 304 |            -1.45197  |               37.1711 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PAUSE | False        |      251 |                 232 |           -0.103352  |               39.2241 |                 189 |           -0.735244  |               41.2698 |                 141 |            -1.18732  |               43.2624 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ACTIVE_BURST | True  |      147 |                 141 |           -1.16274   |               39.0071 |                 120 |            1.42416   |               41.6667 |                  98 |             2.45112  |               44.898  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_SPIKE | False     |       61 |                  60 |            0.511839  |               58.3333 |                  55 |           -0.485504  |               49.0909 |                  49 |            -2.81115  |               40.8163 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PRE_BURST | False    |       27 |                  26 |            0.298833  |               50      |                  22 |           -0.221     |               54.5455 |                  15 |             0.029615 |               46.6667 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_ACTIVE | False    |      102 |                 100 |           -0.0755909 |               48      |                  85 |           -1.91325   |               34.1176 |                  67 |            -3.3755   |               32.8358 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | DELAYED_EP | False   |       44 |                  40 |           -0.380939  |               42.5    |                  36 |            0.603715  |               52.7778 |                  28 |             0.359955 |               53.5714 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ANTICIPATION | False |       23 |                  23 |            0.113939  |               60.8696 |                  21 |            0.927132  |               71.4286 |                  19 |            -0.122798 |               57.8947 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_SPIKE | True      |       46 |                  46 |            0.113864  |               39.1304 |                  41 |            0.73104   |               48.7805 |                  33 |             0.659475 |               45.4545 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PAUSE | True         |       46 |                  41 |            1.32167   |               51.2195 |                  34 |            3.73405   |               52.9412 |                  24 |             5.18542  |               58.3333 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | EP_ACTIVE | True     |       31 |                  29 |            2.4057    |               55.1724 |                  25 |            4.67055   |               40      |                  20 |             4.8472   |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | DELAYED_EP | True    |       11 |                  11 |           -0.474339  |               27.2727 |                  11 |           -2.04115   |               36.3636 |                  10 |            -4.17551  |               40      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | PRE_BURST | True     |        2 |                   2 |           -1.27254   |                0      |                   2 |           -2.62597   |               50      |                   2 |            -2.37558  |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | SLINGSHOT | False    |      187 |                 122 |           -0.551155  |               39.3443 |                  33 |           -3.95704   |               18.1818 |                   0 |           nan        |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | SLINGSHOT | True     |       28 |                  20 |           -0.920813  |               45      |                   7 |           -2.53516   |               14.2857 |                   0 |           nan        |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | primary_setup__x__sugar_baby_flag | ANTICIPATION | True  |        2 |                   1 |            0.0142311 |              100      |                   0 |          nan         |              nan      |                   0 |           nan        |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## E. Setup-family × Sugar Baby

| row_level   | slice_name                       | slice_value          |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:---------------------------------|:---------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| candidate   | setup_family__x__sugar_baby_flag | EP9M | True          |     1794 |                1645 |          -0.00461097 |               45.1064 |                1308 |             0.162248 |               44.2661 |                 977 |            0.496001  |               42.477  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ACTIVE_BURST | False |      444 |                 426 |          -0.442397   |               44.1315 |                 374 |            -0.621363 |               40.6417 |                 308 |           -1.52922   |               37.013  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PAUSE | False        |      268 |                 234 |          -0.10164    |               39.3162 |                 191 |            -0.725312 |               41.3613 |                 142 |           -1.17732   |               43.662  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_ACTIVE | False    |      172 |                 167 |          -0.202452   |               48.503  |                 147 |            -1.39438  |               35.3741 |                 117 |           -3.05827   |               37.6068 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ACTIVE_BURST | True  |      152 |                 145 |          -1.10166    |               39.3103 |                 123 |             1.50191  |               42.2764 |                  99 |            2.49143   |               45.4545 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_SPIKE | False     |       98 |                  96 |           1.29199    |               61.4583 |                  87 |             0.156725 |               55.1724 |                  77 |           -2.0606    |               45.4545 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ANTICIPATION | False |       47 |                  44 |           0.0406905  |               38.6364 |                  35 |             0.550238 |               60      |                  27 |           -0.0914728 |               59.2593 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PRE_BURST | False    |       27 |                  26 |           0.298833   |               50      |                  22 |            -0.221    |               54.5455 |                  15 |            0.029615  |               46.6667 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_SPIKE | True      |      101 |                 101 |          -0.840251   |               38.6139 |                  87 |             1.03797  |               49.4253 |                  69 |           -0.738441  |               46.3768 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | EP_ACTIVE | True     |       52 |                  49 |           0.521751   |               51.0204 |                  43 |             1.72757  |               34.8837 |                  33 |            3.42704   |               45.4545 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | DELAYED_EP | False   |       44 |                  40 |          -0.380939   |               42.5    |                  36 |             0.603715 |               52.7778 |                  28 |            0.359955  |               53.5714 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PAUSE | True         |       57 |                  42 |           0.992586   |               50      |                  35 |             2.68624  |               51.4286 |                  25 |            3.36989   |               56      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | DELAYED_EP | True    |       11 |                  11 |          -0.474339   |               27.2727 |                  11 |            -2.04115  |               36.3636 |                  10 |           -4.17551   |               40      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | PRE_BURST | True     |        2 |                   2 |          -1.27254    |                0      |                   2 |            -2.62597  |               50      |                   2 |           -2.37558   |               50      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | SLINGSHOT | False    |      188 |                 123 |          -0.528686   |               39.8374 |                  34 |            -4.00422  |               17.6471 |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | SLINGSHOT | True     |       28 |                  20 |          -0.920813   |               45      |                   7 |            -2.53516  |               14.2857 |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | DIAGNOSTICS | False  |        4 |                   2 |          -0.103971   |               50      |                   0 |           nan        |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| candidate   | setup_family__x__sugar_baby_flag | ANTICIPATION | True  |        2 |                   1 |           0.0142311  |              100      |                   0 |           nan        |              nan      |                   0 |          nan         |              nan      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## F. B+ blocker × Sugar Baby

| row_level   | slice_name                             | slice_value           |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:---------------------------------------|:----------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | bplus_blocker_type__x__sugar_baby_flag | NOT_BPLUS | True      |     1975 |                1814 |          -0.00520104 |               44.9283 |                1448 |             0.363215 |               44.4751 |                1086 |              0.75135 |               43.2781 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | NOT_BPLUS | False     |     1093 |                 989 |          -0.212825   |               43.9838 |                 792 |            -0.696568 |               42.1717 |                 613 |             -1.51472 |               40.1305 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | BPLUS_UNKNOWN | False |        5 |                   5 |          -0.984624   |               40      |                   5 |            -3.16698  |                0      |                   5 |             -2.83395 |               20      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | C1 | False            |        7 |                   6 |          -2.24715    |               16.6667 |                   4 |            -4.58541  |               25      |                   4 |             -5.59952 |               25      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | C1 | True             |        3 |                   2 |          -2.86862    |               50      |                   2 |            -7.2057   |                0      |                   1 |             -7.19723 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | C3 | False            |        2 |                   2 |          -1.63029    |               50      |                   2 |             0.168028 |               50      |                   1 |              0.56738 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | bplus_blocker_type__x__sugar_baby_flag | BPLUS_UNKNOWN | True  |        1 |                   1 |           4.38024    |              100      |                   1 |            -0.931961 |                0      |                   1 |             -5.68499 |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## G. Council-verdict × Sugar Baby

| row_level   | slice_name                          | slice_value             |   n_rows |   rows_with_t1_eval |   avg_ret_t1_partial |   win_rate_t1_partial |   rows_with_t3_eval |   avg_ret_t3_partial |   win_rate_t3_partial |   rows_with_t5_eval |   avg_ret_t5_partial |   win_rate_t5_partial | partial_label                          |
|:------------|:------------------------------------|:------------------------|---------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|--------------------:|---------------------:|----------------------:|:---------------------------------------|
| ticker      | council_verdict__x__sugar_baby_flag | NOT_COUNCIL | True      |     1974 |                1813 |          -0.00359405 |               44.9531 |                1447 |             0.363627 |               44.5059 |                1085 |             0.754768 |               43.318  | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | NOT_COUNCIL | False     |     1081 |                 978 |          -0.192369   |               44.1718 |                 781 |            -0.661377 |               42.5096 |                 607 |            -1.47905  |               40.3624 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | PENDING_COUNCIL | False |       17 |                  17 |          -1.74947    |               35.2941 |                  17 |            -2.71616  |               17.6471 |                  11 |            -3.64885  |               27.2727 | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | DEFER | False           |        5 |                   4 |          -3.22693    |                0      |                   3 |            -6.47469  |                0      |                   3 |            -7.5769   |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | PENDING_COUNCIL | True  |        3 |                   3 |           1.35448    |               66.6667 |                   3 |            -2.0781   |                0      |                   2 |            -4.32129  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | CANCEL | False          |        3 |                   2 |          -0.287605   |               50      |                   1 |             1.08242  |              100      |                   1 |             0.332617 |              100      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | CANCEL | True           |        2 |                   1 |          -8.3391     |                0      |                   1 |            -9.34256  |                0      |                   1 |            -7.19723  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |
| ticker      | council_verdict__x__sugar_baby_flag | PROMOTE | False         |        1 |                   1 |          -0.788912   |                0      |                   1 |            -4.47048  |                0      |                   1 |            -4.20751  |                0      | SUGAR_BABIES_OVERLAY_NOT_RULE_EVIDENCE |

## Reading rules

- `sugar_baby_flag=True` means the ticker appeared in the Sugar Babies CSV, not that it is automatically tradeable.
- Use this report to test whether Sugar Baby context improves A2/B+/setup-family outcomes over time.
- Missing future bars are excluded from T+N metrics, not treated as zero.
- Rule changes still require mature, repeated weekly cohort evidence.