# LLM Council — Pre-Open Batch (6 tickers) — 2026-05-08

**Signal date:** 2026-05-06 (cohort end 2026-05-10).
**Account:** $100K · 1% risk per position · 0 positions held · Regime Risk-On 10/10 (Normal sizing).
**Outcome / base-rate context:** Cohort age -3 days. All cohorts PARTIAL_OUTCOME / IMMATURE_20D. ACTIVE_BURST n=83, T+1d win 49.3%, avg -0.72%. Catalyst-grade-A intersections n=2 (too small). WATCH_ONLY × B n=17 (T+1d -0.73%, win 45.5%); WATCH_ONLY × C n=28 (-3.33%, 40%); REJECT × D n=36 (+1.49%, 58.8%). Per skill rules: outcome data is monitoring-only. **All verdicts below are playbook-only and should be logged for future calibration.**

---

## Verdict Summary

| Ticker | Trigger / Setup | Verdict | Confidence | Risk | First action |
|---|---|---|---|---|---|
| **IBEX** | A2 / EP_ACTIVE / today_open | **HALF** ($500) | medium | $500 | Buy-stop limit $33.58 (limit $33.75), 118 sh, GTC stop $29.37. Cancel if no trigger by 11:00 ET on weak vol. |
| **ORA** | A2 / EP_ACTIVE / today_open | **HALF** ($500) | 65% | $500 | Stop-buy $127.23 (limit), 62 sh, stop $119.28. Re-eval sizing only on upper-40% close. |
| **SNEX** | B+ Day-2 council / ACTIVE_BURST / monitor | **PROMOTE-on-trigger** (full size on clean A2) | medium-high | $1,000 IF triggered | Set hard alerts $124.20 (trigger) + $117.99 (kill). Pre-stage ticket. |
| **LAMR** | B+ Day-2 council / ACTIVE_BURST / monitor | **DEFER → PROMOTE-half** on confirmation | 55% | $500 IF confirmed | Pull IYR/VNQ vs SPY 5-day + macro/rate calendar before any size. |
| **XPER** | B+ Day-2 council / ACTIVE_BURST / monitor (thin) | **DEFER → conditional PROMOTE-half** | 55% | $500 (hard cap regardless of A2) | Re-verify DTE + check live bid/ask spread + L2 depth at $7.93 before placing limit. |
| **APP** | CONFLICT_A,D / ACTIVE_BURST / today_intraday | **DEFER-FOR-CONFIRMATION → OVERRIDE-HALF conditional** | 6/10 | 0.5% (HALF A2) IF confirmed | Write the override condition in the journal *tonight*: $498.87 close + 1.5x vol + hold $483.55, stop $483.55, half size. If you can't pre-commit in writing, don't take it. |

**Convergent themes across the 6 sessions:**
- No advisor in any session supported FULL size today. Half / defer / skip dominated everywhere.
- Trigger discipline is the binding edge: every council resolved on "no trigger, no trade." Empty book + Risk-On 10/10 is not a reason to deploy.
- Immature outcome data (cohort age -3) means none of these verdicts are evidence-backed. Log every one for T+5/T+20 calibration when cohort matures.
- Conflicts ranked by severity (highest = most caution): APP (two-flag fundamental rejection) > LAMR (kiss-the-high + REIT macro) > XPER (thin liquidity + missing RS) > SNEX (late-stage extension) > IBEX (composite-below-band + R:R-at-floor) > ORA (mid-range close).

---

## Calibration Log Rows (csv)

