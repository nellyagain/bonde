# Council Transcript — KURA / ROIV B+ C1 SLINGSHOT Day-2 Review

**Run date:** 2026-05-21 · **Review date:** 2026-05-21 · **Signal date:** 2026-05-20
**Council skill:** V1.3.4 · **Verdict:** 0 promote / 1 defer (ROIV) / 1 cancel (KURA) · all verdicts **playbook-only** (SLINGSHOT base rates immature)

---

## Original question

`council this:` — user-supplied TSV of two B+ Day-2 council rows (KURA, ROIV), each a SLINGSHOT C1 candidate that passes its gates but fails the static Day-1 2.0 R:R floor, with proposed Path A / Path B Day-2 rescue geometry.

## Context Files Loaded

| file_role | path | status | notes |
|---|---|---|---|
| candidate set | user-supplied TSV in council prompt | LOADED | KURA + ROIV, signal_date 2026-05-20, review 2026-05-21 — NOT in the loaded packet |
| council manifest | `bonde_files 3/active_context/council_context_manifest.md` | LOADED | packet date 2026-05-19 |
| council_queue | `bonde_files 3/current/council_queue_2026-05-19.csv` | LOADED (stale) | 2026-05-19 packet; KURA/ROIV not present |
| daily_decision_log | `bonde_files 3/current/daily_decision_log_2026-05-18.csv` | LOADED (stale) | no `final_trade_status` for KURA/ROIV → legacy action-label fallback |
| skill_pack | `bonde_files 3/current/bonde_skill_pack_2026-05-15.csv` | LOADED (stale) | source signal reference |
| market context | `bonde_files 3/active_context/latest_market_context.md` | LOADED | Nasdaq Bull regime; EMA21 +3.70% Extended; SMA50 +11.29% Extremely Extended |
| SLINGSHOT base rates | `bonde_files 3/learning/slingshot_bucket_performance_v41314.csv`, `slingshot_diagnostics_report_v41314.md` | LOADED (immature) | 337 SLINGSHOT signal rows, **0 resolved outcomes** |
| setup-family base rates | `bonde_files 3/learning/learning_loop_executive_digest_2026-05-20.md` | LOADED | SLINGSHOT n=137, win_rate nan, PARTIAL_OUTCOME |
| self-calibration history | `reports/council_self_calibration_summary_2026-05-20.csv` | LOADED | INSUFFICIENT_DATA (0/30 resolved) |
| prior council | `reports/council-transcript-20260520-batch.md`, `council_outcomes_2026-05-20.csv` | LOADED | 14-row B+ batch → 0 promote / 10 defer / 4 cancel |
| actionability skill | `bonde_stockbee_actionability/SKILL.md` | MISSING_OPTIONAL | not in packet; council operates from candidate packet + embedded V5.9.x playbook rules |

**Limitation:** the loaded daily packet is dated 2026-05-19, one-to-two sessions stale relative to the 2026-05-20 KURA/ROIV signals. It is used as a base-rate / prior-council overlay only. No `final_trade_status` field accompanies the two candidates → V5.9.19 legacy action-label fallback (`action_label=B`, B+ subclass, watch-only, routed to council). `tier` values (KURA TAKE, ROIV WATCH) are dashboard focus only and are **not** trade authorization.

## Framed question

Bonde/Stockbee trading council — Day-2 review, review date Thu 2026-05-21. Two B+ C1 SLINGSHOT candidates routed to council; decide promote / defer / cancel per ticker.

