---
name: llm-council
description: Run high-stakes decisions through 5 independent AI advisors, anonymized peer review, chairman verdict, optional Bonde outcome overlay, and structured trading council outcomes. Use for council this, run the council, pressure-test this, or meaningful tradeoffs. For Bonde trading councils, produce report, transcript, and council_outcomes CSV for learning-loop ingestion.
---
**Version: V1.3.4** (2026-05-17)

**Changelog**

- **V1.3.4 (2026-05-17)** — Create Missing Council Handoff Folder. Strengthens the V1.3.3 handoff rule: if the Bonde machine-readable handoff folder such as `bonde_screener_cache/council_queues/` does not exist but the workspace/repo root is writable, the Council must create it (`mkdir -p`) and write/copy **all four** machine-readable Council CSVs there: `council_outcomes_*`, `council_disagreements_*`, `council_self_calibration_summary_*`, and `council_reachability_audit_*`. A missing handoff directory is not by itself a reason for manual upload. Manual `_inbox` fallback is allowed only when the environment cannot create or write any learning-loop-visible handoff folder. No schema, verdict, routing, or trading-rule changes.

- **V1.3.3 (2026-05-17)** — Reachability Artifact Handoff Fix. Treats `council_reachability_audit_YYYY-MM-DD*.csv` as a first-class Bonde machine-readable Council artifact. The reachability audit must be written next to the report/transcript **and** copied/written to the same machine-readable handoff destination used for `council_outcomes`, `council_disagreements`, and `council_self_calibration_summary`, especially `bonde_screener_cache/council_queues/` when available. A Bonde Council run is incomplete if the existing Council CSVs reach the handoff folder but the reachability audit remains only in the local reports folder. No schema, verdict, routing, or trading-rule changes.

- **V1.3.2 (2026-05-17)** — Manual `_inbox` Handoff Clarification. Adds explicit low-complexity handoff instructions for environments where the Council skill cannot write directly to Google Drive. If workspace/Drive write access is unavailable, the Council must print each required CSV, especially `council_reachability_audit_YYYY-MM-DD.csv`, in a raw CSV code block and instruct Kevin to save/upload it to `/content/drive/MyDrive/bonde_learning/_inbox/`. No schema, verdict, routing, or artifact logic changes.

- **V1.3.1 (2026-05-17)** — Positive-Control Safety Clarification. Tightens the A1/A2 reachability audit so synthetic positive controls are sandbox-only and never injected into production candidate streams, daily decision logs, council outcomes, disagreement/calibration outputs, or learning-loop inputs. If the Council environment cannot execute an isolated routing harness, reachability must be reported as `NOT_EVALUABLE` or based only on actual-corpus evidence; hypothetical clean-row reasoning alone cannot claim `A1_REACHABLE=TRUE` or `A2_EXECUTABLE_REACHABLE=TRUE`.

- **V1.3 (2026-05-17)** — Council A1/A2 Reachability Audit + Zero-TRADE Cause Classification. Adds a mandatory Bonde/trading reachability audit that checks whether A1 and clean A2 outcomes are theoretically reachable, whether A2 rows are being forced to COUNCIL, and why post-cutover runs may produce zero TRADE rows. Adds `council_reachability_audit_YYYY-MM-DD.csv` as a sixth Bonde council artifact, plus report/transcript sections for `A1_REACHABLE`, `A2_EXECUTABLE_REACHABLE`, `ZERO_TRADE_CAUSE`, and top demotion reasons. Existing V1.1/V1.2 artifact schemas remain unchanged: `council_outcomes`, `council_disagreements`, and `council_self_calibration_summary` retain their canonical columns. This patch is diagnostic/reporting only; it does not lower A1/A2 thresholds, promote COUNCIL rows, or change the actionability skill.

- **V1.2 (2026-05-15)** — Context Audit + V5.9.19 Bonde Compatibility + Execution-Safety Guardrails. Adds mandatory `Context Files Loaded` audit section for Bonde/trading council runs; explicitly treats `final_trade_status` as the executable field and `tier` as source/dashboard focus tier only; adds Friday/weekend order-duration guardrail; requires portfolio heat aggregation for promoted candidates; tightens sector-correlation hygiene by separating direct sector exposure from broad risk-appetite exposure; adds Day-2 pullback rescue/base-rate warning when entry is lowered mainly to satisfy R:R. **No changes to V1.1 artifact names, CSV schemas, PROMOTE/DEFER/CANCEL verdict schema, disagreement tracker schema, or self-calibration scaffold.**

- **V1.2 path-compatibility note** — When a repo packet folder is named `bonde_files 3/`, treat it as equivalent to `bonde_files/` for current files, active context, learning context, and actionability playbook files.
- **V1.1 (2026-05-13)** — Reasoning Path Framing + Disagreement Tracker + Self-Calibration Scaffold. Replaced advisor "vote" language with "Reasoning Paths Considered" framing throughout. Renamed report sections "Where the Council Agrees / Clashes" to "Reasoning Path Convergence / Divergence" to clarify that multi-perspective output from one model is not statistical corroboration. Added `council_disagreements_YYYY-MM-DD.csv` output (computes `actionability_council_disagreement` at council-run time; `user_council_disagreement` starts PENDING for learning-loop resolution). Added `council_self_calibration_summary_YYYY-MM-DD.csv` output with strict 30/10 thresholds — no reliability percentages reported below threshold. **No council verdict rule changes. No trading rule changes.** Outputs follow the existing path convention (workspace + `bonde_screener_cache/council_queues/` for Bonde councils). The disagreement tracker honors the no-manual-process constraint: Kevin logs nothing by hand.
- **V1.0** — Initial skill: 5-advisor multi-perspective council, anonymous peer review, chairman verdict, optional Bonde outcome overlay, structured `council_outcomes_YYYY-MM-DD.csv` output.

---

You ask one AI a question, you get one answer. That answer might be great. It might be mid. You have no way to tell because you only saw one perspective.
The council fixes this. It runs your question through 5 independent advisors, each thinking from a fundamentally different angle. Then they review each other's work. Then a chairman synthesizes everything into a final recommendation that tells you where the advisors agree, where they clash, and what you should actually do.
This is adapted from Andrej Karpathy's LLM Council. He dispatches queries to multiple models, has them peer-review each other anonymously, then a chairman produces the final answer. We do the same thing inside Claude using sub-agents with different thinking lenses instead of different models.

when to run the council
The council is for questions where being wrong is expensive.
Good council questions:

"Should I launch a $97 workshop or a $497 course?"
"Which of these 3 positioning angles is strongest?"
"I'm thinking of pivoting from X to Y. Am I crazy?"
"Here's my landing page copy. What's weak?"
"Should I hire a VA or build an automation first?"

Bad council questions:

"What's the capital of France?" (one right answer, no need for perspectives)
"Write me a tweet" (creation task, not a decision)
"Summarize this article" (processing task, not judgment)

The council shines when there's genuine uncertainty and the cost of a bad call is high. If you already know the answer and just want validation, the council will likely tell you things you don't want to hear. That's the point.

the five advisors
Each advisor thinks from a different angle. They're not job titles or personas. They're thinking styles that naturally create tension with each other.
1. The Contrarian
Actively looks for what's wrong, what's missing, what will fail. Assumes the idea has a fatal flaw and tries to find it. If everything looks solid, digs deeper. The Contrarian is not a pessimist. They're the friend who saves you from a bad deal by asking the questions you're avoiding.
2. The First Principles Thinker
Ignores the surface-level question and asks "what are we actually trying to solve here?" Strips away assumptions. Rebuilds the problem from the ground up. Sometimes the most valuable council output is the First Principles Thinker saying "you're asking the wrong question entirely."
3. The Expansionist
Looks for upside everyone else is missing. What could be bigger? What adjacent opportunity is hiding? What's being undervalued? The Expansionist doesn't care about risk (that's the Contrarian's job). They care about what happens if this works even better than expected.
4. The Outsider
Has zero context about you, your field, or your history. Responds purely to what's in front of them. This is the most underrated advisor. Experts develop blind spots. The Outsider catches the curse of knowledge: things that are obvious to you but confusing to everyone else.
5. The Executor
Only cares about one thing: can this actually be done, and what's the fastest path to doing it? Ignores theory, strategy, and big-picture thinking. The Executor looks at every idea through the lens of "OK but what do you do Monday morning?" If an idea sounds brilliant but has no clear first step, the Executor will say so.
Why these five: They create three natural tensions. Contrarian vs Expansionist (downside vs upside). First Principles vs Executor (rethink everything vs just do it). The Outsider sits in the middle keeping everyone honest by seeing what fresh eyes see.

how a council session works
step 1: frame the question (with context enrichment)
When the user says "council this" (or any trigger phrase), do two things before framing:
A. Scan the workspace for context. The user's question is often just the tip of the iceberg. Their Claude setup likely contains files that would dramatically improve the council's output. Before framing, quickly scan for and read any relevant context files:

