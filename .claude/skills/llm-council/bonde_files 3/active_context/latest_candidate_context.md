# ACTIVE CANDIDATE CONTEXT

Generated: 2026-05-16
Source packet: 2026-05-15 V5.9.19-compatible decision log
Status: CURRENT
Instruction: Treat this file as the current candidate context. Do not treat archived reports or root-level dated files as current.

## Current council candidates

The current council packet contains **2 candidates**. Both are routed to council because `final_trade_status=COUNCIL` and both are B+ C1 wide/R:R floor cases.

| Ticker | final_trade_status | action_label | primary_setup | tier | Catalyst | Trigger | Invalidation | Key issue |
|---|---|---|---|---|---|---:|---:|---|
| SPIR | COUNCIL | B+_C1 | slingshot | UNKNOWN | Earnings + guidance raise, Q1 2026 reported 13-May | 20.45 | 17.74 | Wide Day-1 range; no defensible target clears 2R from trigger/stop. Day-2 controlled pullback or inside-day needed. |
| WRBY | COUNCIL | B+_C1 | delayed_ep | TAKE | Earnings beat + AI glasses positioning, Q1 2026 reported 7-May | 29.95 | 27.77 | Wide Day-1 range; measured-move target implies sub-2R. Tighter Day-2 pullback/reclaim needed. |

## Candidate-level interpretation

- `final_trade_status` is the executable/routing field.
- `tier=TAKE` is not trade authorization.
- Both rows require council judgment before any trade.
- Both should be evaluated as `Day-2 pullback rescue` / R:R rescue cases unless the council identifies an independent valid entry/stop/target structure.
- A PROMOTE verdict should specify exact order type, entry, stop, target/R:R, order duration, and cancellation conditions.

## SPIR notes

- Setup family in skill pack includes SLINGSHOT and ACTIVE_BURST evidence; council row primary setup is `slingshot`.
- Slingshot confirmation flags pass: uptrend, range break, contraction quality.
- Volume gate passes: today/prior volume about 1.82x.
- RS context strong; close above 200SMA.
- Main blocker: wide trigger-bar stop and inadequate target/R:R from standard references.
- Council should prefer DEFER unless a Day-2 controlled pullback materially improves R:R without damaging the setup.

## WRBY notes

- Primary setup: delayed_ep / DEP.
- DEP volume gate passes: today/prior volume about 1.51x.
- Structure clean: no extension severity, swing-day context, RS strong.
- Main blocker: target/reference structure near 252d high gives sub-2R on Day-1 trigger geometry.
- Council should not treat `tier=TAKE` as automatic trade permission.

## Required council behavior

- Include Context Files Loaded.
- Use `final_trade_status=COUNCIL` as the routing field.
- Treat market/regime context as advisory execution context, not a trade gate.
- Include Portfolio Heat if either candidate is promoted.
- Since the review context is around a Friday/weekend window, avoid casual GTC language; default to DAY/cancel-before-close unless justified.
