# LLM Council Transcript — A2 SLINGSHOT batch

- **Run date:** 2026-06-19 (Friday, **Juneteenth — US market closed**)
- **Signal date:** 2026-06-18 (Thursday close) · **Review date:** 2026-06-19 · **Next session:** Monday 2026-06-22
- **Candidates (15):** MYRG, ALTG, ANDE, APGE, AS, CGEM, GCMG, INSW, MPLX, MTSI, NPK, PSMT, ROK, SPXC, STTK
- **Routing:** all A2, all `TRIGGER_1_A2` (every A2 routes to council)
- **Verdict basis:** PLAYBOOK-ONLY (SLINGSHOT family has zero resolved outcomes)

---

## Original question

> council this: [pasted A2 SLINGSHOT promotion pack, 15 rows, signal_date 2026-06-18, review_date 2026-06-19]

## Framed question

Should any of these 15 A2 "SLINGSHOT" breakout candidates be promoted to executable trades? Decide PROMOTE / DEFER / CANCEL per ticker.

**Critical execution context:** 2026-06-19 is Juneteenth — US equity markets are closed. With the weekend, the next session is Monday 2026-06-22 (a 3-day gap). **All 15 candidates are un-triggered** — Thursday's close is below the buy-stop trigger for every name. These are forward-looking buy-stop / Day-2 confirmation setups, not same-day entries. Market mode: Risk-On.

**Outcome/base-rate context:** The SLINGSHOT setup family has **zero resolved outcomes** in the Bonde learning loop; the one resolved cousin (SPIR) took a loss. Verdicts are playbook-only. Playbook precedent: static EOD R:R must clear the 2.0 floor; severe extension without reset above the 200SMA is a HARD cancel rule (SPIR cancelled at +75%, UCTT +99.8%, ICHR +115.8%); slingshot_range_break must be TRUE; lowering entry just to make R:R pass = discouraged "Day-2 pullback rescue"; light Day-1 volume = no participation. KRNT precedent (2026-06-18): the only A2 PROMOTEd was already above its trigger; un-triggered A2s were DEFERred.

## Context Files Loaded

| Role | Path | Status | Notes |
|---|---|---|---|
| council_queue (this batch) | pasted A2 SLINGSHOT pack 2026-06-18 | LOADED | 15 rows, full pack columns |
| prior council outcomes | bonde_screener_cache/council_queues/council_outcomes_2026-06-18.csv | LOADED | KRNT precedent |
| prior SLINGSHOT outcomes | council_outcomes_2026-05-20 / 2026-06-03 / 2026-05-15 | LOADED | SPIR/UCTT/ICHR cancels; zero resolved |
| self-calibration | council_self_calibration_summary_2026-06-18.csv | LOADED | INSUFFICIENT_DATA (24/30) |
| reachability audit (prior) | council_reachability_audit_2026-06-18.csv | LOADED | A2→TRADE proven reachable |
| repo project instructions | /home/user/bonde/CLAUDE.md | LOADED | artifact push workflow |
| actionability SKILL.md | bonde_files/playbook/... | MISSING_OPTIONAL | operating from candidate packet + embedded rules |
| daily_decision_log (final_trade_status) | — | MISSING_OPTIONAL | legacy action-label fallback (all rows A2) |

## Council self-calibration status

**INSUFFICIENT_DATA.** Resolved disagreements: 24/30. No reliability percentage reported. Calibration is context only and does not change verdicts.

## A1/A2 Reachability Audit

- **A1_REACHABLE:** NOT_EVALUABLE (no A1 rows in corpus; no isolated routing harness).
- **A2_EXECUTABLE_REACHABLE:** TRUE — actual corpus proof (2026-06-09 NYT 2.21R, FOX 2.92R `final_trade_status=TRADE`; KRNT promoted-to-executable 2026-06-18).
- **ZERO_TRADE_CAUSE:** INSUFFICIENT_CLEAN_ROWS — zero promotes this batch because all 15 closed below trigger; no above-trigger / cleanly executable row. Not a routing bug.
- **Counts:** n_A1=0, n_A2=15, n_TRADE=0 (pre-council), n_A2→COUNCIL=15 (by design, Trigger 1).
- **Top demotion reasons:** no_trigger_confirmation (15/15); severe_extension (MTSI); liquidity_uninvestable (ALTG); rr_floor_pinned (GCMG/INSW/MPLX).
- **audit_basis = ACTUAL_CORPUS.** This is not a threshold-change recommendation — reachability is healthy; the batch simply has not triggered.

