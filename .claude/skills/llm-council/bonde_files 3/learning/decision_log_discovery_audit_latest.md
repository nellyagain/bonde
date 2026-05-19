# Decision-Log Corpus Reconciliation Audit — 2026-05-19

Purpose: explain decision-log row-count changes and EP9M coverage across discovery → de-duplication → normalization → master log.

## Summary

| run_date   |   raw_candidate_files_discovered |   included_files |   excluded_files |   raw_rows_discovered_all_candidates |   raw_rows_included_files |   rows_after_schema_normalization_included |   master_decision_log_rows_after_dedup |   rows_removed_by_master_dedup |   excluded_duplicate_files |   included_raw_ep9m_setup_family_rows |   included_raw_ep9m_context_rows_any |   included_norm_ep9m_setup_family_rows |   included_norm_ep9m_context_rows_any |   master_ep9m_setup_family_rows |   master_ep9m_context_rows_any |
|:-----------|---------------------------------:|-----------------:|-----------------:|-------------------------------------:|--------------------------:|-------------------------------------------:|---------------------------------------:|-------------------------------:|---------------------------:|--------------------------------------:|-------------------------------------:|---------------------------------------:|--------------------------------------:|--------------------------------:|-------------------------------:|
| 2026-05-19 |                                1 |                1 |                0 |                                   90 |                        90 |                                         90 |                                     90 |                              0 |                          0 |                                     0 |                                    2 |                                      0 |                                     2 |                               0 |                              2 |

## Included decision-log files

| file_name                         | detected_date   |   rows_raw_file |   rows_after_schema_normalization |   rows_after_master_dedup | schema_version   |   raw_ep9m_setup_family_rows |   norm_ep9m_setup_family_rows |
|:----------------------------------|:----------------|----------------:|----------------------------------:|--------------------------:|:-----------------|-----------------------------:|------------------------------:|
| daily_decision_log_2026-05-18.csv | 2026-05-18      |              90 |                                90 |                        90 | V5_9_EXPLICIT    |                            0 |                             0 |

## Excluded decision-log files

_No excluded decision-log files._

## EP9M reconciliation

- No `setup_family=EP9M` rows were present in the included decision-log corpus for this run. If prior digests showed EP9M rows, compare the excluded-files table and discovery scope.
- EP9M context rows any-token: raw included=2, normalized included=2, master=2.

## Full audit CSV
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_log_discovery_audit_latest.csv`
