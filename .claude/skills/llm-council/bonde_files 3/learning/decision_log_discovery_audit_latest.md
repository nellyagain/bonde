# Decision-Log Corpus Reconciliation Audit — 2026-05-17

Purpose: explain decision-log row-count changes and EP9M coverage across discovery → de-duplication → normalization → master log.

## Summary

| run_date   |   raw_candidate_files_discovered |   included_files |   excluded_files |   raw_rows_discovered_all_candidates |   raw_rows_included_files |   rows_after_schema_normalization_included |   master_decision_log_rows_after_dedup |   rows_removed_by_master_dedup |   excluded_duplicate_files |   included_raw_ep9m_setup_family_rows |   included_raw_ep9m_context_rows_any |   included_norm_ep9m_setup_family_rows |   included_norm_ep9m_context_rows_any |   master_ep9m_setup_family_rows |   master_ep9m_context_rows_any |
|:-----------|---------------------------------:|-----------------:|-----------------:|-------------------------------------:|--------------------------:|-------------------------------------------:|---------------------------------------:|-------------------------------:|---------------------------:|--------------------------------------:|-------------------------------------:|---------------------------------------:|--------------------------------------:|--------------------------------:|-------------------------------:|
| 2026-05-17 |                                0 |                0 |                0 |                                    0 |                         0 |                                          0 |                                      0 |                              0 |                          0 |                                     0 |                                    0 |                                      0 |                                     0 |                               0 |                              0 |

## Included decision-log files

_No included decision-log files._

## Excluded decision-log files

_No excluded decision-log files._

## EP9M reconciliation

- No `setup_family=EP9M` rows were present in the included decision-log corpus for this run. If prior digests showed EP9M rows, compare the excluded-files table and discovery scope.
- EP9M context rows any-token: raw included=0, normalized included=0, master=0.

## Full audit CSV
- `/content/drive/MyDrive/bonde_screener_cache/learning_outputs/decision_log_discovery_audit_latest.csv`
