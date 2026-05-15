# Council Transcript — 2026-05-15 Batch (re-run, overwrites morning run)

**Council version:** V1.2 (2026-05-15)
**Review date:** 2026-05-15 (Friday — weekend gap to 2026-05-18 execution)
**Signal date:** 2026-05-14
**Tickers reviewed:** WCC, JBHT, NVMI, WERN
**Market mode:** Risk-On

---

## Original Question

User asked: "council this" on a 4-ticker packet (WCC A2 DEP, JBHT/NVMI/WERN B+ C1 slingshots) with full per-ticker council_questions, planned R:R math, catalyst grades, and Day-2 plans.

## Framed Question

Should the user PROMOTE / DEFER / CANCEL four Bonde Day-2 candidates for Monday 2026-05-18 execution, given that WCC is an A2 DELAYED_EP RECLAIM with R:R 2.40 PASS but only 0.10% cushion above pause_high reclaim, and JBHT/NVMI/WERN are B+ C1 slingshots whose R:R passes only by lowering entry to pause_high pullback (Day-2 pullback rescue cohort, no mature base rate)? Today is Friday with a 65-hour weekend gap before execution. V5.9.19 semantics apply (`tier=TAKE` is not authorization).

## Context Files Loaded

| file_role | path | status | notes |
|---|---|---|---|
| council_queue | (user packet inlined in prompt) | LOADED | full per-ticker fields including council_question, R:R math, planned_size, day1 metrics |
| daily_decision_log | bonde_files 3/daily_decision_log_2026-05-13.csv | LOADED | most-recent log available; no 2026-05-14 log present |
| skill_pack | bonde_files 3/skill_pack_performance_report_v410.md | LOADED | v410 cohort context |
| setup_family_perf | bonde_files 3/setup_family_performance_summary_v410.csv | LOADED | ACTIVE_BURST: PARTIAL_OUTCOME / IMMATURE_20D; trigger-hit 5d 72.7%; no separate SLINGSHOT or DELAYED_EP row |
| reviewed_vs_unreviewed | bonde_files 3/reviewed_vs_unreviewed_summary_v410.csv | LOADED | reviewed cohort trigger-hit 59.1%, unreviewed 99.3%; both IMMATURE_20D |
| weekly_learning | bonde_files 3/weekly_learning_report_2026-W20.md | LOADED | week-of context |
| candidate_context | latest_candidate_context.md | MISSING_OPTIONAL | no repo context manifest present |
| learning_context | latest_learning_context.md | MISSING_OPTIONAL | |
| manifest | council_context_manifest.md | MISSING_OPTIONAL | |
| actionability_skill | bonde_stockbee_actionability/SKILL.md | MISSING_REQUIRED | folder present but SKILL.md not located; council operating from candidate packet and embedded V5.9.19 playbook rules |
| prior_council | council-report-20260514-batch.* | LOADED | prior day verdicts (PRM/ARMK promoted; MRVL/AVT cancelled) |
| prior_council_same_packet | council-report-20260515-batch.* (11:42 ET) | LOADED-OVERWRITTEN | this re-run replaces the morning batch per user instruction |

**`final_trade_status` field availability:** NOT PRESENT in the user packet. Council is using legacy action-label fallback per V5.9.19 §B compatibility.

## Outcome / Base-Rate Context

- ACTIVE_BURST: n=92, n_evaluable_5d=71, status PARTIAL_OUTCOME / IMMATURE_20D, trigger-hit 5d 72.7%, win_rate_1d_trig 50.0%, avg_ret_1d_trig -0.62%, avg_ret_3d_trig -0.42%.
- SLINGSHOT: separate row not present in v410 family summary.
- DELAYED_EP: separate row not present in v410 family summary.
- Reviewed (council-touched) cohort: trigger-hit 59.1% vs unreviewed 99.3%; pct_triggered 93.5%; no mature 10D/20D.
- Day-2 pullback rescue cohort (B+ C1 promoted via lowered entry): NO mature base rate.
- Prior council promote outcomes on similar B+ C1 rescue patterns: PENDING resolution.

**Verdicts are playbook-only and should be logged for future calibration.**

---

## Anonymization Mapping

- Response A → First Principles Thinker
- Response B → Outsider
- Response C → Executor
- Response D → Contrarian
- Response E → Expansionist

---

## Advisor Responses (de-anonymized)

### The First Principles Thinker