```
signal_date,ticker,bplus_reason,council_verdict,confidence,base_rate_used,base_rate_sample_size,decision_reason
2026-05-06,IBEX,N/A_A2_at_floor,HALF,medium,playbook_only,2_immature_monitoring_only,composite_3.75_below_A2_band_plus_RR_exactly_at_2.0_floor_offset_by_grade_A_catalyst_and_clean_structure_rank_11_TAKE
2026-05-06,ORA,N/A_A2_cpr_mid_range,HALF,65,playbook_only,0,cpr_40.8_below_strong_close_band_and_ep_spike_nonfire_offset_grade_A_catalyst_and_clean_gates
2026-05-06,SNEX,C3+C1_wide_day1_range,PROMOTE-on-trigger,medium-high,ACTIVE_BURST_family_T+1_playbook-only,83,V5.9.3_inside_day_plan_resolves_C1_via_tighter_stop_extension_moderate_soft_demote_only_full_size_on_clean_A2_promotion
2026-05-06,LAMR,C3_kiss_the_high_consec_up_2,DEFER_PROMOTE_ON_TRIGGER,55,ACTIVE_BURST_T+1d_win_49.3%_avg_-0.72%,83,playbook_only_cpr_96.6_no_margin_wait_Day2_hold_above_151.36_then_half_size
2026-05-06,XPER,C3+C1_thin_liquidity_data_gap,DEFER_conditional_PROMOTE_half,55,ACTIVE_BURST_T1d_playbook_only,83,Late-stage_continuation_bars26_rs3m_missing_thin_liq_2.6M_half_cap_mandatory_catalyst_B_subset_n8_too_small_defer_to_live_trigger_with_spread_volume_gates
2026-05-06,APP,CONFLICT_A_D_QG_FAIL+SPEC_TRUE,DEFER-FOR-CONFIRMATION->OVERRIDE-HALF-CONDITIONAL,6,ACTIVE_BURST x WATCH_ONLY x B (T+1d -0.73% win 45.5%) + ACTIVE_BURST x catalyst-A (avg -5.17%),17_primary_2_catalyst_A_83_cohort,Gates_clean_and_catalyst_stack_strong_but_two-flag_fundamental_rejection_QG_False+spec_True_is_exactly_what_WATCH_tier_was_designed_for_consec_up_1_and_gap-down-ramp_structure_argue_for_confirmation_bar_before_any_override_half_size_only_if_confirmed
```

---

## Per-Ticker Sessions

The full chairman synthesis (agreement, clashes, blind spots, recommendation, advisor snapshots, full advisor responses, peer review highlights) for each ticker is preserved in this transcript below.

---

## 1) IBEX — A2 / EP_ACTIVE / today_open

**Verdict: HALF ($500), confidence MEDIUM, playbook-only.**

### Outcome/Base-Rate Context
Outcome data is IMMATURE — playbook-only verdict. Cohort age -3, no T+5 maturity. EP_ACTIVE family n=64 immature. ACTIVE_BURST × catalyst-A is n=2 (1 evaluable at -10.48% 1d) — too small to act on; monitoring-only.

### Where the Council Agrees
- This is a **valid trade**, not a PASS. Gates clean, hard rules clear, catalyst real (3rd raise, AI/Sierra partnership).
- **R:R at exactly 2.00R is the binding constraint.** No cushion = any slippage at trigger or stop drift kills the math.
- **Composite 3.75 < 5 A2 conviction band** is a real demerit.
- Rank 11 = a TAKE, not a FEATURED. Sizing should reflect that.
- dist_21ema 14.5% + consec_up=1 + bars_since_10ema_break=1 = early in the move — the one structural gift.

### Where the Council Clashes
- HALF vs PASS: Contrarian/Outsider lean PASS — at-floor R:R + sub-band composite + n=2 negative cohort whisper. First Principles, Expansionist, Executor land HALF.
- Catalyst weight: Expansionist treats grade-A as composite override. Contrarian: catalyst is already priced into the 16.54% gap.
- Trigger discipline: First Principles flags that the trigger itself is the test — clean break on volume is required for the 2.00R math to hold.

### Blind Spots Caught
- Gap-fill risk: 9.07% ep_gap with cpr 0.804 means a half-fill takes price under stop.
- Pre-trigger liquidity at $33.58 unmodeled; mb_vol_ratio_50 1.85x is post-earnings volume.
- 252d-high target ($42) is a magnet *and* a wall — realized R:R on prior-high targets historically clips at 1.6–1.8R, pushing effective R:R below floor.
- Composite 3.75 is the system telling you the conviction stack isn't there — catalyst is doing all the lifting alone.

### Recommendation
**HALF ($500 risk), MEDIUM confidence, playbook-only.** Two governors flashing (composite 3.75 < band; R:R exactly at 2.00R floor) typically resolve as HALF or skip — never FULL. Catalyst grade A keeps it from PASS but does not earn FULL. Realized targets at prior 252d highs historically clip at 1.6–1.8R → expected R:R is functionally sub-floor → half is the honest expression.

### One Thing to Do First
Place a buy-stop limit at $33.58 (limit $33.75) for HALF size = 118 shares ($500 risk to $29.37 stop), GTC. No market orders. If trigger doesn't fire on >1.5x avg volume in the first 90 minutes, cancel. No chase intraday.

