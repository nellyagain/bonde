# Council Transcript — TVTX V5.8.6 Day-13 Reclaim

**Date:** 2026-05-03
**Decision date:** Monday 2026-05-04 open
**Ticker:** TVTX (biotech)

---

## Original Question

V5.8.6 surfaced TVTX as B with the following:

- Setup family: DELAYED_EP (reclaim trigger fired today; RECLAIM; days_since_spike=13)
- CONFLICT context: Grade A catalyst (full FDA approval of FILSPARI for FSGS, April 13) AND extended_run_flag = True. V5.8.6 graduated severity: distance_from_21ema_pct=15.9% with bars_since_10ema_break=15 → MODERATE → soft demote to B; A2 only on Day-2 inside-day or 10/21 EMA pullback. Volume also fails (1.14x below 1.5 default and below 1.2 floor).

Gate values: today_pct 4.75%; mb_vol_ratio_50 1.14x (FAIL Gate-3 default 1.5x AND 1.2 floor); ep_gap_pct 0.95%; close_pct_in_range 77.82% (PASS); pause_high 42.69; trigger_price 42.69 (DEP reclaim); invalidation 42.08 (today_low) or 41.10 (10EMA approx); consec_up_days 2; pct_closes_above_21ema_10 100%; bars_since_10ema_break 15; distance_from_21ema_pct 15.9% (Moderate → soft B); extended_run_flag True; ep_spike_flag False; delayed_ep_orig_gap_pct 35.28%; delayed_ep_days_since 13; delayed_ep_trigger RECLAIM.

Dashboard: composite 3.75; comp_rating 76; rs_3month 97; funds_pct 74; quality_gate_passes True; speculative_flag False.

Catalyst: full FDA approval of FILSPARI in FSGS (April 13, 2026); Grade A; first-and-only approved medicine for FSGS; ~30K addressable patients on top of IgAN base; analyst raises through April 24-29 (Guggenheim $56, Citi $48 "upside catalyst watch"); confidence 85.

Decision being weighed: Take Day-13 reclaim above $44.70 Monday, wait for Day-2 inside-day with vol ≥1.5x or pullback to 10EMA (~$41.7) / 21EMA (~$38.1), or pass entirely.

Account: $100k, 1% risk = $1,000, 0 positions held, regime unspecified.

---

## Framed Question (sent to all 5 advisors)

A trader's V5.8.6 system flagged TVTX as a B-grade setup. Choose among:
1. Take a Day-13 DELAYED_EP reclaim entry above $44.70
2. Wait for Day-2 inside-day with vol ≥1.5x avg, OR pullback to 10EMA ~$41.70 / 21EMA ~$38.10
3. Pass entirely

Setup: DELAYED_EP RECLAIM, days_since_spike=13. Grade A FDA catalyst (FILSPARI/FSGS April 13). +4.75% today, close 77.82% of range. Volume FAIL (1.14x vs 1.5 default + 1.2 floor). Geometry: 15.9% above 21EMA, 15 bars since 10EMA tag, extended_run_flag True. Original April 13 gap was 35.28%. Composite 3.75, rs_3month 97. System decision_reason: "Reclaim genuine but late-stage geometry; A2 only on Day-2 inside-day or 10/21 EMA pullback per V5.8.6 moderate-extension rule." Account $100k, 1% risk = $1,000, zero positions.

---

## Advisor Responses

### The Contrarian (verdict: PASS)

This setup is a trap dressed up in Grade A clothing. Let me name the fatal flaws nobody's saying out loud.

The catalyst is already priced in. FDA approval was April 13. The 35.28% gap that day WAS the trade. You are now 13 sessions late, sitting 15.9% above the 21EMA, on a stock that has closed above the 21EMA 100% of the last 10 sessions. That's not opportunity — that's exhaustion geometry. Every late chaser who saw the Guggenheim $56 target is already long.

The volume tells the truth the price won't. 1.14x on a "reclaim" day after a +4.75% move? That fails BOTH the 1.5x default AND the 1.2x floor. This is not institutional accumulation — this is retail FOMO and short-covering on thin participation. Reclaims without volume are bull traps. Period.