---

## Advisor responses (de-anonymized)

Anonymization mapping used in peer review: **A = Expansionist, B = Executor, C = Contrarian, D = Outsider, E = First Principles.**

### The Contrarian
All 15 are un-triggered buy-stops firing into a 3-day Juneteenth+weekend gap. A buy-stop above Thursday's close fills only on a gap-up or fast spike — the worst entry, chasing into a hole with the stop already underneath. The R:R numbers are EOD fictions; PROMOTE today is incoherent. HARD-CANCEL severe extension: MTSI +76.8% and MYRG +66% are the SPIR (+75%) precedent. Extension cluster INSW +35.6%, CGEM +31.6%, APGE +30.3%, PSMT +29.9% → CANCEL/strong-DEFER; APGE/CGEM unresearched biotech = binary long-weekend gap risk. R:R-floor traps GCMG 2.07, INSW 2.11, MPLX 2.14 → DEFER. Liquidity trap ALTG ($1.9M ADV) → CANCEL. AS vol 1.02x / MPLX +1.66% = drift → DEFER. Least-bad ANDE/NPK/ROK (real catalysts) → DEFER as Day-2 alerts requiring a Monday volume trigger-break; KRNT was promoted last time only because it was already above trigger. Net: PROMOTE zero. Playbook-only.

### The First Principles Thinker
The frame is wrong: you can't buy today and zero names triggered, so PROMOTE/DEFER/CANCEL is a false trichotomy. A slingshot is defined by the thrust through the range; none has thrust. You hold a watchlist; the real decision is the Monday trigger-and-confirm protocol. CANCEL now (hard extension): MYRG +66%, MTSI +76.8%, INSW +35.6%, CGEM +31.6% (57% range = no thrust), APGE +30.3%, PSMT +29.9%, plus ALTG ($1.9M ADV uninvestable). Everything else DEFER-pending-trigger. ANDE (5.33, +20%), NPK (3.54), ROK (3.43): watch with intent, volume-confirmed break only, never lower entry. AS/MPLX/GCMG light volume → demand confirmation. Monday protocol: act only on a trigger break on expanding volume; re-cancel any name that gaps through trigger; never lower the stop; recheck extension (>25% stays dead).

### The Expansionist
Playbook-only. NPK — PROMOTE on trigger, high: sole-source defense ammo backlog $1.75B > market cap, ext +8.6% (no extension risk), R:R 3.54, vol 2.13x, closed 99% of range; front of queue. ANDE — PROMOTE on trigger, high: best R:R 5.33, Benchmark $90 PT, Q4 beat, ag/China, vol 1.99x, ext +20%. ROK — PROMOTE on trigger, med-high: $1B buyback + raised FY26 + $525 PT, ext +20.5%, R:R 3.43. Queue NPK > ANDE > ROK; fourth slot MYRG (best un-researched C-name) but DEFER pending catalyst. MTSI HARD CANCEL (+76.8%). APGE/CGEM/STTK biotech and INSW/MPLX/AS/GCMG/PSMT/ALTG = mechanical passes, no upside → DEFER. ALTG $1.9M liquidity caps the prize. Concentrate Monday capital on NPK and ANDE.

### The Outsider
Three things are hard to justify. (1) Timing — 15 buy decisions on a closed market where nothing hit its price and nothing executes for 3 days; these are conditional reminders, not trades. (2) "No catalyst researched" on 11 of 15 means nobody looked → defer, not promote. (3) The numbers contradict the story: 0-for-1 strategy asking for 15 more bets; several names 30-77% above long-run average = chasing; tiny names (ALTG, STTK, CGEM) are noise. Leans: ROK PROMOTE 60%; ANDE PROMOTE 55%; NPK DEFER 50% (verify thin name); MYRG/MTSI/INSW/APGE/PSMT/SPXC/AS/GCMG/MPLX DEFER 65%; ALTG/CGEM/STTK CANCEL 70%. Batch over-promoted by the system.

