# AI Engineering Knowledge Map

_Last reviewed: 2026-11-22_

## Shelf-life legend

- **Stable** — learn deeply; the principle should outlast current tooling.
- **Evolving** — understand and prototype periodically.
- **Volatile** — track awareness; avoid memorizing vendor-specific details.

## System map

| Domain | Stable principles | Evolving patterns | Volatile implementations | Current stance |
|---|---|---|---|---|
| Models | capability boundaries, generalization, evaluation | routing, adaptation, distillation | model IDs and pricing | Select and pin the model–harness pair by measured task performance, latency, cost, and failure spend; re-evaluate when either version changes; in agentic post-training, validate sampler/trainer probability support, policy version, precision, masking, and objective equivalence before trusting reward curves |
| Context | relevance, finite attention, context budgeting | compaction, just-in-time retrieval | SDK context APIs | Curate the smallest sufficient context; treat compaction as a state transition that preserves provenance, committed actions, and unresolved approvals; when a response joins source and derived views, require one revision identity and an atomic publication boundary—serve complete-old, wait/fail, or complete-new context, never a mixed revision |
| Tools | explicit contracts, validation, error semantics, bounded inputs | discovery, capability-scoped authorization, MCP ecosystems | schemas, transports, OAuth/DPoP SDK surfaces | Treat tools as typed, permissioned, resource-bounded interfaces; annotations are advisory, so authorize before dispatch, bind authorization and use to the same opened object, neutralize ambient executable configuration, and enforce canonical resource scope, least-privilege modes, timeouts, cancellation, and output bounds at the server |
| Harness | observe-decide-act loop, separation of concerns, explicit state and approval ownership | planning, delegation, subagents, skill packaging and activation | framework APIs | Keep the control loop inspectable and testable; isolate per-run/per-agent state and scope approvals to the owning agent; treat skills as versioned, integrity-checked inputs and evaluate discovery, loading, and behavior separately |
| State | durability, idempotency, retries, checkpoints | resumable workflows | orchestration libraries | Persisted workflow state is authoritative; when transition rules are known, derive current state with validated deterministic reducers instead of asking a model to reconstruct it from long history; give every external resource a lifecycle owner through timeout, cancellation, and ambiguous errors; test replay compatibility and drain or version workers before behavior-changing upgrades; historical checkpoints must fork explicitly and preserve sibling isolation |
| Memory | write/retrieve/update/forget policies, verified persistence | consolidation, temporal graphs, derived user profiles | memory vendors | Memory is learned persistent information, not transcript replay, and persistence alone is not continual learning; separate source logs, stored content, persistent access/index state, derived representations, and exposure policy; measure task-conditioned future-action gain against formation, maintenance, and exposure cost under interference and change, preserve provenance for repair, distinguish seen-task reuse from unseen-task generalization, compare against cache and parametric-learning baselines, and use derived representations to complement rather than silently replace search |
| Retrieval | precision/recall, ranking, provenance | agentic retrieval, hybrid search | vector DB APIs | Measure retrieval independently and end-to-end |
| Execution | isolation, least privilege, resource limits, idempotency-aware retries | ephemeral sandboxes | sandbox vendors | Assume generated code and external content are untrusted; semantic read-only is not side-effect-free when an interpreter, repository, special file, or ambient configuration can execute behavior; require authenticated ingress, enforced egress, object-bound resource checks, neutralized execution hooks, and owned cleanup; automatically retry only operations known safe to replay, otherwise use idempotency keys or reconciliation |
| Reliability | outcome evals, trace diagnosis, regression tests, oracle integrity | automated judges, simulation | observability SDKs | Start with task success, then test trajectories and components; validate graders, score transforms, fixtures, runner failures, oracle non-interference, terminal-state reconstruction, and declared run conditions with golden cases in a clean grading environment; preserve and evaluate intermediate states for long runs, treat self-tests as signals rather than the oracle, and promote stopping rules only after paired hidden-test non-inferiority |
| Security | authentication, authorization, least privilege, data boundaries, resource bounds | prompt-injection defenses, sender-constrained credentials, trajectory auditing | platform controls | Enforce identity, permissions, resource limits, and data minimization outside the model on canonical resource identities; inherit policy through delegation, audit sensitive reads and outbound writes, and fail closed |
| Economics | latency/quality/cost trade-offs | routing and caching strategies | token prices | Optimize against representative workloads |

## Essential distinctions

```text
conversation history ≠ context ≠ working memory
                     ≠ long-term memory
                     ≠ workflow state
                     ≠ knowledge base
```

- **Conversation history:** raw interaction record.
- **Context:** curated information supplied to the model now.
- **Working memory:** temporary task-local information.
- **Long-term memory:** selected persistent facts or experiences.
- **Workflow state:** authoritative execution progress and invariants.
- **Knowledge base:** externally maintained domain information.

## Weekly decision rule

1. Does new evidence change a fundamental mental model? **Study deeply.**
2. Could it materially improve capability, reliability, cost, or velocity? **Prototype.**
3. Is it mainly a new implementation or API? **Record briefly.**
4. Otherwise: **watch or ignore.**

## Open questions

- Which store, access-index, recall, consolidation, and forget policies improve task-conditioned future actions under interference and change without creating popularity feedback loops; do they improve seen-task reuse, unseen-task generalization, or both; and when do their maintenance and exposure costs exceed a cache or parametric-learning baseline?
- Where does Temporal end and agent-managed state begin?
- Which end-to-end, anytime, and model–harness interaction evals correlate best with production outcomes?
- When does post-training outperform a better harness or better context, and which parity checks prove that sampler and trainer optimize the intended objective?
- What security boundaries should remain deterministic and model-independent?
- How should skill discovery and activation be measured independently from skill quality after loading?
- How should portable skill catalogs be versioned, verified, trusted, and invalidated?
- Which object-binding, ambient-config neutralization, revision-publication, lifecycle-ownership, deterministic-reducer, state-ownership, approval-scope, compaction, recovery, replay-versioning, anytime-stopping, oracle-integrity, and checkpoint-branch invariants should become cross-framework conformance tests?
- Which trajectory-level privacy checks catch real violations without blocking legitimate work?
- Which authorization evals distinguish useful initiative from scope drift and trigger consultation at the right boundary?
