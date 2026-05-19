# Decision-Log Corpus Reconciliation Audit — 2026-05-19

Purpose: explain decision-log row-count changes and EP9M coverage across discovery → de-duplication → normalization → master log.

## Summary

| run_date   |   raw_candidate_files_discovered |   included_files |   excluded_files |   raw_rows_discovered_all_candidates |   raw_rows_included_files |   rows_after_schema_normalization_included |   master_decision_log_rows_after_dedup |   rows_removed_by_master_dedup |   excluded_duplicate_files |   included_raw_ep9m_setup_family_rows |   included_raw_ep9m_context_rows_any |   included_norm_ep9m_setup_family_rows |   included_norm_ep9m_context_rows_any |   master_ep9m_setup_family_rows |   master_ep9m_context_rows_any |
|:-----------|---------------------------------:|-----------------:|-----------------:|-------------------------------------:|--------------------------:|-------------------------------------------:|---------------------------------------:|-------------------------------:|---------------------------:|--------------------------------------:|-------------------------------------:|---------------------------------------:|--------------------------------------:|--------------------------------:|-------------------------------:|
| 2026-05-19 |                               17 |               10 |                7 |                                 1720 |                       908 |                                        883 |                                    859 |                             24 |                          7 |                                     0 |                                  150 |                                      0 |                                   150 |                               0 |                            150 |

## Included decision-log files

| file_name                         | detected_date   |   rows_raw_file |   rows_after_schema_normalization |   rows_after_master_dedup | schema_version    |   raw_ep9m_setup_family_rows |   norm_ep9m_setup_family_rows |
|:----------------------------------|:----------------|----------------:|----------------------------------:|--------------------------:|:------------------|-----------------------------:|------------------------------:|
| daily_decision_log_schema.csv     | 0000-00-00      |              25 |                                 0 |                         0 | EMPTY_OR_FILTERED |                            0 |                             0 |
| sample_daily_decision_log.csv     | 0000-00-00      |               4 |                                 4 |                         4 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-04-27.csv | 2026-04-27      |              19 |                                19 |                        19 | LEGACY_DATE_ONLY  |                            0 |                             0 |
| daily_decision_log_2026-05-06.csv | 2026-05-06      |             248 |                               248 |                       248 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-07.csv | 2026-05-07      |             382 |                               382 |                       358 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-09.csv | 2026-05-09      |              21 |                                21 |                        21 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-12.csv | 2026-05-12      |              22 |                                22 |                        22 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-13.csv | 2026-05-13      |              62 |                                62 |                        62 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-15.csv | 2026-05-15      |              35 |                                35 |                        35 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-18.csv | 2026-05-18      |              90 |                                90 |                        90 | V5_9_EXPLICIT     |                            0 |                             0 |

## Excluded decision-log files

| file_name                             | detected_date   |   rows_raw_file |   candidate_score | exclude_reason                                                              |   raw_ep9m_setup_family_rows |   raw_ep9m_context_rows_any |
|:--------------------------------------|:----------------|----------------:|------------------:|:----------------------------------------------------------------------------|-----------------------------:|----------------------------:|
| daily_decision_log_2026-05-06.csv     | 2026-05-06      |             248 |               170 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-06.csv |                            0 |                         130 |
| daily_decision_log_2026-05-07.csv     | 2026-05-07      |             382 |               170 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-07.csv |                            0 |                           2 |
| daily_decision_log_2026-05-09.csv     | 2026-05-09      |              21 |               134 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-09.csv |                            0 |                           4 |
| daily_decision_log_2026-05-12.csv     | 2026-05-12      |              25 |               131 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-12.csv |                            0 |                           0 |
| daily_decision_log_2026-05-13 (2).csv | 2026-05-13      |              23 |               102 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-13.csv |                            0 |                           1 |
| daily_decision_log_2026-05-13.csv     | 2026-05-13      |              23 |               132 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-13.csv |                            0 |                           1 |
| daily_decision_log_2026-05-18.csv     | 2026-05-18      |              90 |               170 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-18.csv |                            0 |                           2 |

## EP9M reconciliation

- No `setup_family=EP9M` rows were present in the included decision-log corpus for this run. If prior digests showed EP9M rows, compare the excluded-files table and discovery scope.
- EP9M context rows any-token: raw included=150, normalized included=150, master=150.

## Full audit CSV
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_log_discovery_audit_latest.csv`
