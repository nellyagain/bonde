# Decision-Log Corpus Reconciliation Audit — 2026-06-02

Purpose: explain decision-log row-count changes and EP9M coverage across discovery → de-duplication → normalization → master log.

## Summary

| run_date   |   raw_candidate_files_discovered |   included_files |   excluded_files |   raw_rows_discovered_all_candidates |   raw_rows_included_files |   rows_after_schema_normalization_included |   master_decision_log_rows_after_dedup |   rows_removed_by_master_dedup |   excluded_duplicate_files |   included_raw_ep9m_setup_family_rows |   included_raw_ep9m_context_rows_any |   included_norm_ep9m_setup_family_rows |   included_norm_ep9m_context_rows_any |   master_ep9m_setup_family_rows |   master_ep9m_context_rows_any |
|:-----------|---------------------------------:|-----------------:|-----------------:|-------------------------------------:|--------------------------:|-------------------------------------------:|---------------------------------------:|-------------------------------:|---------------------------:|--------------------------------------:|-------------------------------------:|---------------------------------------:|--------------------------------------:|--------------------------------:|-------------------------------:|
| 2026-06-02 |                                9 |                8 |                1 |                                  907 |                       884 |                                        859 |                                    835 |                             24 |                          1 |                                     0 |                                  158 |                                      0 |                                   158 |                               0 |                            158 |

## Included decision-log files

| file_name                         | detected_date   |   rows_raw_file |   rows_after_schema_normalization |   rows_after_master_dedup | schema_version    |   raw_ep9m_setup_family_rows |   norm_ep9m_setup_family_rows |
|:----------------------------------|:----------------|----------------:|----------------------------------:|--------------------------:|:------------------|-----------------------------:|------------------------------:|
| daily_decision_log_schema.csv     | 0000-00-00      |              25 |                                 0 |                         0 | EMPTY_OR_FILTERED |                            0 |                             0 |
| sample_daily_decision_log.csv     | 0000-00-00      |               4 |                                 4 |                         4 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-06.csv | 2026-05-06      |             248 |                               248 |                       248 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-07.csv | 2026-05-07      |             382 |                               382 |                       358 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-09.csv | 2026-05-09      |              21 |                                21 |                        21 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-12.csv | 2026-05-12      |              22 |                                22 |                        22 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-13.csv | 2026-05-13      |              62 |                                62 |                        62 | V5_9_EXPLICIT     |                            0 |                             0 |
| daily_decision_log_2026-05-29.csv | 2026-05-29      |             120 |                               120 |                       120 | V5_9_EXPLICIT     |                            0 |                             0 |

## Excluded decision-log files

| file_name                             | detected_date   |   rows_raw_file |   candidate_score | exclude_reason                                                              |   raw_ep9m_setup_family_rows |   raw_ep9m_context_rows_any |
|:--------------------------------------|:----------------|----------------:|------------------:|:----------------------------------------------------------------------------|-----------------------------:|----------------------------:|
| daily_decision_log_2026-05-13 (2).csv | 2026-05-13      |              23 |               102 | EXCLUDED_DATE_DUPLICATE_LOWER_SCORE; kept=daily_decision_log_2026-05-13.csv |                            0 |                           1 |

## EP9M reconciliation

- No `setup_family=EP9M` rows were present in the included decision-log corpus for this run. If prior digests showed EP9M rows, compare the excluded-files table and discovery scope.
- EP9M context rows any-token: raw included=158, normalized included=158, master=158.

## Full audit CSV
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_log_discovery_audit_latest.csv`