### Advisor Snapshots
- **Contrarian:** Leans PASS. R:R at floor + composite below band + 9.07% ep_gap = priced-in news with no margin. n=2 cohort whisper at -10.48% is uncomfortable. HALF maximum if forced.
- **First Principles:** HALF. One clean (catalyst), one borderline (R:R), one sub-band (composite). Two-of-three at-floor-or-below = half-conviction expression.
- **Expansionist:** HALF leaning FULL. 3rd consecutive beat-raise + Sierra/AI is multi-quarter re-rating. Composite undervalues qualitative catalyst depth.
- **Outsider:** Skeptical, leans PASS or HALF. Rank 11 + composite below band + R:R at floor = the system is hedging. You should too.
- **Executor:** HALF. Buy-stop limit $33.58/$33.75, 118 sh, $500 risk. Trail to BE at +1R. Cancel if no trigger by 11:00 ET on weak volume.

### Peer Review Highlights
- Contrarian → Expansionist: "Dashboard already saw the catalyst and still scored 3.75 — catalyst isn't undervalued, it's *priced*."
- First Principles → Contrarian: "PASS overweights the floor as a binary. Floor-with-catalyst is a real edge category historically; the answer is small, not zero."
- Outsider caught the ordinal-rank blind spot: nobody initially asked *why rank 11 and not rank 1*.
- Surfaced in peer review: realized R:R on prior-252d-high targets historically clips at 1.6–1.8R → "exactly at floor" is functionally sub-floor in expectation.
- Convergence under pressure: Even Expansionist conceded HALF as floor; even Contrarian conceded HALF over PASS. HALF survived all five cross-examinations.

---

## 2) ORA — A2 / EP_ACTIVE / today_open

**Verdict: HALF ($500), confidence 65%, playbook-only.**

### Outcome/Base-Rate Context
Cohort age T-3, no T+5 maturity. EP_ACTIVE family n=64 immature. ACTIVE_BURST × A: n=2, -10.48% 1d (too small to weight). Monitoring-only. Hard rules clear.

### Where the Council Agrees
- Catalyst is exceptional: rev +75.8% YoY, EPS +42.9% beat, Energy Storage +153%, FY26 guide reiterated. Grade A, conf 90 is real.
- All gates PASS, ext_run False, consec_up 1, dist_21ema 7.6% — structurally not extended.
- R:R 2.24 is above floor but not generous; $7.94 risk window is tight relative to $127.22 trigger.
- cpr=0.408 is the single real blemish — above 30% floor, well below 60% strong-close band.
- Trigger discipline matters more than sizing: no fill above $127.22 = no trade.

### Where the Council Clashes
- **FULL camp (Expansionist, Executor):** Strongest catalyst of the day, clean gates, Risk-On 10/10, Tier=TAKE rank 10, composite 6.0, QG=True, 0 positions. Half-sizing the best A-grade setup of the day under 10/10 regime is leaving edge on the table.
- **HALF camp (Contrarian, First Principles):** cpr 40.8% means sellers active into the close. EP_SPIKE did NOT fire on a grade-A blowout — that's information. R:R 2.24 has only 0.24R cushion. funds_pct 54 / rs_3month 64 are middling.
- **PASS camp (Outsider):** Mid-range close after a 75% revenue beat is suspicious. n=2 cohort at -10.48% is the only outcome data, and it's negative.

### Blind Spots Caught
- EP_SPIKE non-fire on a grade-A blowout is a yellow flag the gate sheet alone obscures.
- 2.24R is computed to a +13.5% target ATH; if target trims to realistic +10%, effective R:R drops to ~1.6R.
- ACTIVE_BURST × A cohort n=2 at -10.48% is monitoring-only but directionally cautionary.
- 0 positions + Risk-On 10/10 creates pressure to deploy. Don't let empty-book bias push to FULL.
- Next earnings ~Aug-2026: 3+ months runway, no near-term catalyst risk — supports holding once filled.

### Recommendation
**HALF ($500), 65% confidence, playbook-only.** Catalyst and gates justify participation; mid-range cpr (40.8%), EP_SPIKE non-fire, and 0.24R cushion argue against full size. Half preserves edge on the highest-grade catalyst of the day while respecting the one real soft spot. Upgrade to full only on entry day closing >60% of range.