Your own system is screaming at you. V5.8.6 demoted this to B and explicitly said "A2 only on Day-2 inside-day or EMA pullback." Option (1) is overriding your system because the catalyst feels sexy. That's how accounts blow up — discretionary overrides of quantified rules during late-stage extensions.

Option (2) is also a trap. Waiting for the 10EMA pullback to $41.7 sounds disciplined, but on a Day-13 extended name, the first pullback often becomes the failed bounce that triggers the real flush to the 21EMA or below. You'll be buying weakness in a topping pattern and calling it discipline.

Take Option (3). Pass entirely. Zero positions held means zero pressure to act. The opportunity cost of skipping TVTX is nothing. The cost of a stop-out 15.9% above the 21EMA on a thin-volume reclaim is $1,000 plus the tilt that follows. There will be A-grade Day-1 setups next week. This isn't one.

### The First Principles Thinker (verdict: PASS + BACKTEST)

The user isn't actually asking "which of these three actions?" They're asking: "Please validate my system so I don't have to take responsibility for the decision."

Strip the jargon. Here's what's actually true:

A stock gapped 35% on a real catalyst three weeks ago. It's now 16% above its 21EMA, has run 13 days, and today's "reclaim" happened on 1.14x volume — meaning nobody with size was actually buying. The system itself demoted it to B. The system itself said "wait for pullback or inside day." The trader is now asking strangers on the internet whether to override the system that already gave them the answer.

That's the real question: "Why don't I trust my own framework?"

Rebuild from zero. What does a trader actually need to make money? An edge, repeated many times, with losses smaller than wins. Does chasing a Day-13 extended move on failing volume fit that description? No. Has it ever, statistically, across the trader's own backtest? They didn't say — which is suspicious, because that's the only number that matters here. Not Guggenheim's $56 target. Not "Confidence 85." Not the FDA approval from three weeks ago that's already priced in.

The right question isn't (1), (2), or (3). The right question is: "What is my historical win rate on B-grade DELAYED_EP setups with sub-1.2x volume on Day 10+?" If they don't know, they shouldn't trade it. If they do know and it's negative-expectancy, the debate is over.

Action: Pass on Monday's reclaim. Set alerts at $41.70 and $38.10. Spend the weekend pulling the backtest stats on this exact subtype. Stop asking the council to ratify what your system already told you.

### The Expansionist (verdict: TAKE + UPSIZE 1.5x)

TVTX is a classic case of a system pattern-matching against generic "extension" rules while missing a once-per-decade fundamental inflection. FILSPARI just became the first-and-only approved drug for FSGS — a disease with zero competing approved therapies and ~30K addressable US patients sitting on top of an already-ramping IgAN franchise. That's not a "catalyst gap" to fade. That's a re-rating in progress.

Here's what the system isn't pricing:

The analyst wave is early. Guggenheim $56 and Citi flagging "upside catalyst watch" on April 24-29 — these are the first movers. When Q2 scripts print and Street models get rebuilt around dual-indication peak sales ($1.5B+), you get a second leg of estimate revisions. Day-13 isn't late; it's the quiet middle before institutions finish building positions.

The "weak" 1.14x volume is bullish, not bearish. Holding 78% of range on declining volume after a 35% gap means no supply. Sellers are exhausted. The reclaim above $44.70 unlocks air to $50-56 with no overhead resistance.

Asymmetric play: Take the reclaim entry Monday, but size it 1.5x normal ($1,500 risk) because the catalyst confidence is 85 and the setup is binary — either FILSPARI is a franchise drug and this goes $60+, or it isn't and your stop costs you 1.5R. Stop under $41.50 (below 10EMA). Target: scale 1/3 at $52, 1/3 at $58, let final third ride on a 21EMA trail through earnings.

Waiting for the inside-day or 10EMA pullback means watching it gap to $48 on a script-tracker leak. The Day-2 setup people are looking at the same chart. Be early, be bold, take the reclaim.

### The Outsider (verdict: PASS)

Fresh eyes here. I don't know V5.8.6, I don't know what a "Gate" is, and I don't know why a B becomes tradeable when the rules apparently say it shouldn't. But here's what jumps out.

You built a system. The system said no. You're now shopping the question to a council. That's the tell. You're not asking "is my system right?" — you're asking "can someone give me cover to override it?"

