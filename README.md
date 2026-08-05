# Synsmyr Forgue

Backend engineer focused on distributed systems, event-driven architecture, and financial infrastructure.
B.S. Computer Science, University of Massachusetts Boston — May 2027.

I build systems that have to stay correct under failure: exactly-once message processing, ledgers that
can't go out of balance, and incident pipelines that degrade cleanly when their dependencies are down.
Most of what's here is written from first principles rather than assembled from frameworks.

---

## Featured Work

### [Event-Driven Order Processing Platform](https://github.com/SynsmyrF2001/event-driven-order-platform)
`Python` · `Kafka` · `FastAPI` · `PostgreSQL` · `OpenTelemetry`

Saga orchestration across four microservices coordinating distributed transactions over Kafka.
Implements the transactional outbox pattern — the database write and the event publish commit in one
ACID transaction, so events are never lost to a dual-write failure. Consumers are idempotent under
concurrency via row-level locks: a chaos test fires 100 concurrent orders against a stock of 50 and
asserts exactly 50 succeed. OpenTelemetry trace context propagates across Kafka message boundaries,
so a single trace spans producer → broker → consumer.

### [Sentinel — Autonomous Incident Response](https://github.com/SynsmyrF2001/Sentinel)
`Go` · `PostgreSQL` · `Claude` · `Slack API`

Ingests production alerts over HMAC-verified webhooks, correlates them into incidents, and enriches
each one through a feature-gated pipeline: LLM root-cause analysis, embedding-based runbook retrieval,
metric-derived impact, and a threaded Slack brief. The incident lifecycle is an explicit five-state
machine with a documented legal-transition table, backed by an append-only event log — any incident's
full timeline is reconstructable. Every enrichment step no-ops when unconfigured, so the service runs
end-to-end with zero API keys.

### [Investment Portfolio Ledger & Reconciliation Engine](https://github.com/SynsmyrF2001/Investment-Portfolio-Ledger-Engine)
`Python` · `PostgreSQL` · `DuckDB` · `FastAPI` · `React`

A double-entry accounting ledger where correctness is enforced by the database rather than the
application — a Postgres trigger rejects any transaction where debits ≠ credits, so even raw SQL
cannot write an inconsistent state. Monetary values use exact decimal, not float. Includes portfolio
analytics (time- and money-weighted returns, Sharpe ratio, Brinson attribution) and a tolerance-based
reconciliation engine whose break resolutions are append-only with actor and written justification.

### [Autonomous Financial Research Agent](https://github.com/SynsmyrF2001/financial-research-agent)
`Python` · `AWS Bedrock` · `Redis` · `OpenTelemetry`

The ReAct pattern and tool use implemented from first principles — JSON tool schemas, a Python
execution layer, and `tool_result` blocks let the model chain calls across market data APIs without
hardcoded control flow. Two-tier memory (Redis session window + PostgreSQL memos), a tool result
cache, and SSE streaming. Every tool call is an OpenTelemetry child span visible in Jaeger.

### [AI-Powered Log Analytics & Incident Response API](https://github.com/SynsmyrF2001/log-analyst)
`Python` · `pgvector` · `AWS Bedrock` · `FastAPI`

A RAG pipeline over structured logs — Titan embeddings in a pgvector HNSW index, retrieved by cosine
similarity and passed to a structured SRE prompt that returns P1/P2/P3 incident reports with root
cause, affected services, and prioritized remediation.

---

## Technical Focus

**Languages** — Python, Go, Java, JavaScript/TypeScript, C/C++, SQL

**Distributed systems** — Kafka, saga orchestration, transactional outbox, idempotent consumers,
circuit breakers, dead-letter queues, event sourcing, database-per-service

**Data** — PostgreSQL, DuckDB, Redis, MongoDB, pgvector, SQLAlchemy

**Reliability** — OpenTelemetry, Prometheus, Grafana, Jaeger, chaos testing, contract testing,
load testing, testcontainers

**Infrastructure** — Docker, GitHub Actions, AWS, Nginx

---

## Contact

[LinkedIn](https://linkedin.com/in/synsmyrforgue) · synsmyr.smf@gmail.com