### One Thing to Do First
Stop-buy at $127.23 for HALF size (62 shares, $500 risk to $119.28 stop). No discretionary chase. Re-evaluate sizing only if entry day closes in upper 40% of range.

### Advisor Snapshots
- **A Contrarian:** HALF — cpr 40.8% + EP_SPIKE non-fire = sellers showed up; don't full-size into ambiguity.
- **B First Principles:** HALF — 2.24R is operationally thin; size to the weakest signal, not the strongest.
- **C Expansionist:** FULL — best catalyst of the day, Risk-On 10/10, clean gates, 0 positions; this is what FULL is for.
- **D Outsider:** PASS or HALF — mid-range close on a 75% rev beat is a tell; market is unimpressed.
- **E Executor:** HALF on trigger, mechanical add-on rule contingent on close-strength confirmation.

### Peer Review Highlights
- B (First Principles) flagged C (Expansionist) for dismissing cpr — the 60% band isn't a "bonus tier," it's the empirically-derived demand-confirmation threshold.
- C flagged A and D for over-weighting a single intraday metric against an A-grade catalyst with all structural gates clean.
- D flagged the entire council for under-weighting the n=2 at -10.48% cohort data.
- E proposed the synthesis adopted: HALF on trigger with mechanical add-on rule contingent on close-strength confirmation.
- A flagged behavioral risk: 0 positions + Risk-On 10/10 creates deployment pressure that biases toward FULL.

---

## 3) SNEX — B+ Day-2 council / ACTIVE_BURST / monitor

**Verdict: PROMOTE-on-trigger (full size on clean A2 promotion), confidence medium-high, playbook-only.**

### Outcome/Base-Rate Context
ACTIVE_BURST n=83, T+1 win 49.3%, avg -0.72%, T+5 not mature. Catalyst-A and A2-actionability sub-cells (n=2 each) are statistically meaningless and one shows -10.48% 1d. Per skill rules, monitoring-only. Verdict playbook-only.

### Where the Council Agrees
- Day-1 chase is dead. R:R=0.92R fails 2.0 floor; nobody defends Day-1 close entry.
- Quality is real: composite 7.75, RS 98, A-grade earnings (+70% rev, +54.5% EPS beat, record quarter), DTE clear, Risk-On regime.
- V5.9.3 Day-2 inside-day plan is the correct mechanical resolution to C1 — tightening to ~$118 converts 0.92R to ≥2.0R if trigger fires.
- Moderate extension is a soft demote, not a reject. Taxes size, doesn't veto.
- Half-size discretionary entry NOW (pre-trigger) is rejected by 4 of 5 advisors — C3 protocol exists to refuse anticipation.

### Where the Council Clashes
- Contrarian/Outsider: bars_since_10ema=32 + 13.64% gap on already-extended name = late-stage continuation that fades more often than runs; lean DEFER/CANCEL.
- Expansionist/Executor: RS 98 + composite 7.75 + record-quarter A catalyst is the right-tail profile of the family; the playbook's tightened stop is the asymmetry.
- First Principles splits: plan structurally sound, but only if R:R recomputes ≥2.0 AND volume confirms.
- Sizing: Executor wants full 1% on A2; Contrarian wants half-size even on clean trigger because of extension. Chairman sides with full on clean A2 — playbook already priced extension into soft demote.

### Blind Spots Caught
- "Inside day" must be a real inside day (Day-2 high < Day-1 high), not a narrow-range new-high day.
- $118 invalidation assumes Day-2 builds a base above it; if Day-2 LOD prints below $118, R:R math collapses → cancel, not adjust.
- Volume confirmation must be measured against Day-2's own pace, not Day-1's blow-off.
- DTE re-verification is not a formality — record quarters sometimes drag follow-on filings within 1-2 weeks.
- Composite 7.75 / RS 98 are lagging — they reflect the run that already happened, not independent forward edge.

### Recommendation
**PROMOTE-on-trigger.** Full 1% size IF AND ONLY IF: (1) Day-2 prints true inside day and breaks $124.19 on volume pacing ≥ Day-1's profile with a close above trigger, (2) recomputed R:R ≥ 2.0 vs ~$118 (or Day-2 LOD if higher), (3) DTE re-verifies morning-of. **DEFER** if any gate ambiguous. **CANCEL** if Day-2 closes <$118 OR no inside day OR DTE shrinks <8 days. No discretionary half-size pre-trigger. Confidence medium-high on plan, medium on trigger firing.

