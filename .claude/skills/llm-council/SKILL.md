---
name: llm-council
description: Run high-stakes decisions through 5 independent AI advisors, anonymized peer review, chairman verdict, optional Bonde outcome overlay, and structured trading council outcomes. Use for council this, run the council, pressure-test this, or meaningful tradeoffs. For Bonde trading councils, produce report, transcript, and council_outcomes CSV for learning-loop ingestion.
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

For Bonde/trading/B+ council questions, also look for outcome/base-rate context if available:

skill_pack_performance_report_v410.md or similar
weekly_learning_report_*.md
reviewed_vs_unreviewed_summary*.csv
bplus_council_outcome_summary*.csv
council_queue_*.csv
prior council-report-*.html or council-transcript-*.md
skill_pack_ticker_outcomes_enriched*.csv or decision/outcome summaries

Use Glob and quick Read calls to find these. Don't spend more than 30 seconds on this. You're looking for the 2-3 files that would give advisors the context they need to give specific, grounded advice instead of generic takes.

B. Build outcome/base-rate context when relevant. Outcome data is optional, but if it exists it must be summarized before the advisors vote. For trading/Bonde/B+ questions, summarize:

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

For Bonde/trading questions, include one of: promote / defer / cancel, plus confidence and whether the verdict is evidence-backed or playbook-only.

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


## Outcome/Base-Rate Context

[State whether outcome data was available. Summarize relevant base rates, sample sizes, +1D/+5D, MFE/MAE, trigger-hit or conversion data if available. If unavailable, write: "Outcome data unavailable; verdict is playbook-only and should be logged for future calibration."]


## Where the Council Agrees

[Points multiple advisors converged on independently. These are high-confidence signals.]


## Where the Council Clashes

[Genuine disagreements. Present both sides. Explain why reasonable advisors disagree.]


## Blind Spots the Council Caught

[Things that only emerged through peer review. Things individual advisors missed that others flagged.]


## The Recommendation

[A clear, direct recommendation. Not "it depends." A real answer with reasoning. For Bonde/trading candidates, state promote / defer / cancel, confidence, and whether the recommendation is evidence-backed or playbook-only.]


## The One Thing to Do First

[A single concrete next step. Not a list. One thing.]


## Council Outcome CSV Draft

[For Bonde/trading/B+ questions only, summarize the rows that will be written to council_outcomes_YYYY-MM-DD.csv using the Step 7 schema: signal_date,review_date,ticker,setup_family,action_label,bplus_blocker_type,council_verdict,confidence,decision_reason,report_path,transcript_path. Use council_verdict only as PROMOTE, DEFER, or CANCEL. If not a trading/B+ question, write N/A.]


Be direct. Don't hedge. The whole point of the council is to give the user clarity they couldn't get from a single perspective.
step 5: generate the council report
After the chairman synthesis is complete, generate a visual HTML report and save it to the user's workspace.
File: council-report-[timestamp].html
The report should be a single self-contained HTML file with inline CSS. Clean design, easy to scan. It should contain:

The question at the top
The outcome/base-rate context prominently displayed when relevant
The chairman's verdict prominently displayed (this is what most people will read)
An agreement/disagreement visual — a simple visual showing which advisors aligned and which diverged. This could be a grid, a spectrum, or a simple breakdown showing advisor positions. Keep it clean and scannable.
Collapsible sections for each advisor's full response (collapsed by default so the page isn't overwhelming, but available if the user wants to dig in)
Collapsible section for the peer review highlights
A footer showing the timestamp and what was counciled

Use clean styling: white background, subtle borders, readable sans-serif font (system font stack), soft accent colors to distinguish advisor sections. Nothing flashy. It should look like a professional briefing document.
Open the HTML file after generating it so the user can see it immediately.
step 6: save the full transcript
Save the complete council transcript as council-transcript-[timestamp].md in the same location. This includes:

The original question
The framed question
The outcome/base-rate context used or the statement that no outcome data was available
All 5 advisor responses
All 5 peer reviews (with anonymization mapping revealed)
The chairman's full synthesis

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

Internal verdict language must be normalized to one of the three allowed values before writing the CSV. Use this exact mapping:

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

output format
Every council session produces at least two files:

council-report-[timestamp].html    # visual report for scanning

council-transcript-[timestamp].md  # full transcript for reference

For Bonde/trading council runs, every session also produces:

council_outcomes_YYYY-MM-DD.csv    # machine-readable verdicts for the learning loop

The user sees the HTML report. The transcript is there if they want to dig deeper or reference specific advisor arguments later. The council outcomes CSV is the artifact used by the Bonde learning loop; it must not be replaced by prose-only transcript parsing.

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

Before advisors vote, state whether historical outcome data exists for the same setup_family, same B+ blocker type, or prior council verdict type. Use outcome data only if it is mature enough to be meaningful. Immature cohorts are monitoring-only.

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


For Bonde/trading council runs, the final response must explicitly list where the three artifacts were written:
- council-report-[timestamp].html
- council-transcript-[timestamp].md
- council_outcomes_YYYY-MM-DD.csv

The `council_outcomes_YYYY-MM-DD.csv` file is mandatory for Bonde trading council runs. If file writing fails, state that clearly and print the CSV content in a raw code block so the user can save it manually. Do not silently omit it.

important notes

Always spawn all 5 advisors in parallel. Sequential spawning wastes time and lets earlier responses bleed into later ones.
Always anonymize for peer review. If reviewers know which advisor said what, they'll defer to certain thinking styles instead of evaluating on merit.
The chairman can disagree with the majority. If 4 out of 5 advisors say "do it" but the reasoning of the 1 dissenter is strongest, the chairman should side with the dissenter and explain why.
Don't council trivial questions. If the user asks something with one right answer, just answer it. The council is for genuine uncertainty where multiple perspectives add value.
The visual report matters. Most users will scan the report, not read the full transcript. Make the HTML output clean and scannable.