### The Executor
Playbook-only. Order type first: nothing fills today; do NOT leave GTC buy-stops over the 3-day gap (Monday gap-up wrecks R:R). Monday pre-open, arm DAY buy-stop-limits (stop = trigger, limit = trigger + ~0.3-0.5% cap); re-arm daily. CANCEL biotech APGE/CGEM/STTK (binary/earnings gap risk; STTK ~$5 low quality). CANCEL GCMG (2.07)/INSW (2.11)/MPLX (2.14) — R:R on the 2.0 floor, gap-up busts it. CANCEL ALTG ($1.9M ADV). PROMOTE-on-trigger: ANDE (5.33), NPK (3.54, rng 99%), ROK (3.43, liquid), MYRG (2.57, stretched but clears, med), SPXC (3.40, soft 1.25x vol, med). DEFER: AS (vol 1.02x), MTSI (+77%), PSMT (DTE ~14d).

---

## Peer reviews

**Reviewer 1:** Strongest = First-Principles (reframe + actionable Monday protocol); Executor a close second on GTC-vs-DAY-limit mechanics. Biggest blind spot = Expansionist (treats EOD R:R as real, concentrates on un-triggered names). Rule misuse: Expansionist under-applies extension (MYRG should be near-cancel); the Outsider overfits the 0-for-1 base rate. All missed: batch-sizing/screener-process critique and simultaneous-trigger capital allocation.

**Reviewer 2:** Strongest = Executor (only one to convert the constraint into an executable mechanism). Biggest blind spot = Outsider (ignores mechanics/extension math). CANCEL vs DEFER: MTSI +76.8% qualifies for HARD CANCEL (Expansionist/Executor/Outsider wrongly defer it); MYRG +66% is under ~75% → DEFER, so Contrarian/First-Principles overreach hard-cancelling it; floor-pinned names correctly DEFER. All missed: SLINGSHOT zero resolved outcomes = unvalidated prior → paper-track rather than risk capital.

**Reviewer 3:** Strongest = Executor (gap-risk mechanics, correct + usable). Biggest blind spot = Outsider (hard PROMOTE probabilities on a closed market, no mechanics). The DEFER camp is right — "PROMOTE-on-trigger" for an un-triggered name collapses to DEFER-pending-trigger by the KRNT precedent. MYRG +66% is a CANCEL (no benefit of the doubt with zero resolved outcomes). All missed: the SLINGSHOT family's track record argues for a strategy-pause/size question, not per-name triage.

**Reviewer 4:** Strongest = Executor. Biggest blind spot = Expansionist (concentrating an unvalidated 0-outcome strategy). Calibration: the DEFER camp is right that +30-36% is moderate, not "severe without reset" (SPIR +75% / UCTT +99.8% is the band); Contrarian/First-Principles manufacture CANCELs the rule doesn't license; reserve HARD CANCEL for +66-77% (MTSI, arguably MYRG). All missed: the R:R 2.0 floor itself is an unvalidated assumption on a zero-outcome playbook; plus correlated Monday gap-up risk.

**Reviewer 5:** Strongest = Contrarian (gap mechanics + discipline); Executor close second. Biggest blind spot = Expansionist (concentrates on un-triggered 0-for-1 setups). Basket risk: nobody handled it. ANDE (ag) / NPK (defense) / ROK (industrial) are not direct sector peers but are all pro-cyclical risk-on beta; correlation spikes on a Monday gap-up — the only condition under which they fill. A triple-trigger is one correlated bet, not three. Missing: aggregate-R heat cap, reduced size when 2+ fire, max-concurrent-promote limit. All missed: the gap-up that triggers them is itself the correlation event; NPK is thin so a trigger+0.5% stop-limit may fill poorly.

---

## Chairman Synthesis

