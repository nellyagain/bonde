# LLM Council — Pre-Open Batch (6 tickers) — 2026-05-09

**Signal date:** 2026-05-08 · **Review date:** 2026-05-09
**Account:** $100K · 1.0% risk per position ($1,000 max) · 0 positions held · Regime Risk-On 10/10 (Normal sizing).
**Outcome / base-rate context:** Cohort age -2 days (most recent rows). Per immediately prior 2026-05-08 council batch: ACTIVE_BURST n=83 T+1d win 49.3% / avg -0.72%; EP_ACTIVE family n=64 IMMATURE_20D; ACTIVE_BURST × catalyst-A intersection n=2 (too small). All cohorts PARTIAL_OUTCOME / IMMATURE_20D. Per skill rules: outcome data is monitoring-only. **All verdicts below are playbook-only and should be logged for future calibration.** Outcome data cannot override hard rules.

---

## Verdict Summary

| Ticker | Trigger / Setup | Verdict | Confidence | Risk | First Action |
|---|---|---|---|---|---|
| **BILL** | A2 / EP_ACTIVE / today_open | **PROMOTE FULL** ($1,000) | high | $1,000 | BUY-STOP 234 sh @ $43.31 limit $43.45 DAY; OCO sell-stop $39.03 GTC; tier 1/3 @$48 / 1/3 @$52 / trail to $56.31. |
| **CALY** | B+ C1 / EP_ACTIVE / monitor | **DEFER → Day-2 alert** | medium | $0 today | Alerts: $17.74 break / $16.80 pullback / $15.77 kill. Promote only if trigger fires AND R:R recomputes ≥2.0. |
| **DBX** | B+ C1 / EP_ACTIVE / monitor | **CANCEL** | high | $0 | Remove from screen. NI -24% YoY + R:R 1.24 vs 52w cap = unfixable. |
| **CVSA** | B+ C1 / ACTIVE_BURST / monitor | **DEFER → Day-2 alert** | medium | $0 today | Alerts: $133.79 break / $130 pullback / $121.40 kill. Closest path to 2.0R via Day-2 stop tighten. |
| **CBL** | B+ C1 / ACTIVE_BURST / monitor | **DEFER → Day-2 alert (low priority)** | low-medium | $0 today | Alerts: $47.99 break / $47.00 pullback / $44.82 kill. Low ADR caps target. |
| **TXRH** | B+ C1 / EP_ACTIVE / monitor (V5.8.7 resurrection) | **CANCEL** | high | $0 | Remove from screen. Resurrection + stacked warnings + close_pct 51% barely + R:R 1.29. |

**Net:** 1 PROMOTE today (BILL full $1,000 risk). 3 DEFER as Day-2 alerts (CVSA, CALY, CBL ranked by R:R-proximity then catalyst grade). 2 CANCEL (DBX, TXRH).

---

## Convergent themes across the batch

- **The 2.0R floor is the binding edge** and it is non-negotiable — five candidates failed it for five different reasons (range width, 52w cap, low ADR, resurrection stack), and four of five advisors agreed catalyst grade does not buy R:R relief.
- **BILL is the only A2** — it competes with cash, not with the B+ five. The five compete for a slot that does not exist under the user's own rules until Day-2 promotion math fires.
- **Empty book + Risk-On 10/10 ≠ obligation to deploy.** Regime quality amplifies setups that already pass; it does not manufacture them. Cash is a position.
- **TXRH resurrection is the loudest tell** — a row excluded for 4 warnings then lifted to advisory because the catalyst was strong is exactly the rule-bending pattern n=20 cohort calibration will flag as a leak.
- **DBX is unanimous CANCEL** — flat YoY revenue with raised guide masks NI -24%; B-grade catalyst with the worst R:R in the cohort vs a hard 52w cap.

---

## Anonymization mapping (for reference)

