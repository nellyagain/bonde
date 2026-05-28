# Active Candidate Context

Generated: 2026-05-28
Packet date: 2026-05-27
Status: AUTO_GENERATED_FROM_CURRENT_PACKET

Instruction: Use this as current candidate context. Do not use stale root-level dated files as current context.

## Current council candidates

| ticker   | action_label   | primary_setup   | tier   |   trigger_price |   invalidation_price | planned_size   | decision_reason                                                                                                                                                                                                                                                                                                                            |
|:---------|:---------------|:----------------|:-------|----------------:|---------------------:|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MAC      | A2             | slingshot       | TAKE   |           22.74 |                22.38 | half           | [V5.9.17 Slingshot_vol_gate: 1.26x PASS] Clean A2 slingshot: vol PASS, uptrend PASS, range_break PASS, contraction 54.4, slingshot R:R 3.17 PASS. The only A1/A2 candidate today. Routed COUNCIL (not auto-TRADE) per V5.9.28 candidate-preservation + V5.9.19 cautious resolution: unvalidated slingshot edge + offering overhead supply. |

## Use rules

- `final_trade_status` is the executable/routing field.
- `tier` is dashboard/source context only.
- Sugar Babies, market, and regime context are advisory only.
- Do not override R:R, DTE, hard rejects, failed EP, bag-holder, dilution/offering, or data-quality gates.