### One Thing to Do First
Set hard alert at $124.20 with volume condition + kill alert at $117.99. Pre-stage order ticket with stop at MAX(Day-2 LOD, $118) so R:R recompute happens automatically at trigger.

### Advisor Snapshots
- **A Contrarian:** DEFER-leaning. 32 bars off 10EMA on 13.64% gap = late-cycle; demand trigger but expect failure.
- **B First Principles:** PROMOTE-on-trigger. Plan mechanically correct; gates binary; no trigger no trade.
- **C Expansionist:** PROMOTE, full size. RS 98 + record quarter + Risk-On 10/10 is the right-tail profile.
- **D Outsider:** DEFER. Looks like late-stage breakout that prints one more day then rolls.
- **E Executor:** PROMOTE-on-trigger, full size, hard alerts, no discretion.

### Peer Review Highlights
- B and E flagged A's half-size suggestion as double-counting the extension penalty already priced into the soft demote.
- A and D flagged C's "right-tail of the family" framing as unfalsifiable selection bias — bounded by pre-registered filters, but valid critique.
- B caught a real spec hole in D's "wait for pullback" stance: C3 protocol has no pullback re-entry path — deferring means deferring to a different setup family.
- E's "true inside day" check (Day-2 high < Day-1 high) was upgraded by B into a binary gate.
- D's structural extension warning preserved as monitoring flag: if Day-3 fails to hold above trigger, exit on close regardless of stop.

---

## 4) LAMR — B+ Day-2 council / ACTIVE_BURST / monitor (REIT rate-sensitive)

**Verdict: DEFER → PROMOTE-half on confirmation, confidence 55%, playbook-only.**

### Outcome/Base-Rate Context
ACTIVE_BURST n=83 with 91.6% trigger but T+1d win 49.3% / avg -0.72% — coin-flip with negative drift. ACTIVE_BURST × grade B (n=8, 25% trigger, -0.20%) too small to weight but directionally discouraging. Monitoring-only. Hard rules clear, ext_sev moderate (not severe).

### Where the Council Agrees
- Day-1 chase at $151.36 with cpr=96.6% kiss-the-high is bad — no breathing room.
- Catalyst real (AFFO +7.5%, guide raise) but already 6.24% gapped + +7.12% extended → easy money paid out.
- consec_up=2 after +7% catalyst day with ext_run=True → Day-2 inside-day or 5/10 EMA pullback is the structurally correct entry.
- $146.60 invalidation non-negotiable; thesis dead if violated.
- Half-size discretionary "now" is NOT supported — V5.9.3 explicitly conditions partial entry on Day-2 first-hour hold.

### Where the Council Clashes
- REIT rate sensitivity: Expansionist/Outsider note REITs need dovish/neutral macro; Contrarian flags as hidden veto. No live rate-stance variable provided → monitoring item, not cancel reason.
- Promote-to-A2 vs discretionary half: First Principles/Executor say wait for full A2. Expansionist/Outsider would take a third on inside-day even pre-A2 if first hour holds. Contrarian wants nothing until Day-3 or EMA pullback.
- Catalyst grade B: 25%-triggered sub-cohort (n=8) dismissed as too small by four; Contrarian wants it weighted as soft warning anyway.

### Blind Spots Caught
- **Macro rate calendar not checked**: REIT means an FOMC, CPI, or PCE print in the holding window can override the chart.
- **Sector rotation tape**: Cancel rule mentions REIT rotation reverse but no IYR/VNQ relative-strength check encoded.
- Earnings recency vs ext_run: +7% Day-1 already priced the beat; mean-reversion odds elevated regardless of catalyst grade.
- Liquidity at the kiss: cpr=96.6% means any first-hour weakness Day-2 sees fast supply from Day-1 chasers.
- 0 positions + Risk-On 10/10 = "must deploy" bias; don't let empty book force a marginal entry.

### Recommendation
**DEFER → PROMOTE-on-trigger.** Do NOT enter Day-1. Do NOT take discretionary half-size pre-A2. If Day-2 first hour holds above $151.36 AND R:R recomputes ≥ 2.0 AND DTE re-verifies AND no wide-range red bar → take **half-size (0.5R, $500 risk)** on inside-day confirmation. Full size reserved for Day-3 continuation or 5/10 EMA pullback re-entry. Stop $146.60 hard. Cancel on Day-2 close <$146.60, >3% drop, REIT/IYR rotation reverse, or hawkish rate surprise. Confidence 55%.