For peer review, advisor responses were anonymized as:
- **A** = The Expansionist
- **B** = The Contrarian
- **C** = The Executor
- **D** = The First Principles Thinker
- **E** = The Outsider

---

## Calibration Log Rows (csv preview — see council_outcomes_2026-05-09.csv for canonical artifact)

```
signal_date,ticker,bplus_reason,council_verdict,confidence,base_rate_used,base_rate_sample_size,decision_reason
2026-05-08,BILL,N/A_A2_today_open,PROMOTE_FULL,high,playbook_only,IMMATURE_20D,A2_all_gates_clean_RR_3.05_multi-catalyst_4of5_PROMOTE
2026-05-08,CALY,C1_wide_day1_range,DEFER_DAY2_ALERT,medium,playbook_only,IMMATURE_20D,Agrade_no_52w_cap_promote_only_on_RR>=2.0_recompute
2026-05-08,DBX,C1_worst_RR_52w_cap,CANCEL,high,playbook_only,IMMATURE_20D,unanimous_NI-24pct_flat_YoY_RR1.24_unfixable
2026-05-08,CVSA,C1_close_pct_99.9_extension,DEFER_DAY2_ALERT,medium,playbook_only,IMMATURE_20D,closest_to_2R_Bgrade_education_training
2026-05-08,CBL,C1_low_ADR_2.56_caps_target,DEFER_DAY2_ALERT_LOW_PRIORITY,low-medium,playbook_only,IMMATURE_20D,Agrade_REIT_but_velocity_capped_ATH_overhead
2026-05-08,TXRH,C1_resurrection_stacked_warnings,CANCEL,high,playbook_only,IMMATURE_20D,V5.8.7_resurrection_close_pct_51_barely_RR1.29_honor_filter
```

---

## Chairman's Verdict

### Outcome / Base-Rate Context

Outcome data is IMMATURE — playbook-only verdicts. Cohort age -2; no T+5 maturity; ACTIVE_BURST × catalyst-A intersection n=2 (too small). Per the skill rules and the immediately prior 2026-05-08 batch, the n=83 ACTIVE_BURST T+1 prior (49.3% win, -0.72% avg) is monitoring-only. Three peer reviewers explicitly flagged that the Contrarian's reliance on that prior was overfitting backward — IMMATURE_20D means the prior is symmetric noise relative to the playbook, so it does not earn weight in the verdict either way. Verdicts below are playbook-only and must be logged for future calibration.

### Where the Council Agrees

- **BILL is a real trade** — 4 of 5 advisors call PROMOTE; only the Contrarian dissents (and even there, half-size, not pass).
- **DBX is dead** — 5 of 5 CANCEL. NI -24% YoY on raised guide is exactly the trap; R:R 1.24 vs 52w cap is unfixable in any plausible Day-2 geometry.
- **TXRH should be removed from the channel** — 4 of 5 CANCEL. The V5.8.7 resurrection is the calibration leak the skill exists to prevent. Honor the filter.
- **CVSA and CBL are unanimously DEFER** — math is closest to 2.0R but Day-1 geometry (close_pct 99.9% on CVSA; low ADR 2.56% on CBL) prevents in-session promotion.
- **The 2.0R floor is non-negotiable** — catalyst grade does not buy R:R relief. Five independent failure modes converging on one floor means the floor is doing its job.

### Where the Council Clashes