- **KURA** (Kura Oncology, biotech) — SLINGSHOT B+ C1, tier=TAKE, focus_rank 7. Catalyst POST_EARNINGS_CONTINUATION + EHA data, grade **B**, conf 70. Day-1 (05-20) +15.4% on 3.89x volume, closed 97.1% up range — but the +15.4% is a **delayed Day-6 post-earnings continuation**, not a first-day catalyst response. Trigger $10.38, invalidation $8.98, close $10.34, target $12.14 (recent 52w high) → Day-1 R:R **1.26 FAIL**; pack MM target $11.22 → 0.60R. Close +13.4% above 200SMA. DTE ~70 verified. Path A: keep $10.38 trigger, tighten stop to Day-1 midpoint $9.68 (~6.7% stop) → 2.51R. Path B: pullback to $9.80-10.00, stop ~$9.50 → 4.28R.
- **ROIV** (Roivant Sciences, biotech) — SLINGSHOT B+ C1, tier=WATCH, focus_rank 18. Catalyst EARNINGS+SETTLEMENT+REGULATORY+CLINICAL, grade **A**, conf 92, fresh signal-date catalyst. Day-1 (05-20) +14.9% on 3.10x volume, closed 88.9% up range, **new all-time high**. Trigger $32.79, invalidation $29.35, close $32.41, target $35.00 → Day-1 R:R **0.64 FAIL**; pack slingshot_target $39.68 was an EVAL_2R_FALLBACK (forbidden). Close **+48.9% above 200SMA** (extended). DTE >60 verified. Path A: confirmation entry >$33, stop $31.07, target $40 → 3.63R (but against the defensible $35 target Path A is ~1.0R). Path B: pullback to $30.00-30.50, target $35 → 3.91R.
- Calendar: review Thu 5/21; next sessions Fri 5/22 then Memorial Day long weekend (Mon 5/25 closed).
- Hard-rule check: no bag-holder, no failed EP, DTE verified both, no dilution/offering, no deal-pin (ROIV's Moderna settlement is cash received, not a merger-arb pin). No hard rejects — both legitimately council-routable.

## Outcome / base-rate context used

Outcome data **available but immature** — monitoring only; **all verdicts playbook-only**.

- **SLINGSHOT family** is the least-mature, weakest-evidenced setup family: 337 signal rows, **0 resolved 5-day outcomes**, `win_rate_5d` = nan, confidence = PARTIAL_OUTCOME. Earliest T+5 maturity 2026-05-22. The 2026-05-20 council transcript noted SLINGSHOT ~17.5% 3-day triggered win / avg 3d −3.7% — a noisy in-flight snapshot on zero resolved rows, **not** a settled base rate.
- **Self-calibration:** INSUFFICIENT_DATA (0/30 resolved disagreements). No reliability percentage reported.
- **Market:** Nasdaq Bull regime but extended (EMA21 +3.70% Extended; SMA50 +11.29% Extremely Extended). Risk-On tape, consistent with both candidates' `market_mode=Risk-On`.
- **Prior council precedent:** the 2026-05-20 council reviewed 14 B+ rows → 0 promote / 10 defer / 4 cancel, explicitly flagging back-solved targets and Day-2 pullback rescues as recurring defects.

## A1/A2 reachability audit

This batch is exclusively B+ Day-2 council rows (`action_label=B`, both SLINGSHOT C1). It structurally cannot produce A1/A2/TRADE rows, so zero TRADE is expected, not a routing defect. `A1_REACHABLE` and `A2_EXECUTABLE_REACHABLE` are **NOT_EVALUABLE** — no A1/A2 rows in scope and no isolated routing harness available; no synthetic positive controls were run. `ZERO_TRADE_CAUSE = NO_ZERO_TRADE_ISSUE` for this batch. Carried-forward systemic concern: `learning_loop_executive_digest_2026-05-20.md` §4 documents post-V5.9.19 zero A1 / zero TRADE / all-A2-to-COUNCIL across the full decision log — an open implementation/routing investigation, not a threshold-change recommendation, and not evaluable from this B+-only batch. audit_basis = ACTUAL_CORPUS.

---

## Advisor responses

### The Contrarian

Both candidates fail the same way: the R:R only passes after someone moves the goalposts.

**KURA — CANCEL, confidence high, blocker: manufactured R:R, playbook-only.** The fatal flaw is staring at you. The honest target is the pack's MM target $11.22 — that yields 0.60R. To get to "2.51R" you have to (a) adopt the recent 52w high $12.14 as target AND (b) tighten the stop to a Day-1 midpoint that has zero structural meaning. Two adjustments stacked to clear a floor. Worse: this is a delayed Day-6 post-EP move on a grade-B catalyst, and the playbook explicitly names Day-7 gap-fill as a failure mode. You'd be entering at the exact moment the documented failure clock starts. Path B's "4.28R" requires a pullback that hasn't happened — you're trading a hypothetical. SLINGSHOT has 0/137 resolved and a noted ~17.5% triggered win. Don't pay for that lottery ticket with a fabricated number.

**ROIV — DEFER, confidence high, blocker: inflated target, playbook-only.** The prompt convicts itself: "$40 makes the R:R pass; against the defensible $35 target Path A would be ~1.0R." That is a back-solved target wearing a different costume after the EVAL_2R_FALLBACK $39.68 was already thrown out. A stock at a new ATH, +48.9% above its 200SMA, does not get a 22% measured-move target assumed into existence. The A-grade catalyst is real — that's the only reason this isn't a cancel — but a real catalyst with a fake target is still a losing trade structure. Defer; let it actually pull back and re-qualify on honest geometry.

Execution: any Thu/Fri entry eats a 3-day Memorial Day weekend on extended biotech — gap risk you are not compensated for.

### The First Principles Thinker

You're asking the wrong question. The framed question is "Path A or Path B for each ticker?" — but that presupposes there's a trade here. There isn't. Rebuild from the ground up:

What are you actually trying to do? Capture edge. Edge = a setup where the probabilities favor you. So the real question is: does a fixed R:R floor of 2.0 measure edge? No. R:R is a ratio of two numbers you partly choose. Both candidates failed it on Day-1, and every rescue path "passes" only by moving an input — tightening the stop (Path A) or assuming a deeper pullback (Path B). You are not discovering edge; you are reverse-engineering a number that makes a pre-decided trade legal. That is the exact defect the 5/20 council named: back-solved targets and Day-2 pullback rescues.

Strip it to base reality:
- **KURA:** Grade B, delayed Day-6 continuation, target $12.14 = a chart line. Path B's 4.28R exists only because the stop is the imagined Day-2 low. It's a hypothetical R:R on a hypothetical entry. **Cancel.** Confidence 80%. Blocker: manufactured R:R / weak catalyst. Playbook-only.
- **ROIV:** Genuine A-grade catalyst — that's real. But $40 target is a fabrication ($35 is defensible; against $35 Path A is ~1.0R). +48.9% above 200SMA means you'd be buying the reaction, not the opportunity. The catalyst is real; the entry is not. **Defer.** Confidence 75%. Blocker: inflated target / extension. Playbook-only.

The honest move: SLINGSHOT has 0/137 resolved outcomes. You have no evidence this family pays. The disciplined answer to "no evidence" is "don't fund it" — not "construct an R:R that lets me." Plus Friday entry = 3-day-weekend gap risk on illiquid biotech. Two reasons to wait, zero to rush. 0 promote / 1 defer (ROIV) / 1 cancel (KURA). Log both as playbook-only for calibration.

### The Expansionist

**ROIV — DEFER (lean promote-watch), confidence 65%, blocker: target geometry, playbook-only.** Here's the upside everyone's about to miss: ROIV is a genuine A-grade, confidence-92, multi-vector catalyst — earnings beat, $770M cash settlement, Breakthrough Designation, AND positive RA data — printing a new all-time high on 3.10x volume. That is a four-engine ignition, not a momentum echo. The +48.9% above 200SMA isn't "extended risk," it's a stock in price discovery with no overhead supply. A new ATH means every holder is profitable — the cleanest possible tape. The $35 round-number target is the timid read; it's just the first $5 magnet, not a ceiling. A stock breaking out on settlement-funded balance-sheet strength can run a measured move. But — be honest — Path A's $40 only passes R:R because the target was inflated; against the defensible $35 it's ~1.0R. Don't manufacture it. The real expansion play: defer one session, let Friday confirm continuation above $33, and re-rank for a clean structural entry rather than forcing a holiday-weekend hold on a back-solved number.

**KURA — CANCEL, confidence 70%, blocker: catalyst quality + manufactured R:R, playbook-only.** KURA is the trap dressed as opportunity. A grade-B, delayed Day-6 post-earnings pop is a laggard chasing the move, not leading it. Both rescue paths only clear 2.0 by tightening the stop into Day-1's midpoint — that's R:R engineered, not earned. No upside thesis survives that.

SLINGSHOT family: n=137, zero resolved, win_rate nan — verdicts are playbook-only and must be logged for calibration. Prior weak SLINGSHOT reads (~17.5% triggered win) argue for patience, not against ROIV's quality.

### The Outsider

The whole exercise has a tell that nobody inside seems to notice: you are spending serious effort engineering entries for a setup family with 137 signals and zero resolved outcomes. You don't know if SLINGSHOT works. The one number you do have — 17.5% triggered win rate, avg 3d −3.7% — says it loses. An outsider reads that and asks: why is this on the council at all? You are debating paths down a road that base rates say is a cliff.

KURA: The "rescue" is the problem. Day-1 R:R is 1.26. Both paths only clear 2.0 by tightening the stop until the math works — Path A's 6.7% stop and Path B's $9.50 stop aren't risk discipline, they're R:R cosmetics. The honest target ($12.14) against the honest pack MM target ($11.22) is 0.60R. The catalyst is grade B and a delayed Day-6 reaction, with gap-fill named as an explicit failure mode. CANCEL. Confidence 75%. Blocker: manufactured R:R + weak immature family. Playbook-only.

ROIV: Better catalyst — A-grade, fresh, multi-vector, 92 confidence. But the $40 target is indefensible and you already know it: the prompt itself says against the real $35 target Path A is ~1.0R, and you already killed the $39.68 back-solved version as forbidden. $40 is the same forbidden move wearing a different label. A stock at a new ATH, +48.9% over its 200SMA, does not get a generous measured-move target — extension argues the opposite. DEFER. Confidence 70%. Blocker: inflated target; honest geometry fails 2.0. Evidence-backed only on extension; setup playbook-only.

Weekend risk: any Thu/Fri entry eats a 3-day hold on biotech — asymmetric gap risk both directions. That alone argues against forcing either today.

### The Executor

**KURA — DEFER. Confidence: high. Blocker: no clean mechanical trigger. Playbook-only.** Path A is a fiction. "Hold $9.68 through first 30 min then enter at $10.38" — you can't place that. It requires a manual judgment call at 10:00 ET, then a chase entry, and the R:R 2.51 only exists if you assume the stop never gets touched intraday before fill. That's not an order, it's a hope. Path B is cleaner mechanically (limit buy stop $10.38, stop new Day-2 low) but you're back-solving: R:R 4.28 only works against the 52w-high $12.14, while the pack's own MM target $11.22 gives 0.60R. Against the honest target this fails the floor. Delayed Day-6 continuation + grade-B catalyst + explicit Day-7 gap-fill risk + 3-day weekend = no. Defer.

**ROIV — DEFER. Confidence: high. Blocker: inflated target. Playbook-only.** The mechanics here are actually executable: buy-stop $33.00, stop $31.07, DAY order. The problem is the destination. $40 is a 22% measured move conjured specifically to clear the 2.0 floor — against the defensible $35 target Path A is ~1.0R. That is exactly the "back-solved target" defect the 5/20 council flagged 4 cancels for. A-grade catalyst doesn't fix a 1.0R trade at a new ATH +48.9% above 200SMA. Path B's pullback needs a 6-7% retrace that may never come; un-actionable Thursday.

**Both: do nothing at Thursday's open.** No order goes in. SLINGSHOT has 0 resolved outcomes — first maturity 5/22 — so every verdict is playbook-only, log for calibration. If either is revisited, DAY orders only; never GTC into a Memorial Day weekend on an extended biotech.

---

## Peer review round

Anonymization map: **Response A = Executor · Response B = Contrarian · Response C = Outsider · Response D = Expansionist · Response E = First Principles.**

### Review 1
Strongest: B — diagnoses the shared failure mechanism precisely and is the only one to count the *number* of stacked adjustments on KURA (target swap + stop tighten). Correct split by catalyst quality. Biggest blind spot: D — its ROIV "every holder profitable / no overhead supply" is a momentum-narrative rationalization that nearly talks itself into promote-watch on the same $40 geometry it then admits is inflated; D ignores the base rate entirely. Base rate: A ignores it; B/C/E use it well; E mildly overreaches treating an immature family as proven-bad. All missed: nobody questions whether SLINGSHOT (0 resolved) belongs on the council at all — escalation policy, not per-ticker triage, is the real defect; nor proposes a size haircut or encoded Day-6/7 re-evaluation trigger.

### Review 2
Strongest: B — tightest reasoning per word; nails the shared defect and the verdict split (CANCEL KURA, DEFER ROIV). Biggest blind spot: D — romanticizes ROIV then argues itself out of its own thesis; sentiment substituting for mechanics. Overfit: C and E lean hard on "0/137, 17.5% triggered win" to argue the family loses — a 17.5% triggered win is meaningless without payoff distribution and could still be positive-expectancy; treating a noisy immature stat as proof overfits thin data. All missed: position sizing as the real lever — a sub-floor R:R can be made acceptable with smaller size rather than a binary promote/cancel; and nobody questions whether the 2.0 floor itself should be revisited given it keeps producing back-solved rescues.

### Review 3
Strongest: B — names the core defect precisely and counts KURA's two stacked adjustments; separates real catalyst from fake target cleanly. Biggest blind spot: D — builds a promote-watch case then concedes Path A is manufactured; romanticizes +48.9% above 200SMA as bullish while every other path treats extension as risk, and never reconciles that. Base-rate use: C overfits — 0 resolved means the win-rate is an in-flight snapshot, not a settled base rate; E uses the same data more honestly ("no evidence" → "don't fund it"). All missed: nobody questioned whether the 2.0 R:R floor itself is the right gate, or proposed a process fix so back-solved targets get rejected at intake rather than re-litigated per ticker.

### Review 4
Strongest: B — names the precise mechanism and counts the two stacked adjustments; separates ROIV's real catalyst from its fake target, justifying defer-not-cancel. Biggest blind spot: D — talks itself into "lean promote-watch," exactly the extension-euphoria the other four flag as risk. Base-rate misuse: C overfits, treating 17.5% / 0 resolved as proof "it loses"; E uses it more honestly; A and D underuse it. All missed: nobody questions whether the floor itself should block promotion, proposes smaller starter positions sized to honest R:R, defines what evidence graduates SLINGSHOT from immature, or notes that deferring ROIV still leaves the Memorial Day gap unresolved next session.

### Review 5
Strongest: B — nails the diagnosis (manufactured R:R via stacked adjustments) and the verdict split; uniquely names why ROIV escapes cancel (a real catalyst) while still rejecting the trade. Biggest blind spot: D — talks itself into "lean promote-watch" on ROIV via a narrative that is exactly the bullish story used to justify the inflated $40; frames $35 as "timid." Base-rate use: A ignores it; C borderline-overfits by treating one unresolved-family stat as proof it "loses"; E correct; D underweights. All missed: nobody questioned why a 0-resolved family has a 2.0 R:R floor at all, nor proposed a paper/tracking promotion to generate the outcomes the family needs.

---

## Chairman synthesis

### Reasoning Path Convergence

The Contrarian, First Principles, Outsider and Executor paths each arrived at the same structural finding by different routes: **both candidates fail the Day-1 2.0 R:R floor honestly, and every proposed Day-2 path "passes" only by manufacturing geometry.** The Contrarian reached it via fraud-detection (counting two stacked adjustments on KURA — target swap *and* stop tighten); First Principles via problem reframing (R:R is a ratio of inputs you partly choose, so back-solving it is reverse-engineering legality, not discovering edge); the Outsider via fresh-eyes pattern-matching ("Path A's 6.7% stop and Path B's $9.50 stop aren't risk discipline, they're R:R cosmetics"); the Executor via order-desk mechanics (Path A "hold $9.68 through first 30 min then enter" cannot be placed as an order). The peer-review round unanimously rated the Contrarian path strongest for naming the mechanism most precisely.

All five paths also converged that **ROIV's A-grade catalyst is genuinely real** — fresh, multi-vector, conf 92 — and that this is the single reason ROIV is a DEFER rather than a CANCEL.

All five paths converged on **0 promote**.

### Reasoning Path Divergence

The one genuine split was **KURA cancel vs defer**. Four paths (Contrarian, First Principles, Outsider, Expansionist) said CANCEL; the Executor said DEFER. The Executor's DEFER rests purely on mechanical un-executability ("no order goes in Thursday") — but its own analysis concedes Path B back-solves against the 52w high and the catalyst is a weak delayed laggard. The Executor's *substance* supports CANCEL; it landed on DEFER as a softer label for the same "do nothing" outcome. The CANCEL paths add the decisive point the Executor's framing omits: KURA is not a fixable-geometry problem awaiting a cleaner Day-2 — it is a grade-B *delayed Day-6* post-EP chase entering the explicitly documented Day-7 gap-fill failure window, with no honest target that clears the floor. That is a rejection of the signal, not a deferral of timing.

### Blind Spots the Reasoning Paths Caught

The peer review unanimously flagged the **Expansionist path's ROIV case as the biggest blind spot**: "price discovery with no overhead supply," "every holder profitable," "four-engine ignition," "$35 is timid" — a momentum narrative that nearly produced a "lean promote-watch," then conceded its own $40 geometry is inflated. Reviewers were blunt that this is exactly the extension-euphoria the other four paths read as *risk*: a stock +48.9% above its 200SMA is a warning, not a feature. The Chairman explicitly down-weights the Expansionist's ROIV upside framing — a real catalyst does not rescue a fabricated target.

Peer review also caught that the **Outsider and First Principles paths mildly overfit the immature SLINGSHOT stat** ("17.5% triggered win → it loses"). With 0 of 337 SLINGSHOT rows resolved, that 17.5% is an in-flight snapshot, not a settled base rate. The correct use of immature data is: *no evidence either way → playbook-only, do not lean on it* — not *proven loser*. The Chairman adopts that correction. The verdicts below stand on playbook geometry and catalyst quality, not on the 17.5% figure.

Finally, all five paths missed a process-level point the reviewers raised independently: a setup family with **zero resolved outcomes** keeps generating B+ rows that consume full council cycles and produce back-solved-target rescues. That is an intake/escalation-policy issue (and a question of whether the static 2.0 floor is the right gate at all) — noted here for Kevin as monitoring context. It does **not** change either verdict.

### Chairman verdict

The Chairman weighted the Contrarian path's fraud-detection framing (peer-review's unanimous strongest) and the convergent First Principles / Outsider / Executor structural findings against the Expansionist path's ROIV upside argument, and concludes:

