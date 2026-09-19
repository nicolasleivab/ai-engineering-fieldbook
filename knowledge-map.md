# AI Engineering Knowledge Map

_Last reviewed: 2026-09-19_

## Shelf-life legend

- **Stable** — learn deeply; the principle should outlast current tooling.
- **Evolving** — understand and prototype periodically.
- **Volatile** — track awareness; avoid memorizing vendor-specific details.

## System map

| Domain | Stable principles | Evolving patterns | Volatile implementations | Current stance |
|---|---|---|---|---|
| Models | capability boundaries, generalization, evaluation | routing, adaptation, distillation | model IDs and pricing | Select by measured task performance, latency, and cost |
| Context | relevance, finite attention, context budgeting | compaction, just-in-time retrieval | SDK context APIs | Curate the smallest sufficient context |
| Tools | explicit contracts, validation, error semantics | discovery, MCP ecosystems | schemas and transports | Treat tools as typed, permissioned interfaces |
| Harness | observe-decide-act loop, separation of concerns | planning, delegation, subagents | framework APIs | Keep the control loop inspectable and testable |
| State | durability, idempotency, retries, checkpoints | resumable workflows | orchestration libraries | Workflow state is authoritative; do not hide it in chat history |
| Memory | write/retrieve/update/forget policies | consolidation, temporal graphs | memory vendors | Memory is learned persistent information, not transcript replay |
| Retrieval | precision/recall, ranking, provenance | agentic retrieval, hybrid search | vector DB APIs | Measure retrieval independently and end-to-end |
| Execution | isolation, least privilege, resource limits | ephemeral sandboxes | sandbox vendors | Assume generated code and external content are untrusted |
| Reliability | outcome evals, trace diagnosis, regression tests | automated judges, simulation | observability SDKs | Start with task success; use traces to explain failures |
| Security | authentication, authorization, data boundaries | prompt-injection defenses | platform controls | Enforce permissions outside the model |
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

- Which memory write and invalidation policies work best for long-running assistants?
- Where does Temporal end and agent-managed state begin?
- Which agent evals correlate best with production outcomes?
- When does post-training outperform a better harness or better context?
- What security boundaries should remain deterministic and model-independent?