Look at what you wrote: the catalyst is three weeks old. The 35% gap already happened. Analysts already raised targets. The stock is already 15.9% extended from its 21EMA and hasn't touched the 10EMA in 15 bars. Today's volume missed your own threshold — not by a hair, by a lot (1.14x vs a 1.5x target, barely above the 1.2 floor you call "hard"). Every piece of evidence you presented is something that happened to somebody else already. You're describing a party you weren't invited to and asking whether it's too late to show up.

Option 1 is chasing. Option 2 is what your own system told you to do. Option 3 is also what your system told you to do. So really there's one option (your system's answer) and two flavors of overriding it.

One more thing a stranger notices: you have zero positions and a fresh $100k. That's the actual variable here. Boredom and an empty book make B-grades look like A-grades. The trade you take to feel productive is usually the one that funds someone else's vacation.

Trust the thing you built when you were calmer than you are now.

### The Executor (verdict: WAIT — INSIDE-DAY VARIANT)

**Option 1 — Reclaim $44.70**
- Entry: stop-limit buy $44.72 / $44.85 (avoid chasing past $44.90).
- Stop: $42.07 (under today_low). Risk/share = $2.65. Shares = $1,000 / $2.65 = 377.
- Position notional = ~$16,860 (16.9% of account). Fine.
- Targets: 1/3 at $48 (+$3.30, ~1.25R), 1/3 at $52, trail last 1/3 under rising 10EMA.
- Pre-open checklist: gap < +3% (else skip — entry already extended), pre-market volume > 200k by 9:00, SPY/XBI not red >0.5%, no overnight biotech tape-bomb.

**Option 2 — Wait for inside-day OR EMA pullback**
- Inside-day trigger: break of Day-2 high with vol pace ≥1.5x 20-day avg by 10:30. Stop under inside-day low.
- 10EMA pullback ~$41.70: entry on 5-min reversal bar, stop $40.95. Risk/share $0.75 → 1,333 shares, $55.6k notional. Cap at 25% = 449 shares.
- 21EMA ~$38.10: entry on reclaim, stop $37.40. Risk/share $0.70 → 1,428 shares, capped.

**Option 3 — Pass: free, always available.**

**Verdict:** Take Option 2, specifically the inside-day-with-volume variant. Here's why mechanically: your own system grade is B, volume today was 1.14x (below your 1.2 floor, well below 1.5x trigger), and you're 15.9% above 21EMA on bar 15. Option 1 forces you to pay up another 4.7% into extension on a setup your system already soft-demoted. That's how you get stopped at $42.07 on a normal pullback and lose $1,000 on a thesis that's still intact.

Monday morning: set alerts at $44.70, $42.69 (inside-day pivot), $41.70, $38.10. Don't touch the keyboard otherwise.

---

## Anonymization Mapping (for Peer Review)

- A = Outsider
- B = Expansionist
- C = Executor
- D = Contrarian
- E = First Principles

---

## Peer Reviews

### Reviewer 1
**1. Strongest: Response C.** The only one that respects the user's actual decision framework while doing real work — exact stop levels, share counts, position sizing math, pre-open checklist, verdict tied to the system's own rules. A, D, E converge on "trust the system" but C operationalizes it. Treats the trader as an adult executing a plan, not a patient needing therapy.

**2. Biggest blind spot: Response B.** Tells the trader to upsize to 1.5R and override an explicit system demotion based on narrative (peak sales TAM, "be bold"). Misreads 1.14x volume as bullish exhaustion-of-sellers — post-hoc rationalization. Ignores that the trader's edge comes from rule adherence, not from out-thinking analysts on biotech fundamentals. Worst: no falsification criteria beyond a stop.

**3. What all five missed:** None addressed the base-rate question on the system itself — V5.8.6's historical performance on B-grade DELAYED_EP signals specifically. E gestured at it but punted to the user. Also missed: opportunity cost framing across the watchlist (zero positions held doesn't mean TVTX is the only candidate Monday), and correlation/sector exposure — XBI regime and biotech beta should gate any biotech entry regardless of single-name setup. The council debated TVTX; nobody asked what else is on the screen.