- **BILL full vs half:** The Contrarian read close_pct 66.4% as distribution flavor on Day-2 chase into a 52w-high target and called for half size. The other four call full. **Resolution:** close_pct 66.4% passes Gate 4 cleanly; mid-upper close after a +11% gap-and-run is consistent with continuation, not distribution. The R:R 3.05R + multi-catalyst stack (capital return + restructuring) earns full size per playbook. Contrarian's caution was warranted but already priced into the playbook's gate structure.
- **CALY PROMOTE vs CANCEL vs DEFER:** Expansionist alone calls PROMOTE, citing no-52w-cap base breakout and right-tail upside. Contrarian alone calls CANCEL, citing extended dist_21ema 16.93% and exhausted Day-1 buyers at close_pct 91.1%. The three centrists DEFER. **Resolution:** the same playbook that gates CALY into B+ (R:R floor fail) also defines the promotion mechanism (Day-2 trigger + recomputed R:R ≥2.0). DEFER respects both rules. Expansionist's "right tail understates target" is exactly the narrative override the floor exists to block — flagged by all 5 peer reviewers.
- **TXRH PROMOTE vs CANCEL:** Expansionist alone PROMOTE on comp +7.1% / traffic +4.5%. Four CANCEL. **Resolution:** CANCEL wins. The resurrection mechanism + close_pct 51% barely + worst R:R 1.29 + B-grade with rev miss is the exact rule-stacking pattern that gets flagged as a leak when n matures. Strong comps do not earn override.

### Blind Spots the Council Caught

- **Expansionist used "right-tail understates target" twice to override the hard 2.0R rule** — flagged by all 5 peer reviewers. This is catalyst-grade laundering math; the rule exists precisely to prevent narrative overrides.
- **Contrarian over-leaned on the n=83 ACTIVE_BURST T+1 cohort prior (49.3% win, -0.72% avg)** as if mature — flagged by 3 reviewers. IMMATURE_20D means that number is also symmetric noise; using it to cancel BILL is the inverse error of using regime to promote.
- **No advisor stress-tested BILL's Monday gap-up risk** — BUY-STOP $43.31 may itself break the 2.0R math if Monday gaps and the trigger fills materially above target arithmetic. Mitigated by the SPY-gap kill rule and the limit cap at $43.45, but worth flagging.
- **Sector/correlation risk** across the basket (CALY, DBX tech-adjacent; CVSA education; CBL REIT) — clustered post-earnings vol expansion is one factor, not six independent signals.
- **No "what if BILL stops out" rule for Tuesday's monitor list** — does a BILL loss void or reweight CVSA / CALY / CBL alerts? Worth pre-committing in the journal.
- **No paper-track plan to log these six for the n=20 maturation feedback loop** — the entire point of council_outcomes CSV.
- **Day-3 chase risk** — if 5 deferrals all spike Day-2 cleanly and the user has only allocated 1% to BILL, there is a real risk of forcing in on Day-3 at worse R:R. The deferral plan needs a hard cap on how many alerts can convert.

### Recommendation

**1 PROMOTE today, 3 DEFER as Day-2 alerts (capped at 1 conversion), 2 CANCEL.** Verdicts are playbook-only; outcome cohorts are immature.

- **BILL — PROMOTE FULL** ($1,000 risk; 234 sh × $43.30 ≈ $10,131). Confidence: high. Playbook-only.
- **CALY — DEFER → Day-2 alert.** Confidence: medium. Playbook-only. Promote next session only on (1) trigger fires AND (2) R:R recomputes ≥2.0 AND (3) DTE re-verified.
- **DBX — CANCEL.** Confidence: high. Playbook-only.
- **CVSA — DEFER → Day-2 alert.** Confidence: medium. Playbook-only. Same promotion gate as CALY.
- **CBL — DEFER → Day-2 alert (low priority).** Confidence: low-medium. Playbook-only. Velocity-capped — even on promotion, target may take weeks.
- **TXRH — CANCEL.** Confidence: high. Playbook-only.

**Hard cap on Day-2 conversions: at most 1 of the 3 alerts gets converted to a trade Tuesday, regardless of how many trigger.** Pick the one with highest recomputed R:R; if two tie, prefer A-grade catalyst (CALY > CBL > CVSA).

### The One Thing to Do First