**Strip the framing first.** The question pretends to be "limit-pullback vs buy-stop" on four tickers. It is not. The actual decision is: **am I willing to manufacture R:R compliance by sliding the entry leftward until the spreadsheet stops complaining?** The playbook is obscuring it by labeling the maneuver "Day-2 pullback rescue" — a cohort with *no mature base rate*. When a rule fails (R:R FAIL above trigger), there are only two honest responses: take a smaller size, or pass. Moving the entry until math agrees is a third option that pretends to be the first two. It is a rules-violation wearing a costume.

Three of the four (JBHT, NVMI, WERN) are extended Day-1 burst-and-close-strong setups where the *pullback that rescues R:R is the same pullback that invalidates the thesis* — these names work by continuation, not by retrace-and-resume. You are paying for an entry that, if filled, likely means the trade is already failing.

Weekend gap on a Risk-On Friday with four correlated-ish longs is a single macro bet, not four trades.

**Per-ticker (playbook-only; IMMATURE_20D; V5.9.19):**

1. **WCC — PROMOTE, 0.65.** The $371.67 reclaim limit. The *only* candidate where the pullback IS the actual setup (DELAYED_EP/RECLAIM), not a rescue. R:R 2.40 real not manufactured.
2. **JBHT — DEFER, 0.70.** Pullback to $247.79 is a 5%+ retrace that breaks the slingshot.
3. **NVMI — CANCEL, 0.75.** +10.4% earnings gap, new 52w high, +47.9% above 200SMA, vol *barely* clearing 1.2x. Asking for a -4.7% pullback on Day-2 post-earnings = asking market to undo the catalyst.
4. **WERN — DEFER, 0.60.** Strongest trucking but second trucking name = JBHT duplicate at portfolio level.

**Real decision:** take only the candidate whose pullback is the setup itself (WCC) and pass the three where the pullback is the costume. One trade Monday, not four.

### The Outsider

No historical edge data; reads numbers and geometry only.

**WCC — Defer (medium-high).** Limit at $371.67 is essentially today's close ($372.05). That's not a "limit order" — that's "buy at market on Monday and hope it doesn't gap." Stop at $359.87 fine, but 2.40 R:R is manufactured by picking $400 as target. +42.5% above 200SMA is extended. Want to see it actually pull in and hold $360.

**JBHT — Cancel (high).** Above-trigger R:R 0.83 non-starter. "Pullback to $247.79" = 3.6% drop = meaningful breakdown, not a tag. Same trade as WERN. Pick one truck or none.

**NVMI — Defer (high).** Earnings today. 1.26x volume on beat-and-raise into 52w high is underwhelming — if institutions were loading, 2x+ expected. "Pullback to $530" = 4.7% drawdown = "stock fades earnings pop and I catch the knife." +47.9% above 200SMA most extended.

**WERN — Promote (low-medium), IF taking exactly one trucker.** Limit at $36.86 is genuinely close to close (-0.78%) — an actual limit order. 3.5x volume is only conviction-level tape in batch. +23.8% above 200SMA least extended. R:R 1.09 weak but structure is real.

**Weirdest thing:** three of four "limit entry" plans are either at today's close (WCC) or require 3.6-4.7% decline to fill — not limits, conditional breakdown bets. Friday→Monday gap on +35-48% above 200SMA names in Risk-On tape = exactly when overnight reversals happen.

### The Executor

**WCC — PROMOTE. HIGH.** Monday: BUY LIMIT $371.67, DAY, full size. Stop $359.87 GTC after fill (stop-LIMIT $359.00 floor). Target $400 GTC after fill, scale 1/2 at +1R $383.46. Only one with real R:R 2.40 that doesn't require lowering entry. Fill probability HIGHEST. If WCC gaps up >0.5%, do NOT chase, cancel EOD.

**WERN — PROMOTE (small). MEDIUM.** BUY LIMIT $36.86, DAY, HALF size. Fill probability MEDIUM-HIGH (-0.78% away). Half because Day-2 rescue + correlation.

**JBHT — CANCEL (conditional on WERN). HIGH.** Do not enter Monday. WERN is the cleaner trucking expression. JBHT fill probability LOW (-3.7% away). If you insist: BUY LIMIT $247.79 DAY quarter-size contingent-cancel-on-WERN-fill — recommend skip.