### One Thing to Do First
Before market open Day-2: pull IYR/VNQ relative strength vs SPY (5-day) and check macro calendar for rate-sensitive prints (CPI, FOMC speakers, 10Y auction) inside 5-day holding window. If IYR rolling over OR hawkish-risk print in window → downgrade to skip regardless of $151.36 hold.

### Advisor Snapshots
- **Contrarian:** DEFER, lean CANCEL. cpr 96.6% + ext_run + grade-B sub-cohort = three yellow flags. Wait for Day-3 or EMA pullback.
- **First Principles:** DEFER → PROMOTE-on-A2. Protocol exists for this case; trust it. Half-size on confirmed hold.
- **Expansionist:** PROMOTE-on-trigger, half-size on inside-day. AFFO + raise + RS 89 + Risk-On 10/10 is real edge if entry disciplined.
- **Outsider:** DEFER. REIT rate sensitivity is the unmodeled risk; check IYR and rate calendar before any size.
- **Executor:** PROMOTE-on-trigger, half-size, mechanical. Stop $146.60, R:R ≥ 2.0 gate, DTE re-verify.

### Peer Review Highlights
- 3 of 5 (First Principles, Expansionist, Executor) converge on half-size on Day-2 confirmed hold. Median: DEFER → PROMOTE-on-trigger half-size.
- Outsider's macro/rate-calendar blind spot was unanimously upgraded into "do this first."
- Contrarian's grade-B sub-cohort warning correctly downweighted as too small but kept as confidence cap.
- Expansionist's "Risk-On 10/10 implies rates are supportive" challenged by Outsider — regime score is price-derived composite, not forward rate read.
- Executor's "stop is my macro hedge" accepted for trade management but rejected for position sizing — pre-trade macro filter still required.
- No advisor supported Day-1 entry. No advisor supported full-size on A2 trigger. Consensus confidence band: 50–60%, anchored 55%.

---

## 5) XPER — B+ Day-2 council / ACTIVE_BURST / monitor (thin liquidity)

**Verdict: DEFER → conditional PROMOTE-half, confidence 55%, playbook-only.**

### Outcome/Base-Rate Context
PARTIAL_OUTCOME — playbook-only. ACTIVE_BURST n=83, 91.6% trigger but T+1d win 49.3%. Catalyst-grade-B intersection n=8 (25% trigger, -0.20%) too small to anchor on but directionally discouraging. Hard rules clear, ext_sev moderate. Two structural drags: rs_3month MISSING (signal absence on momentum name = yellow flag) and ~$2.6M ADDV thin-liquidity skill cap forcing half-size regardless of A2.

### Where the Council Agrees
- Hard CANCEL not warranted: trigger structure intact, R:R 2.28R at C3 stop, regime supportive, catalyst (EPS +83%, margin 14.4%→22.1%) is a real inflection.
- Half-size cap is non-negotiable. A2 promotion does not unlock full size on $2.6M ADDV.
- bars_since_10ema_break=26 + ext_run=True = late-stage continuation, not fresh base. Edge is narrower than headline R:R suggests.
- LIMIT-only execution mandatory; market orders would self-inflict 30–80bps slippage.
- Missing rs_3month should be treated as a debit, not neutral.

### Where the Council Clashes
- Contrarian wants CANCEL — late-stage, weak intersection base rate, missing RS, slippage tax.
- Expansionist wants PROMOTE-half — margin inflection of this magnitude is a multi-quarter re-rating, $9.50 target conservative, Risk-On amplifies.
- First Principles: post-slippage on half-size, EV at 49.3% × 2.28R compresses meaningfully, may go negative-EV when weighted by 25% trigger rate of catalyst-B subset.
- Outsider: n=8 subset is statistical noise; EPS print is the dominant prior.
- Executor splits: DEFER to live trigger — only act on $7.93 break with ≥1.5x volume + tight bid/ask.