Place the BILL BUY-STOP **234 sh @ $43.31, DAY, limit $43.45**, with OCO sell-stop **$39.03 GTC**, before market open Monday. Pre-set tier-out (1/3 @$48, 1/3 @$52, trail rest toward $56.31). Set 3 alert triplets (CVSA $133.79/$130/$121.40 · CALY $17.74/$16.80/$15.77 · CBL $47.99/$47/$44.82). Remove DBX and TXRH from the screen now. Pre-commit the kill rule in the journal: "If SPY gaps <-0.8% pre-open OR BILL prints below pause_high $40.41 before 9:35, cancel BILL ticket. If BILL stops out Monday, all Day-2 alerts auto-void for Tuesday."

---

## Per-Advisor Snapshots

- **The Contrarian (Response B):** 0 promotes today. BILL DEFER (mid-range close = distribution flavor; 3.05R is arithmetic not achievable). CALY/DBX/TXRH CANCEL. CVSA/CBL DEFER. Cash is a position.
- **The First Principles Thinker (Response D):** PROMOTE BILL full; DEFER CALY/CVSA/CBL; CANCEL DBX/TXRH. Five failure modes converging on one floor = the floor is doing its job. (Picked strongest by 5/5 peer reviewers.)
- **The Expansionist (Response A):** PROMOTE BILL/CALY/TXRH full; DEFER CVSA/CBL; CANCEL DBX. 3% portfolio risk; cash is the actual risk. (Flagged blind-spot by 5/5 peer reviewers — used "right-tail" narrative to override hard 2.0R rule.)
- **The Outsider (Response E):** PROMOTE BILL; DEFER CALY/CVSA/CBL; CANCEL DBX/TXRH. One clean A2 = a great day. Resurrection itself is the reason to skip TXRH.
- **The Executor (Response C):** PROMOTE BILL with full pre-market ticket; DEFER CALY/CVSA/CBL as alerts only; CANCEL DBX/TXRH. Attention budget = 3 alerts + BILL. Walk away after fill.

---

## Full Advisor Responses

### The Contrarian (Response B)

Playbook-only. Outcomes are IMMATURE_20D and cannot justify any rule break.

The prior cohort tape is ugly: ACTIVE_BURST n=83 printed 49.3% T+1 with avg -0.72%. That is a coin flip with negative expectancy. You are about to deploy into a regime where the most relevant base rate is bleeding. Risk-On 10/10 does not repeal that. Now the names:

**BILL — DEFER (medium-high, playbook-only).** Stop calling this clean. close_pct 66.4% is mid-range, not a Day-2 gap-and-go closer; vol 3.57x with a mid-range close is distribution flavor, not demand. dist_21ema 8.42% is "passes" but stacked on a Day-2 chase into a 52w-high target. The 3.05R is arithmetic, not achievable — the target is the prior high and the path goes through every trapped seller from the last leg. Half size at most; my vote is wait for the inside day. Full-size here is the trade you regret on Monday.

**CALY — CANCEL (high, playbook-only).** 1.65R fails C1. dist_21ema 16.93% is extended. close_pct 91.1% on Day-1 is the worst entry geometry for Day-2 continuation — buyers are exhausted. A-catalyst does not buy you R:R relief.

**DBX — CANCEL (high, playbook-only).** NI down 24% YoY is not a B+ catalyst, it is an accounting mirage with a raised guide on top. 1.24R is structurally un-fixable against a 52w cap. Should not be in the channel.

**CVSA — DEFER (medium, playbook-only).** close_pct 99.9% is a red flag, not a feature — that is the literal high tick, the worst possible Day-2 entry. Vol 1.80x is barely qualifying. Closest-to-2R does not mean good; it means least-bad.

**CBL — DEFER (medium, playbook-only).** Cleanest gates, but adr_20 of 2.56% means the move is structurally capped before it starts. ATH overhead + low ADR = the target won't print in your timeframe.

**TXRH — CANCEL (high, playbook-only).** Resurrection + C1 fail + close_pct 51.0% (barely Gate 4) + fresh 21EMA reclaim + 1.29R. Five yellow flags stacked. V5.8.7 lifted it to advisory; advisory is not "trade it." Kill it.