**NVMI — DEFER. MEDIUM-HIGH.** No Monday order. Re-evaluate Tuesday if it actually pulls back to $530 on declining volume.

**Sequencing Monday open:** 9:30-9:35 nothing, let auction settle. 9:35 WCC limit $371.67 DAY. 9:36 WERN limit $36.86 DAY half. Skip JBHT, NVMI. ALL DAY orders, never GTC over weekend gaps. Stops GTC only AFTER fill, stop-LIMIT not stop-market. Combined risk cap: WCC 1R + WERN 0.5R = 1.5R. If WCC fills but WERN unfilled by 11:00, cancel WERN.

### The Contrarian

**WCC — DEFER, medium-high.** A 0.10% cushion above a reclaim is a coin flip dressed as a setup; one bad opening tick Monday and you're long underneath the line you claimed authorized entry. Limit-only acceptable; buy-stop above $374 fails R:R floor. If gaps >1% above pause_high, stand down not chase.

**JBHT — CANCEL, high.** Worst risk-adjusted ticket. +35.6% extended, large-cap float caps upside, only passes by lowering entry = R:R rescue not setup quality. Pullback to $247.79 is a 3% retrace tape rarely grants without deeper flush.

**NVMI — DEFER, medium.** Earnings-reaction +10.4% on 1.26x volume is yellow flag — move went up on thinner participation than the gap deserves; profile that gives back 50% of Day-1 in 48 hours. $530 pullback = betting on weakness to enter "strong" setup. Pick a lane. Semi-cap single-name Monday post-earnings = gap-risk unhedgeable.

**WERN — DEFER, medium.** Best technical profile of cluster but cannot own WERN+JBHT — one trucking trade with two tickets and double correlated drawdown on sector reversal. $36.86 entry only 0.78% below close = rounding error pretending to fix R:R.

**Collective failure mode:** Three of four only pass R:R by manufacturing pullback entry tape hasn't offered = reverse-engineering "PASS" from desired outcome = how Day-2 rescue cohorts blow up when they get mature base rates. Plus trucking double-correlation, 65-hour weekend gap with no intraday risk management, all four 23-48% above 200SMA in Risk-On tape that mean-reverts hardest from those extensions. Honest read: take WCC only if reclaim holds clean Monday, cancel JBHT, treat NVMI/WERN as Tuesday decisions.

### The Expansionist

Risk-On tape, four Day-1 leaders, A-grade catalysts on three, trucking cluster lighting up. Conservative readings leave R on the table.

**WCC — PROMOTE pullback limit $371.67. HIGH.** Reclaim-day DEP on electrical-distribution +42.5% over 200SMA with clean 4/30 A-beat = textbook institutional re-entry. R:R 2.40 cleanest math. Buy-stop $374 is the trap. Upside: capex/utility/data-center tape bids WCC through $400 toward $420+.

**JBHT — PROMOTE pullback to $247.79. MEDIUM-HIGH.** Large-cap float caps nothing when a sector re-rates — JBHT new 52w high with 2.42x volume *inside a four-name trucking cluster* is thematic regime change. Funds=1789 = structural bid. Upside: 12-15% on multiple expansion.

**NVMI — PROMOTE pullback to $530. HIGH.** Multi-R asymmetric play. A-grade earnings *with raised guide and $1B target reaffirmed*, 90 DTE runway, semi-cap tape, only 1.26x volume = move *under-owned* not blown off. New 52w high + raised guide = overshoot setup. Upside: $600+ within DTE window.

**WERN — PROMOTE pullback to $36.86. MEDIUM-HIGH.** Highest volume in trucking (3.52x), tightest extension (+23.8%), 140% EPS surprise. Day-11 DEP-like. Trucking concentration with JBHT is a *feature* — correlated exposure to a re-rating.

**Biggest opportunity missed:** NVMI. 1.26x reads as "barely qualifying" to a cautious eye — to me it reads as institutions haven't piled in yet on a raised-guide A-beat with $1B reaffirmed and 90 DTE.

---

## Peer Reviews