CLAUDE.md or claude.md in the project root or workspace (business context, preferences, constraints)
Any memory/ folder (audience profiles, voice docs, business details, past decisions)
Any files the user explicitly referenced or attached
Recent council transcripts in this folder (to avoid re-counciling the same ground)
Any other context files that seem relevant to the specific question (e.g., if they're asking about pricing, look for revenue data, past launch results, audience research)

For Bonde/trading/B+ council questions, also look for outcome/base-rate and current-context files if available:

bonde_files/README_BONDE_FILES.md, if present
bonde_files/current/council_queue_*.csv
bonde_files/current/daily_decision_log_*.csv
bonde_files/current/bonde_skill_pack_*.csv
bonde_files/active_context/council_context_manifest.md
bonde_files/active_context/latest_candidate_context.md
bonde_files/active_context/latest_learning_context.md
bonde_files/active_context/latest_market_context.md, if present
bonde_files/playbook/bonde_stockbee_actionability/SKILL.md

If the repo uses a numbered Bonde packet folder, treat it as equivalent to `bonde_files/` and scan it too:

bonde_files 3/current/council_queue_*.csv
bonde_files 3/current/daily_decision_log_*.csv
bonde_files 3/current/bonde_skill_pack_*.csv
bonde_files 3/active_context/council_context_manifest.md
bonde_files 3/active_context/latest_candidate_context.md
bonde_files 3/active_context/latest_learning_context.md
bonde_files 3/active_context/latest_market_context.md, if present
bonde_files 3/learning/*.csv or *.md
bonde_files 3/playbook/bonde_stockbee_actionability/SKILL.md
skill_pack_performance_report_v410.md or similar
weekly_learning_report_*.md
reviewed_vs_unreviewed_summary*.csv
bplus_council_outcome_summary*.csv
council_queue_*.csv
prior council-report-*.html or council-transcript-*.md
skill_pack_ticker_outcomes_enriched*.csv or decision/outcome summaries

For Bonde/trading council runs, record exactly which context files were found and used. The report and transcript must include a `Context Files Loaded` section. Missing optional context files are allowed, but missing current candidate files or missing current council queue/decision log context must be stated clearly.

Use Glob and quick Read calls to find these. Don't spend more than 30 seconds on this. You're looking for the 2-3 files that would give advisors the context they need to give specific, grounded advice instead of generic takes.

B. Build outcome/base-rate context when relevant. Outcome data is optional, but if it exists it must be summarized before the advisors evaluate the question. For trading/Bonde/B+ questions, summarize:

Outcome data available: yes/no
Relevant setup-family base rate, if available
Relevant B+ blocker type base rate, if available: C1 wide Day-1/R:R floor fail, C2 DTE/pre-earnings tactical setup, C3 mild-extension/Day-2 confirmation
Prior council promote/defer/cancel outcomes, if available
+1D / +5D returns, MFE/MAE, trigger-hit rate, or conversion rate from B+ to valid A2, if available
Whether prior cancellations saved money or missed winners, if available

If no relevant outcome data is found, state exactly in the framed question: "Outcome data unavailable; verdict is playbook-only and should be logged for future calibration."

Outcome data is an overlay, not permission to violate hard rules. For Bonde/trading decisions, do not override hard rejects such as bag-holder, failed EP, DTE unknown, DTE hard reject, dilution/offering, deal-pinned/merger-arb, or severe extension without reset unless the main Bonde playbook has formally changed the rule.

C. Frame the question. Take the user's raw question, the enriched context, and any outcome/base-rate context and reframe it as a clear, neutral prompt that all five advisors will receive. The framed question should include:

The core decision or question
Key context from the user's message
Key context from workspace files (business stage, audience, constraints, past results, relevant numbers)
Outcome/base-rate context, or the explicit note that none is available
What's at stake (why this decision matters)

Don't add your own opinion. Don't steer it. But DO make sure each advisor has enough context to give a specific, grounded answer rather than generic advice.
If the question is too vague ("council this: my business"), ask one clarifying question. Just one. Then proceed.
Save the framed question and outcome/base-rate context for the transcript.

step 1.2: Bonde V5.9.19 context and execution-safety normalization

For Bonde/trading council runs, normalize the current context before advisors evaluate candidates.

A. Context files loaded audit

Create a `Context Files Loaded` audit list with these fields per file:

- `file_role` — e.g., council_queue, daily_decision_log, skill_pack, candidate_context, learning_context, manifest, actionability_skill, prior_council.
- `path` — actual path used.
- `status` — LOADED, MISSING_OPTIONAL, MISSING_REQUIRED, or STALE.
- `notes` — version/date caveats.

The audit must appear in the HTML report and markdown transcript. For Bonde runs, the chairman must not merely imply context. It must state what was loaded.

Required or strongly expected Bonde files:

- `council_queue_*.csv` for candidates routed to council.
- `daily_decision_log_*.csv` when available, especially for `final_trade_status`.
- `bonde_skill_pack_*.csv` when available, for source signal evidence.
- `latest_candidate_context.md` and `latest_learning_context.md` when the repo context manager is used.
- `council_context_manifest.md` when present.
- `bonde_stockbee_actionability/SKILL.md` or equivalent current actionability skill. If missing, state that the council is operating from the candidate packet and embedded playbook rules, not a fully auditable skill package.

Optional context files such as `latest_market_context.md`, `latest_regime_context.md`, `latest_accountability_context.md`, and `latest_skill_context.md` are not required unless the current repo manifest explicitly requires them. If `latest_market_context.md` is listed as LOADED in `council_context_manifest.md`, read it and summarize its tactical market implications in Outcome/Base-Rate Context or Portfolio Heat; do not treat it as a hard trade gate.

B. V5.9.19 decision-field semantics

For Bonde V5.9.19 and later:

- `final_trade_status` is the executable field.
- `tier` is source/dashboard focus tier only.
- `tier=TAKE` does not mean trade authorization.
- Plain `B` is watch-only unless explicitly routed to council.
- `B+` / `C1` / `C2` / `C3` / `final_trade_status=COUNCIL` means the candidate is a judgment-review candidate, not an automatic trade.
- If `final_trade_status` is unavailable because the log is pre-V5.9.19, state that the council is using backward-compatible action-label inference.

Do not promote a candidate solely because `tier=TAKE`. The chairman must reference the actual actionable field or its fallback.

C. Friday / weekend exposure guardrail

If the review date is Friday, or the next market session is separated by a weekend or holiday gap:

- Do not casually recommend open-ended GTC orders.
- Default to DAY orders or cancel-before-close instructions unless the user explicitly accepts overnight/weekend exposure.
- If GTC is still recommended, state why the weekend/holiday exposure is intentional and how the order should be canceled or resized if conditions change.
- Include weekend gap risk in the execution section for any promoted candidate.

D. Portfolio heat aggregation

For every Bonde/trading chairman synthesis with one or more PROMOTE verdicts, include a `Portfolio Heat` subsection stating:

- proposed risk per promoted ticker when available;
- total proposed R if all promoted entries fill;
- sector/theme overlap;
- maximum correlated exposure;
- which order fills cancel or resize other orders;
- what market/candidate event invalidates the basket.

If exact account-risk numbers are unavailable, use qualitative heat labels and explicitly say that exact account-risk sizing was unavailable.

E. Sector-correlation hygiene

Separate direct sector/industry correlation from broad risk-appetite correlation.

- Direct sector correlation: same industry/theme, e.g., JBHT/WERN trucking.
- Broad risk-appetite correlation: unrelated growth/cyclical names that may move together during risk-on/risk-off tape.
- Do not claim one unrelated ticker directly gates another unrelated industry unless the linkage is explicit and defensible.
- If a ticker only affects the broader tape, say "broad risk-appetite read-through," not direct sector correlation.

F. Day-2 pullback rescue warning

If a candidate becomes valid mainly because the entry is lowered until R:R passes, label it as `Day-2 pullback rescue`.

For such candidates:

- State whether mature base-rate data exists for that rescue path.
- If no mature base-rate exists, verdict is playbook-only.
- Do not describe R:R rescue as proven edge.
- Require clean thesis preservation: if the pullback needed to satisfy R:R would also damage the catalyst/setup thesis, prefer DEFER or CANCEL.


step 1.3: Bonde Council A1/A2 reachability and zero-TRADE audit (V1.3)

For every Bonde/trading council run, and especially when the current decision log shows zero `TRADE` rows, no `A1` rows, or all visible `A2` rows routed to `COUNCIL`, run a diagnostic reachability audit before advisors evaluate candidates.

This audit is not a trading-rule change. It is a Council-skill sanity check that answers whether the current council/actionability interface can produce executable A1/A2 paths at all, and if not, why.

A. Inputs to inspect

Use the same context files loaded in Step 1.2, especially:

- `council_queue_*.csv`
- `daily_decision_log_*.csv`
- `bonde_skill_pack_*.csv`
- `latest_candidate_context.md`
- `latest_learning_context.md`
- the current actionability skill/playbook when available

If the necessary fields are missing, set the audit status to `NOT_EVALUABLE` rather than guessing.

B. Required reachability questions

The audit must answer these questions in the report and transcript:

1. `A1_REACHABLE` — can a clean, fully valid row theoretically route to `action_label=A1` under the current Council/actionability interface?
2. `A2_EXECUTABLE_REACHABLE` — can a clean A2 row route to an executable status, or does every A2 path force `final_trade_status=COUNCIL`?
3. `ZERO_TRADE_CAUSE` — if recent rows have zero `TRADE`, classify the likely cause.
4. `TOP_DEMOTION_REASONS` — for A1/A2 or near-A1/A2 rows that did not become executable, list the main demotion/override reasons.
5. `ROUTING_OVERRIDE_FIELD` — identify the field or rule layer that overrode the row if detectable, e.g. `final_trade_status`, `council_verdict`, `hard_reject_reason`, `rr_floor_fail`, `dte_guardrail`, `data_missing`, or `unknown`.

Allowed values:

- `A1_REACHABLE`: `TRUE`, `FALSE`, `NOT_EVALUABLE`
- `A2_EXECUTABLE_REACHABLE`: `TRUE`, `FALSE`, `NOT_EVALUABLE`
- `ZERO_TRADE_CAUSE`: `BUG_SUSPECTED`, `INTENTIONAL_STRICTNESS`, `INSUFFICIENT_CLEAN_ROWS`, `DATA_MISSING`, `NOT_EVALUABLE`, `NO_ZERO_TRADE_ISSUE`

C. Positive-control rows — sandbox-only

Positive controls are allowed only as an isolated reachability test. They must never be injected into production candidate streams, `daily_decision_log`, `council_queue`, `council_outcomes`, `council_disagreements`, `council_self_calibration_summary`, learning-loop candidate tables, weekly cohort reports, or any live recommendation artifact.

Use this evidence hierarchy:

1. **Actual-corpus evidence** — real A1/A2 rows and their observed routing in the loaded decision log / council queue.
2. **Isolated routing harness evidence** — synthetic positive controls executed in a sandbox/in-memory harness that cannot write to production artifacts.
3. **Playbook-only inference** — reading rules without executing routing. This may identify likely blockers, but it cannot prove reachability.

Only use synthetic positive controls when the current actionability/council routing logic is actually executable or faithfully emulatable in isolation. If no isolated harness is available, do not fabricate a pass/fail result. Set the relevant reachability fields to `NOT_EVALUABLE` unless actual-corpus evidence already proves the route.

Minimum positive controls, when sandbox execution is available:

- `CLEAN_A1_POSITIVE_CONTROL`: clean setup, valid trigger, valid invalidation, acceptable R:R, no hard rejects, no DTE/earnings guardrail, sufficient liquidity, no bag-holder/failed-EP/dilution/deal-pinned flags, and strong actionability evidence.
- `CLEAN_A2_POSITIVE_CONTROL`: similar to A1 but with slightly lower quality or one mild council-review reason; should still demonstrate whether executable A2 routing is possible when no hard reject exists.

Expected interpretation:

- If actual-corpus rows prove A1 or A2 executable routing exists, reachability may be `TRUE` even without synthetic controls.
- If sandbox positive controls prove the route, reachability may be `TRUE` and the reachability audit must state `audit_basis=SANDBOX_POSITIVE_CONTROL`.
- If a clean A1 positive-control row cannot produce A1 or any executable status in an isolated harness, set `A1_REACHABLE=FALSE` and `ZERO_TRADE_CAUSE=BUG_SUSPECTED` unless the playbook explicitly says A1 is disabled.
- If a clean A2 positive-control row always becomes `COUNCIL` by design in an isolated harness, set `A2_EXECUTABLE_REACHABLE=FALSE` and classify as `INTENTIONAL_STRICTNESS` only if the playbook explicitly documents A2 as council-only. Otherwise classify as `BUG_SUSPECTED` or `DATA_MISSING` depending on evidence.
- If the current environment cannot execute or faithfully emulate routing logic, set the relevant reachability fields to `NOT_EVALUABLE` and explain what is missing. Do not mark reachability `TRUE` from hypothetical clean-row reasoning alone.

D. Actual-corpus audit

For actual rows in the loaded decision log / council queue:

- Count `A1`, `A2`, `TRADE`, `COUNCIL`, `WATCH`, and `REJECT` rows.
- Count `A1/A2 -> TRADE`, `A1/A2 -> COUNCIL`, `A1/A2 -> WATCH`, and `A1/A2 -> REJECT` routes.
- For every actual `A1` or `A2` row reviewed by council, capture the demotion reason if it did not remain executable.
- For rows that appear near-executable but are demoted, capture the first blocking reason visible in the source fields or decision text.

Do not treat “few trades” alone as a bug. Only classify `BUG_SUSPECTED` when the positive controls or rule precedence indicate an unreachable/contradictory route.

E. Chairman use of the audit

The Chairman must use this audit as context only. The audit can justify a diagnostic recommendation such as “fix A1/A2 reachability before changing thresholds,” but it must not promote a live ticker merely because the system is too conservative.

If the audit finds `A1_REACHABLE=FALSE` or `A2_EXECUTABLE_REACHABLE=FALSE`, the Chairman must explicitly state that the issue is an implementation/routing investigation, not proof that thresholds should be relaxed.

step 2: convene the council (5 sub-agents in parallel)
Spawn all 5 advisors simultaneously as sub-agents. Each gets:

Their advisor identity and thinking style (from the descriptions above)
The framed question
A clear instruction: respond independently. Do not hedge. Do not try to be balanced. Lean fully into your assigned perspective. If you see a fatal flaw, say it. If you see massive upside, say it. Your job is to represent your angle as strongly as possible. The synthesis comes later.

Each advisor should produce a response of 150-300 words. Long enough to be substantive, short enough to be scannable.
Sub-agent prompt template:

You are [Advisor Name] on an LLM Council.


Your thinking style: [advisor description from above]


A user has brought this question to the council:


---

[framed question, including any outcome/base-rate context]

---


Respond from your perspective. Be direct and specific. Don't hedge or try to be balanced. Lean fully into your assigned angle. The other advisors will cover the angles you're not covering.

If outcome/base-rate context is available, use it explicitly. If it is unavailable, state that your view is playbook-only and should be logged for calibration. Do not use weak or immature outcome data to justify breaking hard rules.

For Bonde/trading questions, include one of: promote / defer / cancel, plus confidence and whether the verdict is evidence-backed or playbook-only. Respect V5.9.19 semantics: `final_trade_status` is executable, `tier` is not. If a Day-2 pullback only works because entry was lowered to rescue R:R, call that out explicitly. If review timing creates Friday/weekend/holiday gap risk, include that execution risk.

Keep your response between 150-300 words. No preamble. Go straight into your analysis.
step 3: peer review (5 sub-agents in parallel)
This is the step that makes the council more than just "ask 5 times." It's the core of Karpathy's insight.
Collect all 5 advisor responses. Anonymize them as Response A through E (randomize which advisor maps to which letter so there's no positional bias).
Spawn 5 new sub-agents, one for each advisor. Each reviewer sees all 5 anonymized responses and answers three questions:

Which response is the strongest and why? (pick one)
Which response has the biggest blind spot and what is it?
What did ALL responses miss that the council should consider?

Reviewer prompt template:

You are reviewing the outputs of an LLM Council. Five advisors independently answered this question:


---

[framed question]

---


Here are their anonymized responses:


**Response A:**

[response]


**Response B:**

[response]


**Response C:**

[response]


**Response D:**

[response]


**Response E:**

[response]


Answer these four questions. Be specific. Reference responses by letter.


1. Which response is the strongest? Why?

2. Which response has the biggest blind spot? What is it missing?

3. Did any response misuse, ignore, or overfit the outcome/base-rate context?

4. What did ALL five responses miss that the council should consider?


Keep your review under 220 words. Be direct.
step 4: chairman synthesis
This is the final step. One agent gets everything: the original question, all 5 advisor responses (now de-anonymized so you can see which advisor said what), and all 5 peer reviews.
The chairman's job is to produce the final council output. It follows this structure:
COUNCIL VERDICT

Where the council agrees — the points that multiple advisors converged on independently. These are high-confidence signals.
Where the council clashes — the genuine disagreements. Don't smooth these over. Present both sides and explain why reasonable advisors disagree.
Blind spots the council caught — things that only emerged through the peer review round. Things individual advisors missed that other advisors flagged.
The recommendation — a clear, actionable recommendation. Not "it depends." Not "consider both sides." A real answer. The chairman can disagree with the majority if the reasoning supports it.
The one thing you should do first — a single concrete next step. Not a list of 10 things. One thing.

Chairman prompt template:

You are the Chairman of an LLM Council. Your job is to synthesize the work of 5 advisors and their peer reviews into a final verdict.


The question brought to the council:

---

[framed question]

---


ADVISOR RESPONSES:


**The Contrarian:**

[response]


**The First Principles Thinker:**

[response]


**The Expansionist:**

[response]


**The Outsider:**

[response]


**The Executor:**

[response]


PEER REVIEWS:

[all 5 peer reviews]


Produce the council verdict using this exact structure:


## Context Files Loaded

[For Bonde/trading runs, list the concrete files used with role, path, and status. Include council_queue, daily_decision_log, skill_pack, active context files, manifest, actionability skill, and prior council/outcome files when present. State missing optional files as optional; state missing required/current files as limitations. For non-Bonde questions, write N/A unless context files were used.]


## Council self-calibration status

[State the self-calibration status from the most recent `council_self_calibration_summary_YYYY-MM-DD.csv` if available. One of: `UNAVAILABLE` (no history file), `INSUFFICIENT_DATA` (fewer than 30 resolved disagreements), `BUILDING_SAMPLE` (≥30 total but slice thresholds not met), `CALIBRATED` (thresholds met). If CALIBRATED, state aggregate council accuracy with sample size. If not CALIBRATED, state "no reliability percentage reported." See step 7.7 for thresholds. Self-calibration is context only and does NOT change verdicts.]


## A1/A2 Reachability Audit

[For Bonde/trading runs, summarize the V1.3 reachability audit: `A1_REACHABLE`, `A2_EXECUTABLE_REACHABLE`, `ZERO_TRADE_CAUSE`, actual A1/A2/TRADE counts, top demotion reasons, and whether the audit was based on positive-control routing, actual-corpus routing, or was `NOT_EVALUABLE` because required fields/routing code were missing. State explicitly if A1/A2 reachability is an implementation investigation rather than a threshold-change recommendation. For non-Bonde questions, write N/A.]


## Outcome/Base-Rate Context

[State whether outcome data was available. Summarize relevant base rates, sample sizes, +1D/+5D, MFE/MAE, trigger-hit or conversion data if available. If unavailable, write: "Outcome data unavailable; verdict is playbook-only and should be logged for future calibration."]


## Reasoning Paths Considered

**Note:** The council uses multiple reasoning paths generated in one process. **These are not independent votes.** Convergence is useful as a reasoning check, not as statistical corroboration. Four perspectives reaching the same conclusion is one model exploring the same conclusion four times, not four independent verdicts. Use convergence to test whether a position survives different framings; do not treat it as evidence of statistical strength.

### Reasoning Path Convergence

[Points multiple reasoning paths converged on independently. These are positions that survived examination from different framings. Useful as a robustness check, NOT as a vote count. Do not use "4 of 5", "5 of 5", "X advisors voted", "majority", "consensus" or similar statistical-corroboration language. Use prose: "The Contrarian, First Principles, and Executor paths each arrived at X, by different routes — the Contrarian via risk framing, First Principles via problem reframing, Executor via execution feasibility."]

### Reasoning Path Divergence

[Genuine disagreements between reasoning paths. Present both sides. Explain why each path produced its conclusion. Frame as "The Expansionist path argued for X because Y; the Contrarian path rejected this because Z" — not as votes.]

### Blind Spots the Reasoning Paths Caught

[Things that only emerged through peer review. Things one reasoning path missed that another flagged. Frame as "The Outsider path caught X that the other paths missed because they assumed Y."]


## Chairman Synthesis

[The Chairman weighs the reasoning paths against each other and produces ONE verdict. The Chairman is not bound by which path "won" — a single dissenting path may carry the verdict if its reasoning is strongest. State explicitly which paths were weighted and why. Example: "The Chairman weighted the Contrarian path's risk framing against the Expansionist path's upside argument and concluded DEFER because the immediate execution geometry does not yet exist." For Bonde/trading candidates, state promote / defer / cancel, confidence, and whether the recommendation is evidence-backed or playbook-only. Apply V5.9.19 semantics: `final_trade_status` is executable, `tier` is not. If the decision relies on backward-compatible inference because `final_trade_status` is missing, say so.]


## Portfolio Heat

[For Bonde/trading runs with any PROMOTE verdict, state proposed risk per promoted ticker if available, total proposed R if all entries fill, sector/theme overlap, maximum correlated exposure, order-cancel/resize dependencies, and what invalidates the basket. If no PROMOTE verdicts, write "No promoted exposure." If exact account risk is unavailable, say so and use qualitative heat labels.]


## The One Thing to Do First

[A single concrete next step. Not a list. One thing.]


## Council Outcome CSV Draft

[For Bonde/trading/B+ questions only, summarize the rows that will be written to council_outcomes_YYYY-MM-DD.csv using the Step 7 schema: signal_date,review_date,ticker,setup_family,action_label,bplus_blocker_type,council_verdict,confidence,decision_reason,report_path,transcript_path. Use council_verdict only as PROMOTE, DEFER, or CANCEL. If not a trading/B+ question, write N/A.]


Be direct. Don't hedge. The whole point of the council is to give the user clarity they couldn't get from a single perspective.

**Forbidden vote-count language anywhere in the report or transcript:** "4 of 5", "5 of 5", "3 of 5", "X advisors voted", "advisor consensus" used as statistical evidence, "majority of advisors", "agreement matrix" as a header. Acceptable: "reasoning paths converged on X", "the Contrarian and First Principles paths reached Y by different routes", "all five reasoning paths arrived at Z" (this is description, not vote-counting). The Chairman synthesis CAN reference which paths concluded what, as long as it does not frame this as votes.
step 5: generate the council report
After the chairman synthesis is complete, generate a visual HTML report and save it to the user's workspace.
File: council-report-[timestamp].html
The report should be a single self-contained HTML file with inline CSS. Clean design, easy to scan. It should contain:

The question at the top
The outcome/base-rate context prominently displayed when relevant
For Bonde/trading runs, a `Context Files Loaded` section showing concrete file roles, paths, and status
The chairman's verdict prominently displayed (this is what most people will read)
For Bonde/trading runs with promoted candidates, a `Portfolio Heat` section showing risk, correlation, order dependencies, and weekend/holiday guardrails when relevant
For Bonde/trading runs, an `A1/A2 Reachability Audit` section showing A1 reachability, A2 executable reachability, zero-TRADE cause, and top demotion reasons
A "Reasoning Paths Considered" visual — a clean breakdown showing how each reasoning path framed the question and what conclusion it reached. NOT a vote tally. NOT an "agreement matrix" as statistical corroboration. Frame as "Convergence and Divergence of Reasoning Paths" or similar. Include the explicit disclaimer near the visual: "These are not independent votes. Convergence is useful as a reasoning check, not as statistical corroboration." Keep it clean and scannable. The visual MUST NOT use "vote", "4 of 5", or similar language anywhere in its labels or annotations.
Collapsible sections for each advisor's full response (collapsed by default so the page isn't overwhelming, but available if the user wants to dig in)
Collapsible section for the peer review highlights
A footer showing the timestamp and what was counciled

Use clean styling: white background, subtle borders, readable sans-serif font (system font stack), soft accent colors to distinguish advisor sections. Nothing flashy. It should look like a professional briefing document.
Open the HTML file after generating it so the user can see it immediately.
step 6: save the full transcript
Save the complete council transcript as council-transcript-[timestamp].md in the same location. This includes:

The original question
The framed question
The context files loaded audit for Bonde/trading runs
The outcome/base-rate context used or the statement that no outcome data was available
The A1/A2 reachability audit for Bonde/trading runs, including positive-control status where evaluated
All 5 advisor responses
All 5 peer reviews (with anonymization mapping revealed)
The chairman's full synthesis
The portfolio heat section for Bonde/trading runs with promoted exposure

This transcript is the artifact. If the user wants to run the council again on the same question after making changes, having the previous transcript lets them (or a future agent) see how the thinking evolved.


step 7: save structured Bonde council outcomes CSV
For every Bonde/trading council run, generate a machine-readable CSV in addition to the HTML report and markdown transcript.

File name:
council_outcomes_YYYY-MM-DD.csv

The date should be the review date in YYYY-MM-DD format. If the session covers multiple signal dates, still use the review date in the filename and keep the true signal date per row.

Save the CSV next to the council report and transcript. If the workspace has a Bonde repo or cache folder, also copy or write the CSV to the current council queue folder when available:
bonde_screener_cache/council_queues/

Required schema, exact column order:
signal_date,review_date,ticker,setup_family,action_label,bplus_blocker_type,council_verdict,confidence,decision_reason,report_path,transcript_path

Rules:
- One row per ticker reviewed by council.
- Quote every text field.
- Do not use markdown table formatting for the CSV.
- The CSV must parse cleanly with `pandas.read_csv()` — no stray markdown fences, no trailing commentary, no unescaped embedded quotes.
- Keep `decision_reason` concise and machine-readable. Quoting handles commas; do not omit them at the cost of clarity.
- Include the report and transcript paths actually written in this session.

`council_verdict` must be exactly one of: PROMOTE, DEFER, CANCEL.

Internal verdict language must be normalized to one of the three allowed values before writing. Use this exact mapping:

- PROMOTE_FULL → PROMOTE
- PROMOTE_HALF → PROMOTE
- PROMOTE_ON_TRIGGER → PROMOTE
- DEFER_DAY2_ALERT → DEFER
- DEFER_DAY2_ALERT_LOW_PRIORITY → DEFER
- DEFER_CONDITIONAL → DEFER
- CANCEL → CANCEL

Any other internal verdict string must be normalized to its closest match in {PROMOTE, DEFER, CANCEL} before writing. Never write the un-normalized variant into the CSV. Variant-level nuance (full vs half, on-trigger, day-2-alert) belongs in `decision_reason`, not in `council_verdict`.

`bplus_blocker_type` must be exactly one of: C1, C2, C3, NOT_BPLUS, UNKNOWN.

- C1 = wide Day-1 range / static EOD R:R floor fail
- C2 = DTE / pre-earnings tactical setup
- C3 = mild or moderate extension / Day-2 confirmation requirement
- NOT_BPLUS = A1/A2 or any non-B+ row reviewed by council
- UNKNOWN = source prompt does not identify the blocker and it cannot be inferred safely

Rules for `bplus_blocker_type`:
- A2/A1 rows use NOT_BPLUS.
- B+ C1 rows use C1.
- B+ C2 rows use C2.
- B+ C3 rows use C3.
- If the row is B+ but the blocker is not identifiable, use UNKNOWN. Never leave the field blank.

Example CSV:
```csv
"signal_date","review_date","ticker","setup_family","action_label","bplus_blocker_type","council_verdict","confidence","decision_reason","report_path","transcript_path"
"2026-05-08","2026-05-09","BILL","EP_ACTIVE","A2","NOT_BPLUS","PROMOTE","high","A2 all gates clean; R:R 3.05; multi-catalyst; 4/5 advisors promote.","/home/user/bonde/.claude/skills/llm-council/reports/council-report-20260509-batch.html","/home/user/bonde/.claude/skills/llm-council/reports/council-transcript-20260509-batch.md"
"2026-05-08","2026-05-09","CALY","EP_ACTIVE","B","C1","DEFER","medium","B+ C1; R:R floor fail; Day-2 trigger plus recomputed R:R >= 2.0 required.","/home/user/bonde/.claude/skills/llm-council/reports/council-report-20260509-batch.html","/home/user/bonde/.claude/skills/llm-council/reports/council-transcript-20260509-batch.md"
"2026-05-08","2026-05-09","DBX","EP_ACTIVE","B","C1","CANCEL","high","B+ C1 but NI -24% YoY and R:R 1.24 vs 52w cap; remove from screen.","/home/user/bonde/.claude/skills/llm-council/reports/council-report-20260509-batch.html","/home/user/bonde/.claude/skills/llm-council/reports/council-transcript-20260509-batch.md"
```

If the council reviews multiple tickers in one batch, produce one consolidated CSV for the batch. If the council reviews one ticker, produce one CSV with one row.

Acceptance tests (a Bonde trading council run is not complete until all of these pass):

1. `council_outcomes_YYYY-MM-DD.csv` is written after the run, in the same reports folder as the HTML report and markdown transcript.
2. CSV has exactly 11 columns in this order: signal_date, review_date, ticker, setup_family, action_label, bplus_blocker_type, council_verdict, confidence, decision_reason, report_path, transcript_path.
3. `council_verdict` contains only PROMOTE, DEFER, or CANCEL — no PROMOTE_FULL/PROMOTE_HALF/PROMOTE_ON_TRIGGER/DEFER_DAY2_ALERT/DEFER_DAY2_ALERT_LOW_PRIORITY/DEFER_CONDITIONAL or any other variant.
4. `bplus_blocker_type` contains only C1, C2, C3, NOT_BPLUS, or UNKNOWN — no blanks, no other strings.
5. Every A2/A1 row has `bplus_blocker_type` = NOT_BPLUS.
6. Every B+ row preserves its C1/C2/C3 blocker when known; if unknown, UNKNOWN.
7. The CSV parses cleanly with `pandas.read_csv()` and yields one row per reviewed ticker with no parse errors.
8. `report_path` and `transcript_path` point to the HTML and markdown files actually written in this same run.
9. Existing HTML report generation (step 5) and markdown transcript generation (step 6) still work unchanged.

If any acceptance test fails, fix it before reporting the run complete. Do not silently emit a malformed CSV.


step 7.5: write council disagreement tracker CSV (V1.1)

For every Bonde/trading council run, in addition to council_outcomes_*.csv, write `council_disagreements_YYYY-MM-DD.csv` to the same location.

**Always write the file.** If no disagreements exist, write a header-only CSV. Do not skip emission.

**Definition of disagreement (V1.1):**

Two distinct types, tracked separately:

1. **`actionability_council_disagreement`** — the council verdict differs from the original actionability label on the same ticker. The council skill CAN determine this at run time because both inputs are visible (council_queue row's `action_label` from the actionability skill, and the council's own verdict).

2. **`user_council_disagreement`** — the council verdict differs from Kevin's final actual decision. The council skill CANNOT determine this at run time because Kevin's final action happens AFTER the council session. This field starts as `UNKNOWN`/`PENDING` and is resolved later by the learning loop (out of scope for this skill patch).

**No manual logging is required.** The council skill writes whatever it knows at run time. Outcome fields and user-decision fields are explicitly PENDING and are resolved downstream.

**Required schema (V1.1, exact column order, 22 columns, header has 21 commas):**

`run_date,review_date,signal_date,ticker,setup_family,primary_setup,action_label,planned_size,council_verdict,council_confidence,council_size_recommendation,user_final_decision,user_final_size,user_council_disagreement,actionability_council_disagreement,agreement_type,rationale_diverged_on,council_primary_reason,outcome_status,outcome_class,council_outcome_alignment,resolution_notes`

**Note on schema design vs the V1.1 prompt:** The prompt originally specified a single `council_was_right` field. V1.1 implementation splits this into two unambiguous fields — `outcome_class` (what happened to the setup) and `council_outcome_alignment` (whether the verdict matched the outcome). This avoids the contingency ambiguity where DEFER + winner + user-also-defers can be scored "right" or "wrong" depending on interpretation. The two-field design makes every cell of the contingency table unambiguous.

**Column semantics:**

| Column | Allowed values | Source |
|---|---|---|
| `run_date` | YYYY-MM-DD | Today's date |
| `review_date` | YYYY-MM-DD | From council_outcomes row |
| `signal_date` | YYYY-MM-DD | From council_outcomes row |
| `ticker` | string | From council_outcomes row |
| `setup_family` | string | From council_outcomes row |
| `primary_setup` | string | From council_queue / decision log |
| `action_label` | `A1`/`A2`/`B`/`C`/`D` | From council_queue / decision log (actionability's verdict) |
| `planned_size` | string | From council_queue / decision log |
| `council_verdict` | `PROMOTE`/`DEFER`/`CANCEL` | From council_outcomes row |
| `council_confidence` | `low`/`medium`/`medium-high`/`high` | From council_outcomes row |
| `council_size_recommendation` | string or blank | If council suggested a specific size (`full`, `half`, `none`, etc.); blank otherwise |
| `user_final_decision` | `TRADED`/`SKIPPED`/`DEFERRED`/`REDUCED_SIZE`/`INCREASED_SIZE`/`UNKNOWN` | **Always `UNKNOWN` at council-run time** — resolved later by learning loop |
| `user_final_size` | string or `UNKNOWN` | **Always `UNKNOWN` at council-run time** |
| `user_council_disagreement` | `TRUE`/`FALSE`/`UNKNOWN` | **Always `UNKNOWN` at council-run time** |
| `actionability_council_disagreement` | `TRUE`/`FALSE` | **Computed at council-run time** by comparing `action_label` against `council_verdict`. See classification rules below. |
| `agreement_type` | `FULL_AGREEMENT`/`USER_DISAGREED_WITH_COUNCIL`/`ACTIONABILITY_DISAGREED_WITH_COUNCIL`/`BOTH_DISAGREED`/`PENDING_USER_RESOLUTION` | Set to `ACTIONABILITY_DISAGREED_WITH_COUNCIL` if actionability_council_disagreement=TRUE; otherwise `PENDING_USER_RESOLUTION` (because user decision is still pending). Final value resolved later. |
| `rationale_diverged_on` | string | If actionability_council_disagreement=TRUE, one-sentence reason. Blank otherwise. |
| `council_primary_reason` | string | One-sentence council primary reason. Sourced from `decision_reason` in council_outcomes. |
| `outcome_status` | `PENDING` always at write time | Resolved by learning loop |
| `outcome_class` | `PENDING` always at write time | Resolved by learning loop. Allowed final values: `WINNER` (setup worked at T+5), `LOSER` (setup invalidated by stop or fade), `NEVER_TRIGGERED` (entry condition never fired), `AMBIGUOUS` (mixed T+5/T+20), `NOT_APPLICABLE`. |
| `council_outcome_alignment` | `PENDING` always at write time | Resolved by learning loop. Allowed final values: `ALIGNED` (verdict matched outcome), `MISALIGNED` (verdict mismatched outcome), `NEUTRAL` (verdict-outcome combination doesn't carry a quality signal — e.g., DEFER+NEVER_TRIGGERED is neutral), `NOT_APPLICABLE`. |
| `resolution_notes` | string or blank | Free text for downstream resolution context. Blank at write time. |

**Classification rules for `actionability_council_disagreement` (computed at run time):**

- If `action_label = A1` or `A2`, and `council_verdict = DEFER` or `CANCEL` → TRUE.
- If `action_label = B` (any B+ subclass), and `council_verdict = PROMOTE` → TRUE.
- If `action_label = C` or `D`, and `council_verdict = PROMOTE` → TRUE.
- If `action_label = A1`/`A2`, and `council_verdict = PROMOTE` → FALSE (alignment).
- If `action_label = B`, and `council_verdict = DEFER` or `CANCEL` → FALSE (alignment).
- Edge cases (`UNKNOWN` action_label, `PENDING` verdict): default to FALSE, populate `rationale_diverged_on` with `"undetermined"`.

**Row inclusion rule (V1.1):** Include a row for every ticker in council_outcomes, regardless of disagreement state. This differs from the original prompt's "only include rows with disagreement" — including all rows makes the file a faithful disagreement audit and enables future learning-loop joins. If `actionability_council_disagreement = FALSE` and `user_council_disagreement = UNKNOWN`, the row still writes with those values.

**Final-response audit block (V1.1):**

After writing the file, the final response MUST include:

```
Council disagreement audit:
- council_rows: N
- actionability_council_disagreements: N
- user_council_disagreements: N (PENDING — resolved by learning loop)
- file_path: /path/to/council_disagreements_YYYY-MM-DD.csv
- pending_outcome_count: N (all rows pending at write time)
```

If `actionability_council_disagreements > 0`, list affected tickers and the divergence reason in the audit block.

**Failure handling:** If `council_disagreements_YYYY-MM-DD.csv` cannot be written, state this clearly and print the CSV content in a raw code block. Do not silently omit.


step 7.7: write self-calibration scaffold CSV (V1.1)

For every Bonde/trading council run, after writing council_disagreements_*.csv, write `council_self_calibration_summary_YYYY-MM-DD.csv` to the same location.

**Always write this file.** Insufficient-data state is the default; the file documents that state explicitly. Do not skip emission.

**Inputs:**

- All historical `council_disagreements_YYYY-MM-DD.csv` files in the same folder, OR a consolidated `council_disagreements_history.csv` if present.
- A "resolved" row is one where `outcome_status != PENDING` AND `outcome_class != PENDING` AND `council_outcome_alignment != PENDING`.

**Thresholds (V1.1, strict; mirrors bonde learning-loop lock discipline):**

- `INSUFFICIENT_DATA`: fewer than 30 resolved disagreement rows total. No reliability percentages reported.
- `BUILDING_SAMPLE`: ≥30 total resolved, but slice thresholds not met (per-verdict <10 or per-setup_family <10).
- `CALIBRATED`: ≥30 total resolved AND per-verdict ≥10 resolved AND per-setup_family ≥10 resolved.
- `UNAVAILABLE`: no historical disagreement files exist.

**Required schema (V1.1, exact column order, 13 columns, header has 12 commas):**

`run_date,calibration_status,resolved_disagreements_total,threshold_total,resolved_defer_disagreements,resolved_cancel_disagreements,resolved_promote_disagreements,resolved_by_setup_family,council_defer_accuracy,council_cancel_accuracy,council_promote_accuracy,user_override_success_rate,notes`

**Column semantics:**

| Column | Allowed values | Notes |
|---|---|---|
| `run_date` | YYYY-MM-DD | Today's date |
| `calibration_status` | `UNAVAILABLE`/`INSUFFICIENT_DATA`/`BUILDING_SAMPLE`/`CALIBRATED` | Per thresholds above |
| `resolved_disagreements_total` | integer | Count of rows where outcome_status != PENDING |
| `threshold_total` | integer | 30 (hard-coded discipline threshold) |
| `resolved_defer_disagreements` | integer | Resolved rows with council_verdict=DEFER |
| `resolved_cancel_disagreements` | integer | Resolved rows with council_verdict=CANCEL |
| `resolved_promote_disagreements` | integer | Resolved rows with council_verdict=PROMOTE |
| `resolved_by_setup_family` | string | Pipe-delimited counts: `EP_ACTIVE:12\|EP9M:7\|...` |
| `council_defer_accuracy` | float `0.0-1.0` or `INSUFFICIENT` | `ALIGNED count / resolved DEFER count`. Show only when `>=10` resolved DEFER. Otherwise `INSUFFICIENT`. |
| `council_cancel_accuracy` | float or `INSUFFICIENT` | Same logic |
| `council_promote_accuracy` | float or `INSUFFICIENT` | Same logic |
| `user_override_success_rate` | float or `INSUFFICIENT` | Rate at which user-override decisions (when `agreement_type=USER_DISAGREED_WITH_COUNCIL`) led to `outcome_class=WINNER`. `>=10` resolved overrides required. |
| `notes` | string | Free text, e.g., `"first run, no history available"` or `"calibration enabled 2026-06-15"`. |

**No premature reporting rule:**

Below threshold, the row writes with all accuracy fields = `INSUFFICIENT`. The skill's report section MUST NOT display fractional accuracy when total resolved is below 30. The report MUST say:

`Self-calibration: INSUFFICIENT_DATA. Resolved disagreements: N/30. No reliability percentage reported.`

Above threshold (CALIBRATED state) the report MAY say:

`Self-calibration: CALIBRATED. Historical accuracy on DEFER verdicts: X% (n=N). Historical accuracy on CANCEL verdicts: Y% (n=N).`

The calibration data is context only. **It MUST NOT change the council verdict.** Specifically, the chairman MUST NOT alter a DEFER to a PROMOTE because "historical DEFER accuracy is only 45%." The verdict logic is rule-based; calibration is meta-context that informs the user, not the verdict.



step 7.8: write A1/A2 reachability audit CSV (V1.3)

For every Bonde/trading council run, after writing the self-calibration scaffold, write `council_reachability_audit_YYYY-MM-DD*.csv` to the same location as the report, transcript, outcomes, disagreements, and calibration files. Then copy/write the same reachability CSV to every machine-readable handoff destination used for the other Council CSVs in that run.

Required handoff behavior:

- If `council_outcomes_*.csv`, `council_disagreements_*.csv`, or `council_self_calibration_summary_*.csv` is copied/written to `bonde_screener_cache/council_queues/`, then `council_reachability_audit_*.csv` must be copied/written there too.
- If a repo-specific Council handoff folder exists and receives the other Council CSVs, the reachability audit must be copied/written there too.
- If `bonde_screener_cache/council_queues/` does **not** exist but the repo/workspace root is writable, create it with `mkdir -p bonde_screener_cache/council_queues/` and write/copy all four machine-readable Council CSVs there in the same run. A missing handoff directory is not by itself a valid reason for manual upload.
- If the Council can write local reports to `/home/user/bonde/.claude/skills/llm-council/reports/`, first try to resolve `/home/user/bonde/bonde_screener_cache/council_queues/` as the machine-readable handoff folder; create it if missing and writable.
- The reachability audit must not remain only in `/home/user/bonde/.claude/skills/llm-council/reports/` when a repo/workspace handoff folder can be created or already exists.
- A Bonde Council run is incomplete if the existing Council CSVs are available to the learning loop but the reachability audit is not. Fix the copy/write failure before reporting the run complete, or explicitly set `manual_handoff_required: true` and print the raw CSV content.

**Always write this file.** If the run has no Bonde rows, write a header-only CSV. If the audit cannot be evaluated because fields or routing code are missing, write one `NOT_EVALUABLE` summary row explaining why.

Required schema, exact column order:

`run_date,review_date,audit_scope,ticker,signal_date,setup_family,action_label,final_trade_status,a1_reachable,a2_executable_reachable,zero_trade_cause,demotion_reason,routing_override_field,source_file,notes`

Column semantics:

| Column | Allowed values / notes |
|---|---|
| `run_date` | YYYY-MM-DD |
| `review_date` | YYYY-MM-DD |
| `audit_scope` | `SUMMARY`, `POSITIVE_CONTROL_A1`, `POSITIVE_CONTROL_A2`, `ACTUAL_A1_A2_ROW`, `NEAR_EXECUTABLE_ROW`, `NOT_EVALUABLE` |
| `ticker` | real ticker for actual rows; blank for summary/positive-control rows. Synthetic ticker symbols such as `SYNTH_*` are forbidden in all production artifacts. |
| `signal_date` | YYYY-MM-DD or blank |
| `setup_family` | source setup family for actual rows; for positive controls use `SANDBOX_CONTROL` or blank, not a live setup-family row that could be joined as a candidate. |
| `action_label` | A1/A2/B/C/D/UNKNOWN for actual rows; expected label for sandbox controls only, clearly marked by `audit_scope`. |
| `final_trade_status` | TRADE/COUNCIL/WATCH/REJECT/UNKNOWN for actual rows; sandbox routed status only when produced by an isolated harness. |
| `a1_reachable` | TRUE/FALSE/NOT_EVALUABLE |
| `a2_executable_reachable` | TRUE/FALSE/NOT_EVALUABLE |
| `zero_trade_cause` | BUG_SUSPECTED/INTENTIONAL_STRICTNESS/INSUFFICIENT_CLEAN_ROWS/DATA_MISSING/NOT_EVALUABLE/NO_ZERO_TRADE_ISSUE |
| `demotion_reason` | concise machine-readable reason; blank when not applicable |
| `routing_override_field` | final_trade_status/council_verdict/hard_reject_reason/rr_floor_fail/dte_guardrail/data_missing/unknown/none |
| `source_file` | path or basename of the decision log / council queue / skill file that produced the row |
| `notes` | concise explanation |

Summary row requirements:

- Include one `SUMMARY` row per run.
- The `notes` field in the `SUMMARY` row must include `audit_basis=ACTUAL_CORPUS`, `audit_basis=SANDBOX_POSITIVE_CONTROL`, `audit_basis=PLAYBOOK_ONLY`, or `audit_basis=NOT_EVALUABLE`.
- `audit_basis=PLAYBOOK_ONLY` may support `BUG_SUSPECTED` or `DATA_MISSING`, but must not be used to claim `A1_REACHABLE=TRUE` or `A2_EXECUTABLE_REACHABLE=TRUE`.
- The summary row must state the overall `A1_REACHABLE`, `A2_EXECUTABLE_REACHABLE`, and `ZERO_TRADE_CAUSE` values.
- Use `notes` to include compact counts, e.g. `n_A1=0; n_A2=7; n_TRADE=0; n_A2_to_COUNCIL=7; top_demotion=rr_floor_fail`.

Positive-control row requirements:

- If positive controls were evaluated, include one row each for `POSITIVE_CONTROL_A1` and `POSITIVE_CONTROL_A2`.
- If they were not evaluated, include `NOT_EVALUABLE` in the summary row and explain what was missing.
- Synthetic positive controls must never enter `council_outcomes`, `council_disagreements`, or live candidate recommendation tables.

Actual-row requirements:

- Include one `ACTUAL_A1_A2_ROW` for every actual A1/A2 row visible to the council run.
- Include `NEAR_EXECUTABLE_ROW` rows only when the source data makes a blocking reason clear enough to audit.
- Do not invent demotion reasons. If not visible, use `routing_override_field=unknown` and explain the limitation.

Final-response audit block (V1.3):

After writing the file, the final response MUST include:

```
Council reachability audit:
- A1_REACHABLE: TRUE/FALSE/NOT_EVALUABLE
- A2_EXECUTABLE_REACHABLE: TRUE/FALSE/NOT_EVALUABLE
- ZERO_TRADE_CAUSE: BUG_SUSPECTED/INTENTIONAL_STRICTNESS/INSUFFICIENT_CLEAN_ROWS/DATA_MISSING/NOT_EVALUABLE/NO_ZERO_TRADE_ISSUE
- n_A1: N
- n_A2: N
- n_TRADE: N
- n_A2_to_COUNCIL: N
- top_demotion_reasons: ...
- file_path: /path/to/council_reachability_audit_YYYY-MM-DD.csv
- handoff_path: /path/to/learning-loop-visible/council_reachability_audit_YYYY-MM-DD.csv or NOT_WRITTEN
- copied_to_machine_handoff: TRUE/FALSE
```

If the audit cannot be evaluated, say so directly. Do not claim A1/A2 is reachable unless the positive-control or actual-corpus evidence supports it.

Failure handling: If `council_reachability_audit_YYYY-MM-DD*.csv` cannot be written or cannot be copied to the same machine-readable handoff destination as the other Council CSVs, state this clearly and print the CSV content in a raw code block. Do not silently omit it.

**Machine-readable handoff rule for reachability audits (V1.3.3 / V1.3.4):**

The reachability audit is a learning-loop artifact, not merely a local report attachment. It must follow the same handoff path as `council_outcomes_*.csv`, `council_disagreements_*.csv`, and `council_self_calibration_summary_*.csv`. When `bonde_screener_cache/council_queues/` is available, the reachability audit must be written or copied there using the exact filename prefix `council_reachability_audit_`.

If `bonde_screener_cache/council_queues/` is not available because the directory is missing, the Council must attempt to create it in the current repo/workspace root before falling back to manual handoff. For the common Claude workspace path, if local reports are being written to `/home/user/bonde/.claude/skills/llm-council/reports/`, the preferred machine-readable handoff folder is:

```text
/home/user/bonde/bonde_screener_cache/council_queues/
```

Create that folder if it does not exist and the workspace is writable. Then write/copy all four machine-readable CSVs there. A missing handoff folder is not, by itself, a valid reason to require manual upload.

The final response must show:

```text
local_report_path: /home/user/bonde/.claude/skills/llm-council/reports/council_reachability_audit_YYYY-MM-DD*.csv
handoff_path: /path/to/bonde_screener_cache/council_queues/council_reachability_audit_YYYY-MM-DD*.csv
copied_to_machine_handoff: TRUE/FALSE
handoff_dir_created: TRUE/FALSE
manual_handoff_required: TRUE/FALSE
```

If the local report path exists but the handoff path does not, and the handoff directory could have been created, the Council run is not complete for learning-loop purposes.

**Manual `_inbox` handoff when Drive/workspace write access is unavailable (V1.3.2 fallback, narrowed by V1.3.4):**

Manual handoff is allowed only after the Council has tried and failed to create/write a learning-loop-visible handoff folder such as `bonde_screener_cache/council_queues/`. A missing folder alone is not enough; try `mkdir -p` first. If the Council environment truly cannot write directly to Google Drive or the Bonde workspace, still produce the artifact content. Print `council_reachability_audit_YYYY-MM-DD.csv` as a raw CSV code block and instruct Kevin to save or upload it exactly as:

```text
/content/drive/MyDrive/bonde_learning/_inbox/council_reachability_audit_YYYY-MM-DD.csv
```

Use the same fallback for the other Bonde machine-readable artifacts if they cannot be written directly. The learning loop ingests reachability handoff files from `_inbox` using the filename pattern `council_reachability_audit_*.csv`. Keep the workflow simple: Council produces the CSV; Kevin uploads it to `_inbox`; the learning loop ingests it on the next run.

output format
Every council session produces at least two files:

council-report-[timestamp].html    # visual report for scanning

council-transcript-[timestamp].md  # full transcript for reference

For Bonde/trading council runs, every session also produces:

council_outcomes_YYYY-MM-DD.csv                  # machine-readable verdicts for the learning loop
council_disagreements_YYYY-MM-DD.csv             # V1.1 — actionability/user/council disagreement audit
council_self_calibration_summary_YYYY-MM-DD.csv  # V1.1 — calibration status (default: INSUFFICIENT_DATA)
council_reachability_audit_YYYY-MM-DD.csv           # V1.3 — A1/A2 reachability and zero-TRADE cause audit

The user sees the HTML report. The transcript is there if they want to dig deeper or reference specific advisor arguments later. The council outcomes CSV is the artifact used by the Bonde learning loop; it must not be replaced by prose-only transcript parsing. The V1.1 disagreement and calibration CSVs are emitted alongside; the V1.3 reachability audit is emitted alongside as a durable diagnostic artifact for downstream accountability and learning-loop reporting.

example: counciling a product decision
User: "Council this: I'm thinking of building a $297 course on Claude Code for beginners. My audience is mostly non-technical solopreneurs. Is this the right move?"
The Contrarian: "The market is flooded with Claude courses right now. At $297, you're competing with free YouTube content. Your audience is non-technical, which means high support burden and refund risk. The people who would pay $297 are likely already past beginner level..."
The First Principles Thinker: "What are you actually trying to achieve? If it's revenue, a course is one of the slowest paths. If it's authority, a free resource might do more. If it's building a customer base for higher-ticket offers, the price point and audience might be mismatched..."
The Expansionist: "Beginner Claude for solopreneurs is a massive underserved market. Everyone's teaching advanced stuff. If you nail the beginner angle, you own the entry point to this entire space. The $297 might be low. What if this became a $997 program with community access..."
The Outsider: "I don't know what Claude Code is. If I saw '$297 course on Claude Code for beginners,' I wouldn't know if this is for me. The name means nothing to someone outside your world. Your landing page needs to sell the outcome, not the tool..."
The Executor: "A full course takes 4-8 weeks to produce properly. Before building anything, run a live workshop at $97 to 50 people. You validate demand, generate testimonials, and create the raw material for the course. If 50 people don't buy the workshop, 500 won't buy the course..."
Chairman's Verdict:
Where the council agrees: The beginner solopreneur angle has real demand, but the current framing (Claude Code course) is too tool-specific and won't resonate with non-technical buyers.
Where the council clashes: Price. The Contrarian says $297 is too high given competition. The Expansionist says it's too low for the value. The resolution likely depends on how much support and community access is bundled.
Blind spots caught: The Outsider's point that "Claude Code" means nothing to the target buyer is the single most important insight. Every advisor except the Outsider assumed the audience already knows what this is.
Recommendation: Don't build the course yet. Validate with a lower-commitment offer first. But reframe entirely: sell the outcome (automate your business, get 10 hours back per week), not the tool.
One thing to do first: Run a $97 live workshop called "How to automate your first business task with AI" to 50 people. Don't mention Claude Code in the title.

Bonde / trading council addendum

When the council is being used for Bonde/Stockbee trade candidates, B+ Day-2 council setups, or council_queue rows, apply these additional rules:

B+ blocker types:

C1 = wide Day-1 range / static EOD R:R floor fail
C2 = DTE / pre-earnings tactical setup
C3 = mild extension or Day-2 confirmation requirement

V5.9.19 actionability compatibility:

- `final_trade_status` is the executable field when present.
- `tier` is source/dashboard focus tier only.
- `tier=TAKE` is not a trade signal.
- `final_trade_status=TRADE` means the actionability skill views it as executable, still subject to council/risk review if routed.
- `final_trade_status=COUNCIL` means judgment review is required before execution.
- `final_trade_status=WATCH` means review/watch only unless a later fresh signal changes the status.
- `final_trade_status=REJECT` means no trade unless the main Bonde actionability skill has formally changed the rule.
- If `final_trade_status` is missing, state that the council is using legacy action-label fallback.

Council A1/A2 reachability compatibility (V1.3):

- If the current run or recent decision log has zero `TRADE` rows, no `A1` rows, or all visible `A2` rows routed to `COUNCIL`, run the V1.3 reachability audit before issuing chairman verdicts.
- Treat A1/A2 reachability failures as implementation/routing investigations, not as permission to lower thresholds.
- Do not promote a candidate merely to compensate for zero `TRADE` output.
- If `A1_REACHABLE=FALSE` or `A2_EXECUTABLE_REACHABLE=FALSE`, state whether the evidence points to `BUG_SUSPECTED`, `INTENTIONAL_STRICTNESS`, `INSUFFICIENT_CLEAN_ROWS`, `DATA_MISSING`, or `NOT_EVALUABLE`.
- If A2 is intentionally council-only, document that explicitly; otherwise, all-A2-to-COUNCIL routing should be treated as a reachability concern until proven intentional.

Before the reasoning paths evaluate the candidates, state whether historical outcome data exists for the same setup_family, same B+ blocker type, or prior council verdict type. Use outcome data only if it is mature enough to be meaningful. Immature cohorts are monitoring-only.

For every B+ candidate, the final verdict must include:

blocker type: C1, C2, C3, NOT_BPLUS, or UNKNOWN. Do not use mixed in the council_outcomes CSV; if multiple blockers appear and the source row is not safely classifiable, use UNKNOWN.
historical sample size if available
historical +1D / +5D expectancy if available
prior council promote/defer/cancel outcome if available
verdict: promote / defer / cancel
confidence score
whether the verdict is evidence-backed or playbook-only

Hard rule: outcome data is an overlay, not a loophole. The council cannot use outcome data to override bag-holder, failed EP, DTE unknown, DTE hard reject, dilution/offering, deal-pinned/merger-arb, or severe extension without reset unless the main Bonde actionability skill has formally changed that rule.

If outcome data is unavailable, the council must say: "Outcome data unavailable; verdict is playbook-only and should be logged for future calibration."

Execution-safety guardrails for Bonde/trading runs:

- Friday/weekend/holiday guardrail: use DAY orders or cancel-before-close by default. Do not recommend open-ended GTC orders across a weekend/holiday unless intentional and explicitly justified.
- Portfolio heat: when promoting more than one candidate, aggregate total risk and correlated exposure. If exact account-risk data is unavailable, state that and still provide qualitative heat.
- Order dependency: state which order fills cancel, reduce, or condition other orders.
- Sector-correlation hygiene: separate same-sector exposure from broad risk-appetite exposure. Do not claim unrelated sectors directly gate each other unless the linkage is explicit.
- Day-2 pullback rescue: if R:R passes only after lowering entry, label the setup as Day-2 pullback rescue and state whether base-rate evidence exists. If the pullback that creates R:R would also damage the thesis, prefer DEFER or CANCEL.


For Bonde/trading council runs, the final response must explicitly list where the six artifacts were written and state whether the report included the `Context Files Loaded` and `Portfolio Heat` sections:
- council-report-[timestamp].html
- council-transcript-[timestamp].md
- council_outcomes_YYYY-MM-DD.csv
- council_disagreements_YYYY-MM-DD.csv (V1.1)
- council_self_calibration_summary_YYYY-MM-DD.csv (V1.1)
- council_reachability_audit_YYYY-MM-DD.csv (V1.3)

For each machine-readable Council CSV, the final response must state where the file was written locally and where it was written/copied for learning-loop ingestion. For the reachability audit, the final response must include both `local_report_path` and `handoff_path`.

If any artifact was not written directly because Drive/workspace access was unavailable, the final response must state `manual_handoff_required: true` and identify the exact target upload path. For reachability audits, the fallback target path is:

```text
/content/drive/MyDrive/bonde_learning/_inbox/council_reachability_audit_YYYY-MM-DD.csv
```

All six files are mandatory for Bonde trading council runs. If any file write/copy fails, state that clearly and print the file content in a raw code block so the user can save it. Do not silently omit any of them. If the other Council CSVs are copied to a learning-loop-visible handoff folder but the reachability CSV is not, treat that as a failed acceptance test.

Final response must also include the Council disagreement audit block from Step 7.5 with `council_rows`, `actionability_council_disagreements`, `user_council_disagreements` (always PENDING at run time), `pending_outcome_count`, and the file path. Final response must also include the Council reachability audit block from Step 7.8 with A1/A2 reachability, zero-TRADE cause, key counts, top demotion reasons, the local report path, the learning-loop handoff path, and whether the handoff copy succeeded.



acceptance tests (V1.1)

The following tests apply to every Bonde/trading council run. Any failure must be fixed before reporting the run complete.

**Reframing tests (Section 1 of V1.1):**

1. The generated council report contains no "4 of 5", "5 of 5", "3 of 5", or similar vote-count phrasing except in historical quoted text (e.g., the user's prior transcript being referenced).
2. The report contains the exact section header `Reasoning Paths Considered`.
3. The report explicitly contains the disclaimer text: `These are not independent votes. Convergence is useful as a reasoning check, not as statistical corroboration.`
4. The detailed advisor/perspective reasoning is preserved (the five reasoning paths still appear in the transcript and in the report's expandable detail).
5. The chairman synthesis produces one final verdict per ticker.

**Disagreement tracker tests (Section 2 of V1.1):**

6. `council_disagreements_YYYY-MM-DD.csv` is written for every Bonde council run.
7. The CSV header has exactly 21 commas (22 columns) in the V1.1 canonical order.
8. If actionability `action_label = A2` and `council_verdict = DEFER`, the row has `actionability_council_disagreement = TRUE`.
9. If actionability `action_label = B` (B+ C1/C2/C3) and `council_verdict = DEFER` or `CANCEL`, the row has `actionability_council_disagreement = FALSE` (alignment).
10. Every row has `user_council_disagreement = UNKNOWN` at council-run time (the council cannot know Kevin's final action).
11. Every row has `outcome_status = PENDING`, `outcome_class = PENDING`, `council_outcome_alignment = PENDING` at council-run time.
12. Header-only CSV writes if zero rows (degenerate case: no Bonde tickers in this council session).
13. The CSV parses with `pandas.read_csv()`.

**Self-calibration scaffold tests (Section 3 of V1.1):**

14. `council_self_calibration_summary_YYYY-MM-DD.csv` is written for every Bonde council run.
15. With no historical disagreement files present, `calibration_status = UNAVAILABLE`.
16. With historical disagreement files but fewer than 30 resolved rows, `calibration_status = INSUFFICIENT_DATA` and all accuracy fields = `INSUFFICIENT`.
17. With ≥30 resolved rows but per-verdict <10, `calibration_status = BUILDING_SAMPLE`.
18. With ≥30 resolved rows AND per-verdict ≥10 AND per-setup_family ≥10, `calibration_status = CALIBRATED`.
19. The council verdict for any ticker is NEVER changed because of calibration data. Calibration is context only; the verdict logic is rule-based.
20. The report displays the calibration status. If `INSUFFICIENT_DATA`, the report says `"No reliability percentage reported"` and does NOT show fractional accuracy.

**Report-structure grep tests (V1.1 addition beyond original prompt):**

21. The HTML report contains the literal string `Reasoning Paths Considered` as a section header AND the literal disclaimer `These are not independent votes. Convergence is useful as a reasoning check, not as statistical corroboration.` Both must appear; missing either fails the test.

**Compatibility tests (Sections 4-5 of V1.1):**

22. Existing `council_outcomes_YYYY-MM-DD.csv` still writes with unchanged 11-column schema.
23. Existing `council-report-[timestamp].html` still writes.
24. Existing `council-transcript-[timestamp].md` still writes.
25. The chairman verdict schema (PROMOTE/DEFER/CANCEL) is unchanged.
26. No actionability skill outputs are affected by this patch.
27. The final response lists all five Bonde artifacts (report, transcript, outcomes, disagreements, calibration).

**V1.2 context/execution-safety tests:**

28. For Bonde/trading runs, the HTML report contains the exact section header `Context Files Loaded`.
29. For Bonde/trading runs, the markdown transcript contains the context files loaded audit.
30. If `daily_decision_log_*.csv` contains `final_trade_status`, the report treats `final_trade_status` as executable and does not treat `tier=TAKE` as trade authorization.
31. If `final_trade_status` is missing, the report states that it is using legacy action-label fallback.
32. If any candidate is promoted on a Friday or before a weekend/holiday gap, the report includes an order-duration guardrail: DAY order, cancel-before-close, or explicit justification for GTC.
33. If more than one candidate is promoted, the report contains a `Portfolio Heat` section with total exposure and correlation notes.
34. If promoted candidates share direct sector/theme exposure, the report states the maximum correlated exposure and any cancel/resize dependency.
35. The report does not claim direct sector correlation between unrelated industries unless the linkage is explicit. Broad tape linkage must be labeled as broad risk-appetite read-through.
36. If a Day-2 entry becomes valid mainly by lowering entry until R:R passes, the report labels it as `Day-2 pullback rescue` and states whether mature base-rate data exists.
37. Existing V1.1 schemas remain unchanged: council_outcomes has 11 columns, council_disagreements has 22 columns, and council_self_calibration_summary has 13 columns.

If any test fails, fix it before reporting the run complete.



**V1.3 Council A1/A2 reachability tests:**

38. For every Bonde/trading council run, `council_reachability_audit_YYYY-MM-DD.csv` is written alongside the other council artifacts.
39. The reachability CSV has exactly 15 columns in this order: `run_date,review_date,audit_scope,ticker,signal_date,setup_family,action_label,final_trade_status,a1_reachable,a2_executable_reachable,zero_trade_cause,demotion_reason,routing_override_field,source_file,notes`.
40. The reachability CSV parses cleanly with `pandas.read_csv()`.
41. The reachability CSV contains one `SUMMARY` row for every Bonde/trading run, even if no A1/A2 rows are present.
42. `a1_reachable` contains only `TRUE`, `FALSE`, or `NOT_EVALUABLE`.
43. `a2_executable_reachable` contains only `TRUE`, `FALSE`, or `NOT_EVALUABLE`.
44. `zero_trade_cause` contains only `BUG_SUSPECTED`, `INTENTIONAL_STRICTNESS`, `INSUFFICIENT_CLEAN_ROWS`, `DATA_MISSING`, `NOT_EVALUABLE`, or `NO_ZERO_TRADE_ISSUE`.
45. Synthetic positive-control rows, if generated, never appear in `daily_decision_log`, `council_queue`, `council_outcomes_YYYY-MM-DD.csv`, `council_disagreements_YYYY-MM-DD.csv`, `council_self_calibration_summary_YYYY-MM-DD.csv`, learning-loop candidate tables, weekly cohort reports, or any live candidate recommendation table.
45a. If no isolated routing harness is available and actual-corpus evidence does not prove reachability, the audit must not mark `A1_REACHABLE=TRUE` or `A2_EXECUTABLE_REACHABLE=TRUE`.
45b. Any positive-control row written to `council_reachability_audit_YYYY-MM-DD.csv` must have `audit_scope` beginning with `POSITIVE_CONTROL_`, blank `ticker`, and `setup_family` equal to `SANDBOX_CONTROL` or blank; it must not use a tradable ticker or production candidate key.
46. If recent rows have zero `TRADE` and the audit cannot evaluate routing due to missing fields/code, the summary row uses `A1_REACHABLE=NOT_EVALUABLE`, `A2_EXECUTABLE_REACHABLE=NOT_EVALUABLE`, and `ZERO_TRADE_CAUSE=NOT_EVALUABLE` or `DATA_MISSING`; it does not assert reachability.
47. The HTML report and markdown transcript contain the section header `A1/A2 Reachability Audit` for Bonde/trading runs.
48. The final response includes the Council reachability audit block with A1 reachability, A2 executable reachability, zero-TRADE cause, n_A1, n_A2, n_TRADE, n_A2_to_COUNCIL, top demotion reasons, and the reachability CSV path.
49. If `A1_REACHABLE=FALSE` or `A2_EXECUTABLE_REACHABLE=FALSE`, the chairman synthesis labels the issue as implementation/routing investigation unless the playbook explicitly documents the strictness.
50. Existing V1.1/V1.2 schemas remain unchanged: `council_outcomes` has 11 columns, `council_disagreements` has 22 columns, and `council_self_calibration_summary` has 13 columns.
51. If Drive/workspace write access is unavailable, the final response prints `council_reachability_audit_YYYY-MM-DD.csv` in a raw CSV code block and states the exact manual upload path `/content/drive/MyDrive/bonde_learning/_inbox/council_reachability_audit_YYYY-MM-DD.csv`.
52. If manual handoff is required, the final response includes `manual_handoff_required: true` and does not claim that the learning loop has ingested the reachability audit until Kevin uploads the CSV and reruns the learning loop.
52a. If `bonde_screener_cache/council_queues/` is missing but the repo/workspace root is writable, the Council creates the directory and writes/copies all four machine-readable Council CSVs there.
52b. A run fails acceptance if it reports manual handoff solely because `bonde_screener_cache/council_queues/` did not already exist.
53. If `council_outcomes_*.csv`, `council_disagreements_*.csv`, or `council_self_calibration_summary_*.csv` is copied/written to `bonde_screener_cache/council_queues/` or any other learning-loop-visible handoff folder, then `council_reachability_audit_*.csv` must be copied/written to the same folder in the same run.
54. The final response lists both `local_report_path` and `handoff_path` for `council_reachability_audit_*.csv`, and states `copied_to_machine_handoff: TRUE` when the handoff copy succeeds.
55. A Bonde Council run fails acceptance if the reachability audit exists only in the local reports folder while the other Council CSVs are available in the machine-readable handoff folder.
56. If the reachability handoff copy fails, the final response must set `manual_handoff_required: true`, print the raw reachability CSV content, and identify the fallback `_inbox` upload path.

important notes

Always spawn all 5 advisors in parallel. Sequential spawning wastes time and lets earlier responses bleed into later ones.
Always anonymize for peer review. If reviewers know which advisor said what, they'll defer to certain thinking styles instead of evaluating on merit.
The chairman is not bound by reasoning-path convergence. If four reasoning paths reach the same conclusion but the fifth path's argument is strongest, the chairman sides with the strongest argument and explains why. The reasoning paths are not votes; the chairman weighs argument quality, not path counts.
For Bonde/trading runs, the chairman must distinguish direct sector correlation from broad risk-appetite correlation. Do not let a broad market concern masquerade as a direct industry linkage.
For Bonde/trading runs, the chairman must distinguish A1/A2 reachability/routing defects from threshold-calibration questions. Fix unreachable logic now; do not lower thresholds or promote marginal candidates without pre-registered evidence.
For Bonde/trading runs, the reachability audit must travel with the other machine-readable Council CSVs to the learning-loop-visible handoff folder; writing it only to the local reports folder is an incomplete run. If the expected handoff directory is missing, create it before falling back to manual upload.
Don't council trivial questions. If the user asks something with one right answer, just answer it. The council is for genuine uncertainty where multiple perspectives add value.
The visual report matters. Most users will scan the report, not read the full transcript. Make the HTML output clean and scannable.