**Net: 0 promotes today.** The honest answer is the queue is weak; the user is shopping because Risk-On 10/10 feels like obligation. It isn't. Cash is a position. Re-rack tomorrow on inside-day setups for BILL/CVSA/CBL.

### The First Principles Thinker (Response D)

The wrong question is being asked. The user frames this as "where is my edge among 6 candidates?" That's a selection problem. But the actual problem is structural: **you have a hard rule (R:R ≥ 2.0) and five candidates that fail it for five different reasons.** When five independent failure modes converge on one floor, the floor is doing its job. Stop trying to negotiate with it.

The real question is: "Do I have one trade or zero trades tonight?" Not six. The B+ basket is a distraction generated by an empty book and a 10/10 regime making you itch. Regime quality does not manufacture setups; it amplifies the ones that already pass. An empty book in Risk-On is not a problem to solve — it is a neutral state. Forcing it is how 1.0% risk becomes 5.0% risk in flawed names.

Second reframe: BILL isn't competing with the B+ five. BILL is competing with cash. The B+ five are competing with each other for a slot that doesn't exist under your own rules.

Third: TXRH is a "V5.8.7 RESURRECTION" with close_pct 51% barely passing Gate 4. A resurrection mechanic that lifts a 4-warning name into advisory is the kind of rule-bending that, in aggregate, is exactly what cohort calibration will later flag as your leak. Treat resurrections as suspect by default.

**Verdicts (playbook-only — outcomes IMMATURE_20D, monitoring only):**

1. BILL — PROMOTE, full $1K risk. High confidence. Playbook-only. A2, today_open, all gates clean, R:R 3.05, multi-catalyst with structural (buyback + restructuring) not just earnings. This is what the playbook is built for.
2. CALY — DEFER. Med-high. Playbook-only. C1 fails; pullback $16.50-$16.80 plan is correct — wait for the trigger that fixes R:R, don't relax R:R.
3. DBX — CANCEL. High. Playbook-only. NI -24% YoY on a "beat" is a quality flag, R:R 1.24 is the worst of the set, and "raised guide" with falling earnings is exactly the trap. Drop it.
4. CVSA — DEFER. Medium. Playbook-only. Closest to 2.0 R:R, close_pct 99.9% is extension risk. Watch for inside-day or shallow pullback.
5. CBL — DEFER. Medium. Playbook-only. Cleanest Gate 6 but ADR 2.56% structurally caps upside; needs a different target construction, not a different decision.
6. TXRH — CANCEL. High. Playbook-only. Resurrection + barely-passing Gate 4 + worst-tier R:R 1.29. The mechanism that put it on the list is the reason to remove it.

**One trade tonight: BILL. Cash on the other five is the edge.**

### The Expansionist (Response A)

The asymmetry everyone's missing: this is a 10/10 Risk-On regime with an EMPTY BOOK and multiple A-grade capital-return catalysts on the same day. That's a coincidence the council is treating as ordinary. It isn't.

**BILL — PROMOTE, high conviction (playbook-only).** The $1B buyback on a $4-5B cap is a 20%+ float reduction signaling floor — that's not a normal EP catalyst, that's a structural re-rate fuel. 30% AI restructuring means margin expansion the street hasn't modeled. R:R 3.05 is the headline, but the under-modeled scenario is BILL piercing 52w-high and trending — buybacks chase strength, AI re-rates compound. The 52w-high target caps your imagination, not the stock. Today_open + clean trigger + uncapped upside vector = take it full size.

**CALY — PROMOTE, high conviction (playbook-only).** This is the most underweighted name on the sheet. No 52w cap, fresh base breakout, close_pct 91.1%, raised guide, EBITDA +40%. The target ($21) is lazy — round-number anchoring. Base breakouts with A-grade earnings and golf/leisure tailwind don't stop at 2x ADR; they trend. R:R 1.65 understates the right tail by an order of magnitude. The "small target" is the opportunity.

