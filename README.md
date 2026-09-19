# AI Engineering Fieldbook

A living, versioned map of durable AI/ML fundamentals and fast-moving production agent engineering.

The goal is not to collect every new framework. It is to understand stable concepts deeply, track implementation changes selectively, and turn meaningful developments into experiments and engineering decisions.

## How this repository works

| Area | Purpose | Update cadence |
|---|---|---|
| [Knowledge map](./knowledge-map.md) | Stable principles, evolving patterns, volatile implementations, and our current stance | When evidence changes the map |
| [Catch-up roadmap](./roadmap.md) | Initial four-week path from fundamentals to production hardening | Weekly during catch-up |
| [Weekly updates](./weekly/) | High-signal changes, implications, and next actions | Weekly |
| `experiments/` | Reproducible prototypes and comparisons | When a question warrants testing |
| `decisions/` | Short architecture decision records | When we adopt or reject an approach |

## Operating principles

1. Separate **concepts** from **implementations**.
2. Classify knowledge by shelf life: stable, evolving, or volatile.
3. Prefer evidence and reproducible experiments over hype.
4. Start with end-to-end outcomes, then diagnose traces and components.
5. Treat context, memory, workflow state, and knowledge bases as distinct.
6. Fine-tune only after evaluating context, tools, retrieval, and harness design.
7. Record what changed, why it matters, and what action follows.

## Current learning sequence

1. LLM and transformer fundamentals
2. Model lifecycle and post-training
3. Modern agent harness architecture
4. Context vs memory vs workflow state
5. Evals and production feedback loops
6. Memory, retrieval, and durable execution
7. Custom models and post-training experiments
8. Production hardening: security, permissions, latency, cost, and recovery

## Status

Catch-up phase: **Week 1 — LLM reset and modern agent architecture**.

This is a personal engineering fieldbook maintained in public. It is intentionally opinionated and will change as evidence and production experience accumulate.