### Reviewer 1
**Strongest: D (Contrarian).** Names the unifying defect — three of four tickets only pass R:R by manufacturing a pullback the tape hasn't offered — then layers correlation, 65-hour weekend gap, Risk-On-mean-reverts-from-extension. A converges on the same verdict but D's failure-mode framing is more transferable. C is operationally crisp but skips "is this an edge."
**Biggest blind spot: E (Expansionist).** Treats 1.26x volume on a beat-and-raise gap to 52-week high as bullish under-ownership — confirmation-bias on the single most diagnostic bearish tell. Dismisses correlation ("FEATURE if theme works") = standard double-down rationalization. Ignores IMMATURE_20D entirely.
**Base-rate misuse: E overfits** to imagined upside without any base rate to anchor; "if one prints 4R+ it's NVMI" is pure narrative. C also ignores IMMATURE — sizes confidently as if cohort edge were established. A, B, D correctly treat absence as restraint.
**All five missed:** Sunday-night futures / Asia semis tape as a pre-decision gate — NVMI and the truckers will be repriced before any Monday limit can fill. Also: no one specified what invalidates the WCC reclaim intraday Monday.

### Reviewer 2
**Strongest: A (First Principles).** Reframes the actual decision (Day-2 pullback rescue: edge or rationalization?) instead of fiddling with limit prices on a flawed premise. Correctly identifies correlated-longs problem. WCC-only conclusion internally consistent.
**Biggest blind spot: E.** Calling trucking concentration "a feature" inverts portfolio math — correlation increases variance, not expectancy. Treats NVMI's 1.26x as bullish on a catalyst day when it reads as distribution/lukewarm reception.
**IMMATURE_20D handling:** E ignores entirely. C underweights (precise tickets imply precision base rate doesn't support). A, B, D appropriately shrink.
**All missed:** quantitative weekend-gap risk, Monday macro calendar, portfolio-level kill switch if WCC fills and gaps against.

### Reviewer 3
**Strongest: A.** Identifies the load-bearing question nobody else fully names. Differentiated calls (PROMOTE WCC because pullback IS the DEP reclaim; CANCEL NVMI because pullback contradicts catalyst thesis) show setup-by-setup reasoning.
**Biggest blind spot: E.** Promotes all four with no acknowledgment that three require a pullback that mechanically violates R:R or slingshot thesis. Reading momentum, not structure.
**Base-rate misuse: E overfits** bullish regime read. C underweights by sizing full/half as if playbook were proven.
**All missed:** post-weekend two-day news/gap window; OPEX-week positioning carryover; option of paper-tracking all four to mature the base rate.

### Reviewer 4
**Strongest: D.** Only response explicitly naming the structural problem: three of four require a 3.6-4.7% adverse move to qualify = reverse-engineering PASS. D's framing of NVMI/WERN as Tuesday decisions respects weekend gap + IMMATURE.
**Biggest blind spot: E.** Treats trucking concentration as "feature" without acknowledging IMMATURE_20D = no validated base rate for B+ C1 slingshot, let alone for stacking two truckers across a weekend gap. Conflates regime narrative with edge.
**Base-rate misuse:** E overfits bullish. C overfits opposite — false precision on IMMATURE sample where execution theater substitutes for statistical confidence. B partially misuses by converting "no base rate" into specific limit prices.
**All missed:** Monday 2026-05-18 macro events; OpEx unwind dynamics from prior Friday; pre-market gap behavior that invalidates Friday-close-based limits. Sample-building option value none of the five priced.

### Reviewer 5
**Strongest: C (Executor).** Only response that converts judgment into executable Monday plan — explicit limits, time-in-force, OCO logic, 11:00 abandonment rule, stop-limit, 1.5R cap. Resolves trucking correlation via OCO rather than ignoring (E) or just disqualifying (D).
**Biggest blind spot: E.** Trucking concentration "feature"; ignores three-of-four pullback-invalidates-thesis; reads 1.26x as bullish without addressing that entry sits ~3.6% below current price (bidding weakness, not buying strength).
**IMMATURE handling:** E overfits to optimism. D and B handle it best (downshift to DEFER/CANCEL defaults). A acknowledges implicitly. C uses appropriately as sizing constraint.
**All missed:** Monday 2026-05-18 scheduled catalyst check (NVMI post-earnings drift window); sector ETF (XLI/PAVE) open confirmation for WCC; trucking ETF confirmation for the trucks.

---

## Reasoning Path Convergence

**Note:** These are not independent votes. Convergence is useful as a reasoning check, not as statistical corroboration. Five perspectives reaching the same conclusion is one model exploring the same conclusion five times.

- **WCC pullback-limit is the only honest entry geometry in the batch:** First Principles, Executor, and Expansionist each arrived here by different routes — First Principles via "the pullback IS the setup, not a rescue," Executor via "highest fill probability at-the-money," Expansionist via "textbook institutional re-entry."
- **JBHT is the weakest ticket:** Contrarian, Outsider, Executor, and First Principles each rejected it — Contrarian via large-cap upside cap, Outsider via "same trade as WERN," Executor via OCO logic, First Principles via "pullback breaks slingshot." Only the Expansionist path argued for it, leaning on a thematic regime claim.
- **NVMI's 1.26x volume on an A-grade earnings gap is the most diagnostic data point:** Contrarian called it a "yellow flag," Outsider called it "underwhelming," First Principles called it "barely clearing," Executor refused to bid weakness. Only the Expansionist framed it as bullish under-ownership.
- **Day-2 pullback rescue is structurally different from Day-2 pullback setup:** First Principles and Contrarian arrived at this distinction independently; Outsider arrived at the same place by raw geometry (a "limit" at -4.7% is a breakdown bet). WCC's pullback IS the setup; JBHT/NVMI/WERN's pullbacks are rescue maneuvers.

## Reasoning Path Divergence

- **WCC PROMOTE vs DEFER:** First Principles, Executor, Expansionist PROMOTE on the structural argument that the pullback IS the setup. Contrarian and Outsider DEFER on the 0.10% cushion — a single bad opening tick leaves the buyer underneath the authorization line. Chairman weights the structural argument higher but adopts the execution caveat (limit-only, DAY order, do-not-chase).
- **WERN PROMOTE vs DEFER:** Executor, Outsider (conditional), Expansionist PROMOTE on lead-horse trucking metrics. Contrarian and First Principles DEFER on "JBHT duplicate at portfolio level." Chairman resolves by cancelling JBHT first; WERN as the sole trucking expression is a different ticket than WERN-plus-JBHT.
- **NVMI DEFER vs CANCEL vs PROMOTE:** First Principles CANCEL (catalyst-contradicting pullback); Contrarian/Outsider/Executor DEFER (volume tell, gap-risk, fantasy fill); Expansionist PROMOTE. DEFER carries the synthesis — CANCEL is too aggressive given a 90 DTE A-grade catalyst, but PROMOTE on Day-2 rescue with the worst volume signature is not justified.

## Blind Spots the Reasoning Paths Caught

- **Outsider's "weirdest thing" framing** flagged that three of four "limit entry" plans are conditional breakdown bets dressed up as limits — the same structural defect First Principles named as Day-2 pullback rescue, arrived at from raw geometry without needing playbook vocabulary.
- **Contrarian** caught that even WCC's "real R:R" is conditional on the reclaim holding intraday Monday; a 0.10% cushion is a coin flip dressed as one. This refines WCC PROMOTE to a Monday-DAY-limit-with-stand-down rule, not an open commitment.
- **Executor** alone provided OCO logic that resolves the trucking-correlation problem cleanly — cancel the weaker name (JBHT), let the stronger one (WERN) carry the exposure at half size.
- **Peer review caught two collective misses:** (1) Sunday-night futures / Asia semis tape will reprice NVMI and possibly trucking before any Monday limit can fill — every "pullback to $X" plan is conditional on a gap that hasn't happened; (2) Sample-building option value — with IMMATURE_20D, paper-tracking these four to mature the dataset has measurable option value none of the five advisors priced.

---

## Chairman Synthesis

**Council self-calibration status:** INSUFFICIENT_DATA. Resolved disagreements: 0/30. No reliability percentage reported. Self-calibration is context only and does NOT change the verdict.

**V5.9.19 compatibility note:** `final_trade_status` is NOT present in the user packet. Council is using legacy action-label fallback. `tier=TAKE` for JBHT/NVMI/WERN is NOT trade authorization; B+ C1 council-routed status governs.

The Chairman weighted the First Principles "pullback rescue vs pullback setup" distinction against the Expansionist's "trucking-regime under-owned-NVMI" thesis and concluded the structural argument wins on every ticket. Executor's geometry carries the execution detail. Contrarian's caveats refine WCC to a constrained DAY-only limit. The Expansionist path is preserved in the report but did not carry the verdict because it relies on regime narrative and imagined institutional flow rather than the candidates' own structure — three of its four PROMOTE arguments require entries the tape has not offered.

### Per-ticker verdicts

- **WCC — PROMOTE, medium-high confidence.** Playbook-only. Limit-only at pause_high $371.67, stop $359.87, target $400, R:R 2.40 PASS, full size. Day-2 DEP RECLAIM pullback IS the setup, not a rescue. Do NOT chase a buy-stop above $374 (R:R 1.84 fails floor). Monday DAY order only.

- **JBHT — CANCEL, high confidence.** Playbook-only. Worst risk-adjusted ticket: pullback to $247.79 is a 3.6% breakdown that mechanically invalidates the slingshot continuation thesis; large-cap float historically caps post-earnings continuation under 10%; redundant with WERN. Day-2 pullback rescue is not enough to justify allocation against a cleaner trucking expression (WERN).

- **NVMI — DEFER, medium-high confidence.** Playbook-only. The 1.26x volume on an A-grade beat-and-raise into a new 52w high is the most diagnostic bearish tell in the batch — institutions did not pile in on the print. The $530 pullback (-4.7% from $556.11 close) is a breakdown bet, not a limit entry, and the pullback that satisfies R:R would also damage the just-raised-guide thesis. 90 DTE catalyst intact; re-evaluate Tuesday/Wednesday if NVMI organically resets to $530-540 on declining volume (fresh Day-2 signal required, not Day-2 rescue).

- **WERN — PROMOTE, medium confidence (half size).** Playbook-only. The cleanest trucking expression and the only Day-2 pullback in the batch where the entry is genuinely close to current price (-0.78% from close). 3.52x volume strongest in cluster; +23.8% above 200SMA tightest extension; A-grade Apr 28 earnings (Day-11 DEP-like). With JBHT cancelled, the correlation objection collapses: WERN becomes the sole trucking ticket at half size. R:R only passes by lowering entry — hence the "playbook-only / half size" qualifier; this IS Day-2 pullback rescue, not validated edge. Cancel if the trucking ETF gaps against on the Monday open.

## Portfolio Heat

Two promoted tickets: WCC (full size) + WERN (half size).

| ticker | risk_per_share | size | account-R contribution |
|---|---|---|---|
| WCC | stop $359.87 from entry $371.67 = $11.80 (3.2%) | full | 1.0R |
| WERN | stop $34.10 from entry $36.86 = $2.76 (7.5%) | half | 0.5R |

**Total proposed R if both fill: 1.5R.** Exact account-risk dollar sizing was not available in the packet; figures expressed in units of R.

**Sector / theme overlap:**
- **Direct sector correlation:** LOW. WCC = industrial electrical distribution (capex/utility/data-center beneficiary); WERN = trucking. Different industries.
- **Broad risk-appetite correlation:** MODERATE. Both are cyclical industrials and would drawdown together in a Risk-Off rotation.

**Max correlated exposure:** 1.5R if both fill and a broad cyclical reversal hits both simultaneously. Acceptable.

**Order dependencies:**
- WCC fill is independent of WERN fill (no OCO).
- JBHT is CANCELLED — no JBHT ticket Monday.
- WERN cancels if the trucking ETF opens >1.5% down Monday — the cluster thesis is what makes WERN's R:R rescue defensible; lose the cluster, lose the trade.

**What invalidates the basket:**
- Monday gap-up >0.5% on WCC: limit won't fill, do NOT chase the buy-stop above $374.
- Monday gap-down through WCC stop: accept stop-limit slip at $359.00 floor.
- Trucking-cluster reversal (KNX/SAIA/JBHT gap-down >2%): cancel WERN limit pre-fill.
- Monday macro shock (FOMC speakers, China data): stand down entirely; reassess Tuesday.

**Weekend / Friday-to-Monday guardrail:**
- ALL Monday entry orders are DAY orders, NOT GTC. Re-evaluate Tuesday morning for anything unfilled — do not let Friday-close-based limits sit live across an Asian/European session that has repriced semis and trucking.
- Stops go GTC only after fill confirmation, as stop-LIMIT (not stop-market) to protect against gap-down liquidity vacuums.
- If WCC fills but WERN unfilled by 11:00 ET Monday, CANCEL the WERN limit.

## The One Thing to Do First

Monday 2026-05-18, 9:35 ET (after the opening auction settles): place WCC BUY LIMIT $371.67, DAY order, full size. That single ticket has the best fill probability and the only validated R:R geometry in the batch. Everything else is contingent.

## Council Outcome CSV Draft

See `council_outcomes_2026-05-15.csv` for the machine-readable verdicts.
