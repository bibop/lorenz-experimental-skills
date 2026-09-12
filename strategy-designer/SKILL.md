---
name: strategy-designer
description: Turn an eligible trading hypothesis into an auditable draft StrategySpec; use before simulation, never for orders, P&L, broker access, or promotion.
---

# Strategy Designer

## Boundary

Design a draft from a supplied `EvidenceBundle`, frozen universe, and immutable
evaluator, cost, benchmark, and risk-policy references. The skill has no broker,
secret, code-execution, P&L, holdout, promotion, or deployment authority. Its
output is not approval and cannot start a simulation.

## Procedure

1. Resolve the requested hypothesis and every research claim through the
   supplied evidence digest.
   `TIER_3_ONLY` material may identify only a `FAILURE_MODE`; never relabel it
   as a `STRATEGY_CANDIDATE` or use it as evidence of alpha.
2. Reject or revise requests that conflict with the frozen universe or risk
   policy; never weaken policy to preserve the user's proposed tactic.
3. Define a causal target, permitted feature groups, model lane, abstention
   rule, and execution assumptions. A signal observed after close on session
   `t` cannot execute before the next session.
4. Treat every learned model, including TCN or Transformer, as a challenger.
   Do not predict that complexity will outperform a simpler baseline.
5. Record assumptions, falsification criteria, failure modes, unresolved
   questions, and any changes made to the request.
6. Require explicit owner confirmation of the resulting manifest before a
   separate system creates a simulation.

## Output

Return only the object defined by `schemas/output.schema.json`. A ready draft
contains a `StrategySpec`, confirmation summary, and assumption diff. If the
evidence is insufficient, return `INSUFFICIENT_EVIDENCE` with no strategy spec.
Set `evidenceGate=TIER_3_ONLY_FAILURE_MODE` when the supplied bundle contains
only Tier 3 support. In that case the decision must be `INSUFFICIENT_EVIDENCE`
and `strategySpec` must be `null`.

## Invariants

- Do not emit orders, positions, trades, fills, broker payloads, or P&L.
- `TIER_3_ONLY` is always a `FAILURE_MODE`. A Tier-3-only bundle can produce
  only `evidenceGate=TIER_3_ONLY_FAILURE_MODE`, `INSUFFICIENT_EVIDENCE`, and
  `strategySpec=null`.
- Do not invent expected returns, Sharpe ratios, win rates, or profit claims.
- Do not alter immutable evaluator, cost, benchmark, or risk-policy references.
- Keep `longOnly=true`, leverage/short/options/crypto disabled, and
  `NO_TRADE` available for this qualification.
- A draft is always `DRAFT_UNCONFIRMED`; only the evaluator can qualify it.