### Reviewer 2
**1. Strongest: E.** Reframes the actual problem. The trader isn't asking "which option," they're asking permission to override their own system. E demands the only data that resolves it: historical win rate on this exact subtype. Without that number, every other response is opinion. A gestures at the same insight emotionally; E operationalizes it.

**2. Biggest blind spot: B.** Treats fundamentals as if they predict 2-week price action. "$1.5B peak sales" is irrelevant to a Day-13 extended entry. B ignores the system's explicit demotion, the failed volume floor (not just default), the 15.9% extension, and recommends 1.5x sizing on a setup the framework rated B. This is the exact override-with-narrative behavior A and E warned about.

**3. What all five missed:** Position-sizing math under the system's own demotion. If the system soft-demoted to B and gated A2 on specific conditions not met, the correct risk isn't 1% — B-grade setups historically warrant fractional risk (0.25-0.5%). Also missed: opportunity cost framing. Capital tied up in a B-grade chase blocks the A-setup D mentions. None addressed earnings date proximity, which changes the trail logic C proposed.

### Reviewer 3
**1. Strongest: E.** Reframes from "what trade?" to "why are you overriding the system?" and prescribes falsifiable homework (backtest B-grade DELAYED_EP with sub-1.2x volume on Day 10+). A and D reach the same Pass verdict but assert it; E gives the trader a way to update the framework rather than just skip Monday. C is operationally tight but answers the wrong question.

**2. Biggest blind spot: B.** Up-sizing to 1.5x risk on a setup the system itself grades as failing two of three volume gates, on Day 13 of a known catalyst, is exactly the trade the V5.8.6 rules were written to prevent. "Sellers exhausted" is unfalsifiable narrative; 1.14x volume is the data. B is also silent on the asymmetric downside of a Day-13 failed reclaim into a gap-fill.

**3. What all five missed:** None questioned the signal itself. A Day-13 DELAYED_EP RECLAIM firing at all on a name 15.9% extended with 15 bars since 10EMA suggests the V5.8.6 scanner has a parameter gap — DELAYED_EP probably needs a max-extension or max-bars-since-10EMA filter. The council debated trade/no-trade; nobody flagged that the system surfaced a structurally low-quality B in the first place. That is the durable fix; Monday's TVTX decision is noise by comparison.

### Reviewer 4
**1. Strongest: E.** The only response that attacks the actual decision-quality problem. A, C, D all answer the trade question; E reframes to the meta-question that determines every future B-grade DELAYED_EP setup. Converting one trade's ambiguity into a backtest spec ("B-grade, sub-1.2x vol, Day 10+") compounds. The others are one-shot answers.

**2. Biggest blind spot: B.** Treats fundamentals as if they override the system's mechanical signal. The setup already passed an FDA-catalyst check — Grade A is priced in. B's "low volume = no supply" is the textbook rationalization for chasing extension; on Day-13, 15.9% above 21EMA, low volume is more often distribution-by-absence than accumulation. Upsizing to 1.5x on a setup the system flagged B is exactly the discretionary override that destroys system edge.

**3. What all five missed:** Opportunity cost and base rate of the next setup. With zero positions and a fresh $100k, the relevant comparison isn't TVTX vs. cash — it's TVTX-now vs. the expected A-grade setup arriving within N days. None quantified the cost of waiting. Also missed: position in broader portfolio heat / correlation, and whether "boredom risk" (A) should itself be a tracked, sized metric rather than a vibe.

### Reviewer 5
**1. Strongest: E.** The only response that reframes the actual decision. A, C, D all answer "should I take this trade" — E answers "should you be asking this question at all without data?" The backtest demand is concrete and weekend-actionable. A reaches a similar conclusion but via psychology; E reaches it via epistemics, which is harder to rationalize away.

**2. Biggest blind spot: B.** Not the bullishness — the size-up. Recommending 1.5x normal risk ($1,500) on a setup the system graded B with two failed volume floors is the exact inversion of correct sizing. Conviction from fundamentals doesn't override mechanical risk rules; it's supposed to be filtered by them. B also ignores that "analyst wave early" and "sellers exhausted" are unfalsifiable post-hoc narratives.

**3. What ALL missed:** None addressed the meta-pattern. This is one ticker on one weekend — but the behavior (system says B, user convenes council) is the precedent that matters. If overriding produces a win, the system's authority is permanently degraded for every future B-grade. The council should be asked: "What rule governs when I'm allowed to ask you at all?" Without that, every B-grade becomes a council vote, and the system becomes decorative.

