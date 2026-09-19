# Catch-up Roadmap

Assumption: roughly six focused hours per week. Preserve the sequence; scale session length if needed.

| Phase | Fundamentals | Agent frontier |
|---|---:|---:|
| Week 1 | 55% | 45% |
| Week 2 | 45% | 55% |
| Week 3 | 30% | 70% |
| Week 4 | 20% | 80% |
| Steady state | 0–10% | 90–100% |

## Week 1 — LLM reset and modern architecture

- Transformer path: tokens → embeddings → attention/MLP blocks → logits → sampling.
- Model lifecycle: pretraining → SFT → preference/RL post-training → optional task adaptation.
- Agent system map: model, harness, context, tools, state, memory, permissions, traces.
- Deep distinction: context vs memory vs state vs knowledge.
- Evals loop: traces → taxonomy → dataset → change → compare → deploy.

**Deliverable:** explain and draw the complete production-agent mental model from memory.

## Week 2 — Memory, retrieval, and durable execution

- Implement one small agent with explicit workflow state.
- Add semantic and episodic memory with clear write/retrieval policies.
- Test stale, contradictory, irrelevant, and missing memories.
- Compare persistence/checkpointing with learned memory.
- Evaluate lexical, vector, hybrid, and reranked retrieval where appropriate.

**Deliverable:** working prototype plus an architecture note describing ownership of every stateful component.

## Week 3 — Eval engineering and post-training

- Build a representative task set.
- Annotate initial traces and create a failure taxonomy.
- Add end-to-end success measures and targeted component checks.
- Learn SFT, LoRA/QLoRA, preference optimization, synthetic data, and distillation.
- Run one narrow adaptation experiment only if the evals justify it.

**Deliverable:** baseline report showing whether a harness, retrieval, prompt, tool, or model change is needed.

## Week 4 — Production hardening

- Sandboxing and external-content trust boundaries.
- Authentication, authorization, approvals, and least privilege.
- Timeouts, retries, idempotency, partial failure, and recovery.
- Latency, caching, routing, token use, and cost.
- Human-in-the-loop and dangerous-action boundaries.

**Deliverable:** production readiness checklist and prioritized gaps.

## Steady state

Each week:

1. Review a high-signal frontier digest.
2. Map developments to stable/evolving/volatile.
3. Select at most one deep study or experiment.
4. Update the knowledge map only when evidence changes our stance.
5. Record architecture decisions with rationale and revisit triggers.