**TXRH — PROMOTE, medium-high (playbook-only).** Comp +7.1% / traffic +4.5% is the rarest print in consumer discretionary right now — actual unit economics, not financial engineering. Resurrection flag is noise; the tape is signal. 52w-high target is conservative; consumer names with this comp profile run multiples past prior highs. Fresh 21EMA reclaim = early innings.

**CBL — DEFER, medium (playbook-only).** +130% NI and 39% div hike is genuinely A-grade, but low ADR 2.56% structurally caps velocity. Right thesis, wrong vehicle for an Expansionist book in 10/10 regime. Hold for pullback entry only.

**CVSA — DEFER, medium (playbook-only).** close_pct 99.9% is extension, not strength, into a capped target. Wait for Day-2 continuation or stand aside.

**DBX — CANCEL, high (playbook-only).** Flat revenue, NI -24%, R:R 1.24. B-grade catalyst masquerading as EP_ACTIVE. In a 10/10 regime with BILL/CALY/TXRH on the table, DBX is opportunity-cost theft. Kill it.

**Sizing posture:** Empty book + 10/10 regime + three A-grade vectors = deploy 3 positions full-size ($1K risk each = 3% portfolio risk). Holding cash here is the actual risk no one is pricing.

### The Outsider (Response E)

The thing nobody in this room is saying out loud: you have one trade. It's BILL. Everything else is a story about why almost-qualifying trades might qualify tomorrow.

Five of your six candidates failed the same gate — the 2.0R floor — for the same reason: Day-1 ranges were too wide. That's not six independent signals. That's one market condition (volatility expanded after earnings season) producing five identical near-misses. Treating them as a "watchlist of six" makes you feel busy. It's noise dressed as focus.

On the core question — should you ever take a sub-2R trade because the catalyst is pretty? No. The 2.0R rule isn't a suggestion you negotiate with when fundamentals look juicy; it's the thing that makes the math work over n=83+ trades where you're winning 49%. At 49% win rate and 1.65R, you're roughly breakeven before fees. At 1.24R you're bleeding. The catalyst grade doesn't change the arithmetic.

The "resurrection" of TXRH is the loudest tell. A row got rejected for four warnings, then un-rejected because someone liked the story. That's the system serving the trader's want-to-trade, not the other way around. If your playbook has a backdoor labeled "but the catalyst was strong," the playbook has a hole.

Empty book + 10/10 risk-on doesn't mean "deploy." It means the filter did its job yesterday. One clean A2 today is a great day.

**Verdicts (playbook-only, IMMATURE_20D):**

1. BILL — PROMOTE, high confidence. Passes every gate. 3.05R, real catalyst (beat + guide + buyback + restructuring), volume confirms. This is the trade.
2. CALY — DEFER, medium. Strongest B+ catalyst of the bunch. Day-2 plan is legitimate; tighter stop tomorrow could make 2R.
3. DBX — CANCEL, high. Flat YoY revenue and net income down 24% is not a breakout catalyst, it's a relief bounce. Worst R:R. Stop looking at it.
4. CVSA — DEFER, low. Closest to 2R, but catalyst is mid (B-grade, single-digit rev growth). Only revisit if range tightens hard tomorrow.
5. CBL — DEFER, medium. Best fundamentals of the B+ group, but 2.56% ADR means the target is weeks away. Wrong vehicle for a swing thesis.
6. TXRH — CANCEL, high. The resurrection itself is the reason to skip. Honor your own filters or stop having them.

Take BILL. Watch CALY tomorrow. Close the other four tabs.

### The Executor (Response C)

**MONDAY PRE-MARKET TICKET — single page, 6 names**