**KURA — CANCEL. Confidence: medium-high. Blocker: C1. Playbook-only.**
Day-1 R:R 1.26 fails the 2.0 floor. Both rescue paths manufacture R:R: Path A stacks two adjustments (adopt the 52w-high $12.14 target *and* tighten the stop to the structurally meaningless Day-1 midpoint $9.68); Path B back-solves 4.28R against an imagined, not-yet-existing Day-2 low. Against the honest pack MM target $11.22 the trade is 0.60R. The catalyst is only grade B and the +15.4% is a *delayed Day-6* post-EP continuation — a laggard chasing the move into the explicitly documented Day-7 gap-fill failure window. There is no honest tradeable entry today and no honest path to one. CANCEL the current signal; KURA may re-qualify later only on a fresh, clean SLINGSHOT signal with structurally derived geometry that clears the floor without manufacture. (Backward-compatible action-label inference: no `final_trade_status` supplied; `tier=TAKE` is dashboard focus only and is not trade authorization.)

**ROIV — DEFER (Day-2 alert). Confidence: medium-high. Blocker: C1. Playbook-only.**
The A-grade, multi-vector, fresh signal-date catalyst (conf 92) is genuinely real — that is why this is a DEFER, not a CANCEL. But the geometry is not tradeable as presented. Day-1 R:R 0.64 fails the floor badly. Path A's 3.63R exists *only* against an inflated $40 target — a 22% measured move that is a relabel of the forbidden EVAL_2R_FALLBACK $39.68; against the defensible $35 target Path A collapses to ~1.0R. Path B is a textbook **Day-2 pullback rescue**: it needs a 6-7% retrace from the close, and a 6-7% fade of a new-ATH gap would itself damage the breakout thesis it depends on — and SLINGSHOT pullback rescues have **no mature base-rate evidence**. ROIV is also +48.9% above its 200SMA (extended). DEFER as a Day-2 alert: re-qualify only on honest structural geometry — a confirmed continuation that produces R:R ≥ 2.0 against a defensible target (not $40), with no forced hold across the Memorial Day weekend.

