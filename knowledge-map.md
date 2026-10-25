# AI Engineering Knowledge Map

_Last reviewed: 2026-10-25_

## Shelf-life legend

- **Stable** — learn deeply; the principle should outlast current tooling.
- **Evolving** — understand and prototype periodically.
- **Volatile** — track awareness; avoid memorizing vendor-specific details.

## System map

| Domain | Stable principles | Evolving patterns | Volatile implementations | Current stance |
|---|---|---|---|---|
| Models | capability boundaries, generalization, evaluation | routing, adaptation, distillation | model IDs and pricing | Select by measured task performance, latency, and cost |
| Context | relevance, finite attention, context budgeting | compaction, just-in-time retrieval | SDK context APIs | Curate the smallest sufficient context; treat compaction as a state transition that preserves provenance, committed actions, and unresolved approvals |
| Tools | explicit contracts, validation, error semantics, bounded inputs | discovery, capability-scoped authorization, MCP ecosystems | schemas, transports, OAuth/DPoP SDK surfaces | Treat tools as typed, permissioned, resource-bounded interfaces; authorize before dispatch |
| Harness | observe-decide-act loop, separation of concerns, explicit state and approval ownership | planning, delegation, subagents, skill packaging and activation | framework APIs | Keep the control loop inspectable and testable; isolate per-run/per-agent state and scope approvals to the owning agent; treat skills as versioned, integrity-checked inputs and evaluate discovery, loading, and behavior separately |
| State | durability, idempotency, retries, checkpoints | resumable workflows | orchestration libraries | Persisted workflow state is authoritative; reconcile transient projections after cancellation or resume; replaying or updating historical checkpoints must fork explicitly and preserve sibling isolation |
| Memory | write/retrieve/update/forget policies, verified persistence | consolidation, temporal graphs, derived user profiles | memory vendors | Memory is learned persistent information, not transcript replay; evaluate store, recall, and forget policies by future-action gains under interference and change, not retrieval accuracy alone |
| Retrieval | precision/recall, ranking, provenance | agentic retrieval, hybrid search | vector DB APIs | Measure retrieval independently and end-to-end |
| Execution | isolation, least privilege, resource limits, idempotency-aware retries | ephemeral sandboxes | sandbox vendors | Assume generated code and external content are untrusted; automatically retry only operations known safe to replay, otherwise use idempotency keys or reconciliation |
| Reliability | outcome evals, trace diagnosis, regression tests, oracle integrity | automated judges, simulation | observability SDKs | Start with task success, then test trajectories and components; validate graders, score transforms, fixtures, runner failures, oracle non-interference, and terminal-state reconstruction with golden cases |
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

- Which store, recall, and forget policies improve future actions under interference and change?
- Where does Temporal end and agent-managed state begin?
- Which agent evals correlate best with production outcomes?
- When does post-training outperform a better harness or better context?
- What security boundaries should remain deterministic and model-independent?
- How should skill discovery and activation be measured independently from skill quality after loading?
- How should portable skill catalogs be versioned, verified, trusted, and invalidated?
- Which state-ownership, approval-scope, compaction, recovery, oracle-integrity, and checkpoint-branch invariants should become cross-framework conformance tests?
- Which trajectory-level privacy checks catch real violations without blocking legitimate work?
- Which authorization evals distinguish useful initiative from scope drift and trigger consultation at the right boundary?