**1) BILL — PROMOTE. Confidence: High. Playbook-only.** Only A2.
- Order: BUY-STOP 234 sh @ $43.31, DAY, limit $43.45 (slippage cap).
- Hard stop (OCO bracket): SELL-STOP $39.03 GTC.
- Target tier-out: 1/3 @ $48.00, 1/3 @ $52.00, trail rest toward $56.31.
- Kill before fill: cancel if SPY gaps <-0.8% pre-open OR BILL prints below $40.41 (pause_high) before 9:35.
- Risk: $1,000. Full size.

**2-6) ALL B+ C1s — DEFER. No live orders. Alerts only.** Cannot promote in-session. Trigger + recomputed R:R ≥ 2.0 required next session. Attention budget: 3 alerts max + BILL.

- **CVSA — ALERT. Med, playbook-only.** Closest R:R (1.67) + close_pct 99.9%. Alerts: $133.79 break / $130 pullback / $121.40 kill.
- **CALY — ALERT. Med, playbook-only.** A-grade, R:R 1.65, vol 3.18x. Alerts: $17.74 break / $16.80 pullback / $15.77 kill.
- **CBL — ALERT. Low-Med, playbook-only.** A-grade REIT only reason it stays. Alerts: $47.99 break / $47.00 pullback / $44.82 kill.

**CANCELS — remove from screen now:**
- DBX — CANCEL. High. Worst R:R 1.24, B-grade with NI -24%. Math doesn't get to 2.0 cleanly. Dead.
- TXRH — CANCEL. High. close_pct 51% barely, R:R 1.29, B-grade, V5.8.7 resurrection adds noise. Dead.

**"If only X happens" rules:**
- If BILL fills and trades to +1R before 10:30 → do nothing else, no new tickets today.
- If BILL stops out → close laptop until 12:00, no revenge entries on B+s.
- If 2+ B+ alerts trigger same minute → take the one with higher recomputed R:R, ignore the other.
- If SPY < -1% intraday → all B+ alerts auto-void.
- No discretionary entries. No "feels strong." Ticket or nothing.

**Deployed Monday: $10,131 / $100K. Risk live: $1,000 / $1,000 budget. One trade. Walk away.**

---

## Peer Review Highlights

All 5 reviewers independently picked **Response D (First Principles)** as strongest, citing the reframe from "select among six" to "one trade or zero," and the diagnosis that five independent failure modes converging on one floor means the floor is working.

All 5 reviewers independently flagged **Response A (Expansionist)** as the biggest blind spot. Recurring critique: "right-tail understates target" is exactly the narrative override the 2.0R floor exists to prevent. The 3-position full-size deployment ignores IMMATURE_20D and conflates regime quality with validated edge.

3 of 5 reviewers flagged **Response B (Contrarian)** for over-leaning on the n=83 ACTIVE_BURST 49.3% / -0.72% prior cohort tape — the prompt specified IMMATURE_20D, so that prior is symmetric noise; using it directionally to cancel BILL is the inverse error of using regime to promote it.

Things ALL five advisors missed (per peer review):
1. Sector / correlation concentration across the basket — clustered post-earnings vol expansion is one factor, not six independent signals.
2. Execution-path risk on BILL itself — Day-1 A2 today_open into a Monday gap with no SPY-overnight stress test beyond the Executor's brief mention.
3. "If BILL stops out" rule for Tuesday — does a BILL loss void or reweight CVSA / CALY / CBL alerts?
4. Day-3 chase risk if 5 deferrals all spike Day-2 — the deferral plan needs a hard cap on conversions.
5. Paper-track logging plan to feed these six into n=20 maturation feedback (the council_outcomes CSV exists, but no advisor named it as the artifact).
6. Half-size BILL pending cohort maturation as an explicit middle path — none of the five PROMOTE-BILL advisors considered it.

---

## Files written this session

- `council-report-20260509-batch.html`
- `council-transcript-20260509-batch.md`
- `council_outcomes_2026-05-09.csv`

All under `/home/user/bonde/.claude/skills/llm-council/reports/`.