---

## Chairman Synthesis

### Where the Council Agrees

- **Don't take the $44.70 reclaim Monday.** 4 of 5 advisors converged on this. Volume violates two floors (1.14x vs 1.5x default + 1.2x hard floor); geometry is extended (15.9% above 21EMA, 15 bars since 10EMA tag). Three advisors pinned the same psychological tell: zero positions + fresh $100k + a B-grade signal you're shopping to the council = boredom-driven override.
- **The system already answered the question.** V5.8.6 explicitly conditioned A2 on inside-day OR EMA pullback. Discretionary override of a quantified rule, on the same day it fires, is the canonical edge-destroyer.
- **The Grade A catalyst is mostly priced in.** The 35% gap on April 13 was the trade. Day-13 entries on a name closing above 21EMA every day for 10 sessions are exhaustion geometry, not "early."

### Where the Council Clashes

- **Expansionist vs everyone on the upsize.** Expansionist argues 1.5x risk on the reclaim because FSGS is a once-per-decade re-rating. All 5 peer reviewers independently flagged this as the council's biggest blind spot. The criticism: conviction from fundamentals is supposed to be filtered by mechanical risk rules, not override them.
- **Executor vs Contrarian on the pullback path.** Executor green-lights Option 2 inside-day-with-volume. Contrarian argues that on Day-13 extended names, the first pullback is usually the failed bounce — so even Option 2 is a trap. Genuine disagreement; cannot be resolved without base-rate data.

### Blind Spots the Peer Round Caught

- **Base rate of the signal itself.** No advisor cited V5.8.6's historical win rate on B-grade DELAYED_EP with sub-1.2x volume on Day 10+. Without that, every position is opinion.
- **Position sizing under demotion.** If the system soft-demoted to B, correct risk is likely fractional (0.25–0.5%), not 1%. Expansionist proposed the inverse.
- **Opportunity cost across the watchlist.** Zero positions ≠ TVTX is the only candidate.
- **XBI / biotech regime gate.** Single-name biotech entries should be gated by sector regime regardless of setup quality.
- **Possible parameter gap in V5.8.6.** A DELAYED_EP RECLAIM firing on a 15.9%-extended, 15-bar-since-10EMA name suggests the scanner needs a max-extension filter. Durable fix is to the system, not Monday's trade.
- **Earnings proximity.** Changes Executor's trail logic; no advisor addressed it.
- **The meta-precedent.** If overriding a B produces a win, system authority is permanently degraded for every future B.

### The Recommendation

**Pass the $44.70 reclaim Monday.** Don't take it long, don't size up on it, don't argue yourself into it. The system flagged it B for two volume reasons and one geometry reason; all three are still true Monday morning.

**For Option 2, only the inside-day-with-confirmed-volume variant is live.** Skip the 10EMA pullback at $41.70 — Contrarian's point that first pullbacks on Day-13 extended names tend to be failed bounces is well-grounded enough that you shouldn't trade it without base-rate evidence. The 21EMA pullback at $38.10 is a different setup (re-test of trend) and worth a separate alert, not a present plan.

**If you still want the inside-day, size at 0.5% risk ($500), not 1%.** The system demoted to B; sizing should follow grade, not the trader's narrative. Multiple peer reviewers independently flagged that no advisor said this out loud.

**Then go fix the system.** A V5.8.6 RECLAIM firing on a name 15.9% above its 21EMA is information about the scanner, not about TVTX. Add a max-extension or max-bars-since-10EMA filter to DELAYED_EP. That change compounds; Monday's TVTX decision does not.

### The One Thing to Do First

This weekend, before Monday's open: pull historical results for B-grade DELAYED_EP setups with sub-1.2x volume, >10 bars since 10EMA tag, and >13% above 21EMA. If the sample is too thin, that's the answer — you don't have edge here, so you can't trade it. If win rate × avg win > loss rate × avg loss at acceptable expectancy, take only the inside-day-with-volume trigger at 0.5% risk. Otherwise set a 21EMA-tag alert at $38.10 and walk away from this name until a real reset.
