# Bonde repo operating instructions

## LLM Council artifact workflow

When running the `llm-council` skill for Bonde/trading council sessions:

1. Generate all six Council artifacts locally:
   - `council-report-*.html`
   - `council-transcript-*.md`
   - `council_outcomes_*.csv`
   - `council_disagreements_*.csv`
   - `council_self_calibration_summary_*.csv`
   - `council_reachability_audit_*.csv`

2. Ensure the four machine-readable CSVs are also present in:
   - `bonde_screener_cache/council_queues/`

   If that folder does not exist and the workspace is writable, create it with `mkdir -p`.

3. Commit and push the generated Council artifacts using the existing repo workflow when git is available.
   - Do not ask Kevin to manually upload `_inbox` files when commit/push succeeds.
   - Do not create or open a pull request for generated Council artifacts unless Kevin explicitly asks.
   - If the current branch is an existing Claude/artifact branch, push there.

4. Use manual `_inbox` fallback only if git push is unavailable or fails.
   If fallback is required, state the exact failure and list the exact local artifact paths.

5. The learning loop depends on the pushed machine-readable CSVs, especially:
   - `council_reachability_audit_*.csv`

The intended flow is: Council writes artifacts → Council pushes artifacts → learning loop reads artifacts. No manual file movement should be required in the normal path.