Both verdicts are **playbook-only** and must be logged for calibration: SLINGSHOT has 0 resolved outcomes and self-calibration is INSUFFICIENT_DATA (0/30). No outcome evidence was used to override any rule, and the immature 17.5% snapshot was not used as decisive evidence in either direction.

### Portfolio Heat

**No promoted exposure.** 0 PROMOTE verdicts → no risk is being put on. For Kevin's awareness if he overrides: KURA and ROIV are **both biotech/pharma** — that is *direct sector correlation*, not merely broad risk-appetite read-through; taking both would concentrate single-industry exposure. Execution guardrail (applies only if a future Day-2 re-qualification produces an honest entry): the review date is Thu 2026-05-21 and Mon 2026-05-25 is Memorial Day (market closed) — use **DAY orders / cancel-before-close**, never an open-ended GTC into the 3-day weekend on an extended biotech name.

### The one thing to do first

**Thursday at the open, place no orders on either name.** KURA is cancelled — drop it from the active screen; ROIV is a watch-only Day-2 alert — set a passive alert for a confirmed continuation that yields an honest R:R ≥ 2.0 against a defensible target, and do not act on the inflated $40 target or a thesis-damaging pullback.

## Council outcome CSV draft

Rows written to `council_outcomes_2026-05-21.csv`:

- `2026-05-20,2026-05-21,KURA,SLINGSHOT,B+,C1,CANCEL,medium-high,...`
- `2026-05-20,2026-05-21,ROIV,SLINGSHOT,B+,C1,DEFER,medium-high,...`