**PROMOTE none today. The honest deliverable is a Monday trigger-and-confirm protocol, not a basket of trades.** Every candidate is un-triggered into a 3-day holiday+weekend gap, so per-ticker R:R figures are end-of-day projections, not fill-able prices — a Monday gap-up would fill above trigger and silently break them. The Chairman weighted the First-Principles reframe (no thrust = no slingshot; this is a watchlist) and the Contrarian/Outsider discipline (KRNT precedent: PROMOTE requires being above trigger) above the Expansionist/Executor "promote-on-trigger" framing, which the peer round correctly relabeled as DEFER-pending-trigger.

**Extension rule:** sided with the calibrated reviewers over the two advisors who hard-cancelled the entire +30-36% cluster. The documented hard-cancel band is ≥+75% (SPIR/UCTT/ICHR). So **MTSI (+76.8%) is a clean CANCEL**; **MYRG (+66%) is a DEFER** with an explicit Monday extension re-check. Remaining CANCELs rest on independent hard reasons — ALTG (uninvestable liquidity), CGEM (3.11x volume but 57% close = absorption/failed thrust, extended biotech), STTK (~$5 noise-tier unresearched biotech). APGE stays DEFER because "unresearched" is a fixable data gap (LLY precedent), not a structural break.

**Catalyst-backed trio ANDE, NPK, ROK** are the front of Monday's queue as DEFER / watch-with-intent — only on a volume-confirmed trigger break, never by lowering entry to rescue R:R. Confidence medium; verdicts playbook-only.

### Per-ticker verdicts
- **DEFER (priority Day-2/trigger alerts):** ANDE, NPK, ROK
- **DEFER (watch):** MYRG (extension re-check), SPXC, AS, GCMG, INSW, MPLX, PSMT (pre-earnings DTE~14d), APGE
- **CANCEL:** MTSI (severe extension), ALTG (liquidity), CGEM (failed thrust/biotech), STTK (noise/biotech)
- **Tally:** PROMOTE 0 · DEFER 11 · CANCEL 4

## Portfolio Heat

**No promoted exposure** (0 PROMOTE). Exact account-risk sizing unavailable → qualitative, forward-looking.

Conditional basket warning: ANDE/NPK/ROK fill together only on a broadly strong Monday open. Not direct sector peers (ag / defense / industrial) → **broad risk-appetite read-through, not direct sector correlation** — but a simultaneous triple-trigger is closer to one correlated risk-on bet than three independent setups. Guidance: cap concurrent SLINGSHOT promotes Monday (max 2 of the trio, or down-size the third); later fills on the open gap should be reduced, not full risk; a weak Monday tape that gaps names *through* their triggers cancels the setups.

## Execution Guardrail — Friday/holiday gap

Do NOT leave GTC buy-stops over the Juneteenth+weekend gap (a Monday gap-up fills far above trigger — fatal for floor-pinned GCMG 2.07 / INSW 2.11 / MPLX 2.14). Monday protocol: arm **DAY buy-stop-LIMIT** orders pre-open (stop = trigger, limit ≈ trigger + 0.3–0.5%); require close/hold above trigger on ≥1.2x volume; re-arm each morning; re-check MYRG extension; abort below invalidation.

## The One Thing to Do First

Build the Monday 2026-06-22 trigger sheet for ANDE, NPK, ROK (watch MYRG): arm DAY buy-stop-LIMIT orders pre-open (limit ≈ trigger + 0.4%), require a close/hold above trigger on ≥1.2x volume, and cap the basket at two concurrent SLINGSHOT fills. Place nothing over the holiday/weekend gap.

## Council Outcome CSV Draft

One row per ticker → `council_outcomes_2026-06-19.csv` (schema: signal_date, review_date, ticker, setup_family, action_label, bplus_blocker_type, council_verdict, confidence, decision_reason, report_path, transcript_path). All `setup_family=SLINGSHOT`, `action_label=A2`, `bplus_blocker_type=NOT_BPLUS`. Verdicts: DEFER ×11 (ANDE, NPK, ROK, MYRG, SPXC, AS, GCMG, INSW, MPLX, PSMT, APGE), CANCEL ×4 (MTSI, ALTG, CGEM, STTK).