### Blind Spots Caught
- Slippage at half-size on a 7% stop distance could eat 0.15–0.25R of the 2.28R edge — meaningful in R-units even when dollars are small.
- rs_3month MISSING on a momentum-system signal more damning than treated; structurally weaker than score implies.
- bars_since_10ema_break=26 in "extended continuation" zone — historically lower follow-through, especially with ext_run=True.
- Next earnings Aug-2026 — no near-term catalyst refresh; trade has to work on momentum + re-rating alone.
- cpr 0.701 + mid-range Day-1 close = the actual reason Day-1 R:R failed; Day-2 inside-day is a valid second chance but you're paying the lower-quality close with thinner margin.

### Recommendation
**DEFER → conditional PROMOTE-half**, 55%, playbook-only. Do not pre-commit. Place a working LIMIT at or just above $7.93 ONLY IF intraday tape shows: (a) volume pacing ≥1.5x by mid-session, (b) bid/ask ≤ 0.3% spread, (c) DTE re-verified, (d) no break of $7.24 intraday. Half-size cap ($500 risk) holds regardless. If trigger fires clean → take it as 0.5R book-risk. If tape sloppy or fill poor → walk away. CANCEL if Day-2 closes <$7.24 or ADDV proxy <$1.5M. Slippage budget: assume 0.15R round-trip cost. Net expected edge ≈ 2.13R at 49.3% — positive but slim.

### One Thing to Do First
Re-verify DTE and check live bid/ask spread + Level 2 depth at $7.93 area before placing the limit. If spread >0.3% or depth <$25K on the offer → downgrade to skip. Liquidity reality check is the gate, not the chart.

### Advisor Snapshots
- **Contrarian:** CANCEL — late-stage, missing RS, catalyst-B subset 25%/-0.20%, slippage tax.
- **First Principles:** DEFER — EV math is marginal post-slippage; need live confirmation.
- **Expansionist:** PROMOTE-half — margin inflection is a re-rating catalyst, regime supportive.
- **Outsider:** PROMOTE-half cautiously — EPS beat dominates; n=8 subset is noise.
- **Executor:** DEFER → conditional half — work the limit, walk if tape is sloppy.

### Peer Review Highlights
- Contrarian's CANCEL was challenged on over-weighting n=8 catalyst-B subset; conceded but held that missing rs_3month + bars=26 still independently argue against entry.
- Expansionist's "$9.50 is conservative" pushed back: re-rating thesis is multi-quarter, doesn't help T+1 to T+5 momentum trade.
- Outsider's "thin liquidity overstated at half-size" partially accepted — but Executor noted slippage shows up in R-units even when dollars are small.
- First Principles' EV math was the most-cited framework; consensus formed around DEFER-with-live-gates rather than binary PROMOTE/CANCEL.
- All five flagged missing rs_3month as under-weighted — recommend treating data-gap as half-step debit on composite_score going forward.

---

## 6) APP — CONFLICT_A,D / ACTIVE_BURST / today_intraday

**Verdict: DEFER-FOR-CONFIRMATION → OVERRIDE-HALF conditional, confidence 6/10, playbook-only.**

### Outcome/Base-Rate Context
- ACTIVE_BURST overall: n=83, T+1d win 49.3%, avg -0.72%.
- ACTIVE_BURST × catalyst-A: n=2, avg -5.17% T+1d. Too small but directionally cautionary.
- **ACTIVE_BURST × WATCH_ONLY × action_label B (APP's exact path): n=17, 64.7% triggered, T+1d -0.73%, win 45.5%.**
- WATCH_ONLY × C: n=28, -3.33% T+1d, win 40.0%.
- REJECT × D: n=36, +1.49% T+1d, win 58.8%.

Directional read: WATCH tier is doing real work. Sample sizes small (n=17, n=28); soft prior, not law. The "lower tier wins" rule was designed precisely for this configuration.

### Where the Council Agrees
- Price-action picture is genuinely clean. Gates 1-6 PASS, vol 2.75x, CPR 80.2%, dist_21ema 9.0%, grade-A catalyst with $1B buyback is a legitimate institutional signal.
- WATCH tier exists for exactly this scenario. QG=False AND spec=True together is the two-flag fundamental rejection the framework was built to respect.
- Risk-On 10/10 affects portfolio aggression, not whether you override a documented gating rule.
- **This is a calibration moment, not a max-conviction moment.** The right move is the one that preserves the integrity of the WATCH tier as a signal going forward.
- If anything is taken: smaller than normal A2 with tighter, mechanical invalidation.

### Where the Council Clashes
- Contrarian/Outsider want zero position: respect the WATCH, log it, let the tape prove the system wrong over n≥20 before changing the rule.
- Expansionist: catalyst stack (beat + raise + $1B buyback + $1.21B net cash) is materially different from typical QG-fail + spec-true row; base rate contaminated by lower-quality catalysts. Wants OVERRIDE-HALF.
- First Principles: Bayesian — rule is prior, catalyst is evidence; update justifies reduced-size override only if invalidation is mechanical and pre-committed.
- Executor: bigger risk is the trader teaching themselves that gates-clean + good catalyst overrides WATCH. That precedent is more expensive than this trade.

### Blind Spots Caught
- Catalyst-A in this cohort is n=2 at -5.17%. The "good catalyst saves it" intuition is not supported by the data we have, even thin.
- ep_gap_pct -2.98% (gap-down then ramped) is not a clean breakout — it's a recovery day. Gates pass, but setup is closer to reversal-to-trend than fresh thrust.
- consec_up=1 means today is the entire move. There is no confirmation bar.
- Invalidation choice matters: pause_high $483.55 vs Day-1 LOD $479.31 = ~3% spread on $498.87 entry. Sizing not trivial.
- Speculative_flag=True often correlates with bimodal cohorts (explosive winners + explosive losers); negative mean is still negative-EV at full size.

### Recommendation
**DEFER-FOR-CONFIRMATION today, with a pre-committed OVERRIDE-HALF trigger tomorrow.** No position at today's close. Pre-commit: if APP closes tomorrow above today's close ($498.87) on volume ≥ 1.5x 50-day, take HALF size A2 (0.5% account risk, NOT 1%). Invalidation: pause_high $483.55, mechanical, no discretion. If APP closes red tomorrow or fails to hold $483.55 intraday → row dead, WATCH tier vindicated. Do NOT take FULL A2. Confidence 6/10. The recommendation is about preserving the WATCH-tier signal's integrity as much as it is about this specific trade.

### One Thing to Do First
Write the override condition into the journal *before* tomorrow's open: exact price ($498.87 close), exact volume threshold (1.5x 50-day), exact invalidation ($483.55), exact size (half A2 = 0.5% risk). **If you cannot pre-commit it in writing tonight, you do not take it tomorrow. The discipline test is the trade.**

### Advisor Snapshots
- **Contrarian:** RESPECT-WATCH. The rule exists for this row. Don't break it on case #1.
- **First Principles:** OVERRIDE-HALF, conditional. Catalyst is real evidence; size down to reflect prior.
- **Expansionist:** OVERRIDE-HALF now. $1B buyback + raise is a different animal than the cohort average.
- **Outsider:** RESPECT-WATCH or DEFER. consec_up=1 on a gap-down-ramp is not a breakout you chase.
- **Executor:** DEFER-FOR-CONFIRMATION. Process integrity > this trade. Pre-commit the override condition in writing.

### Peer Review Highlights
- Contrarian's "case #1" framing pushed Expansionist to concede half-size, not full.
- Expansionist's "base rate contaminated" landed: n=17 cohort almost certainly includes catalyst-D and -C rows. But catalyst-A subsample at n=2 / -5.17% blunts the rebuttal. Council judged contamination directionally valid but not strong enough to support full size.
- Outsider's gap-down-ramp structural read was the most-credited blind-spot catch — three other advisors had treated CPR 80.2% as a clean thrust signal without examining ep_gap_pct.
- First Principles' Bayesian framing accepted as cleanest synthesis: prior negative, evidence real, posterior neutral, neutral means smaller size with confirmation.
- Executor's "the precedent is the trade" was the dominant tiebreaker. Even Expansionist agreed pre-committing in writing is non-negotiable if any position is taken.
- Convergence: DEFER today, OVERRIDE-HALF tomorrow if confirmation triggers, RESPECT-WATCH if not. **No advisor defended FULL A2.**

---

## Notes on this batch
- Outcome data is monitoring-only at cohort age -3 days; none of these verdicts qualify as evidence-backed.
- The recommended trades, if taken at the proposed sizes, sum to a max simultaneous risk of ~$2,500 (IBEX $500 + ORA $500 + LAMR $500 conditional + XPER $500 conditional + APP $500 conditional + SNEX $1,000 conditional). At most three should fire on any one open. Position-by-position trigger discipline is the binding edge.
- Re-run the council with mature outcome data after T+5 bars are available (~2026-05-15) to upgrade any of these from playbook-only to evidence-backed.
