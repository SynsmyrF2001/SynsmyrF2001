# Synsmyr Forgue

Systems Reliability & Infrastructure Engineer | Computer Science @ UMass Boston (Spring 2027)

I operate at the intersection of enterprise infrastructure and distributed systems engineering. My focus is on building resilient systems that stay correct under failure—from Active Directory identity infrastructure and enterprise SDN, to event-driven microservices, OpenTelemetry observability pipelines, and automated incident response services. 

---

## Featured Work

### [Windows Server Active Directory Homelab](https://github.com/SynsmyrF2001/homelab-ad-ds)
`Windows Server` · `AD DS` · `PowerShell` · `Group Policy` · `UTM`

Enterprise identity and domain infrastructure built from scratch under virtualization constraints. Deployed a Windows Server domain controller (`DC01.corp.local`) with self-hosted DNS, static routing, and all five FSMO roles. Automated departmental OU hierarchy provisioning and user lifecycle management using idempotent PowerShell scripts. Authored and linked scoped Group Policy Objects (GPOs) for domain-root password enforcement, departmental screen lock timeouts, and contractor USB block restrictions, validated via `gpresult` and fully documented in a dedicated troubleshooting log.

### [Sentinel — Autonomous Incident Response Service](https://github.com/SynsmyrF2001/Sentinel)
`Go` · `PostgreSQL` · `AWS Bedrock` · `Docker` · `Slack API`

Production incident management service written in Go designed to guarantee zero silent alert drops. Ingests alerts over HMAC-SHA256 verified webhooks with constant-time comparison, a TTL-bounded deduper, and a jittered exponential backoff worker pool that parks exhausted jobs in a dead-letter queue. Models the incident lifecycle as an explicit 5-state machine with a legal-transition table backed by an append-only event log, making full incident timelines reconstructable for post-mortems. Features automated LLM root-cause analysis and threaded Slack briefs that degrade gracefully when unconfigured. 157 Go tests.

### [Event-Driven Order Processing Platform](https://github.com/SynsmyrF2001/event-driven-order-platform)
`Python` · `Kafka` · `FastAPI` · `PostgreSQL` · `OpenTelemetry` · `Docker`

Distributed transaction pipeline across four microservices using saga orchestration over 13 typed Kafka schemas. Implements the transactional outbox pattern to eliminate dual-write failure windows by committing database state and event enqueues in a single ACID transaction. Enforces idempotent consumption under concurrency via row-level locks (`SELECT FOR UPDATE`), validated through chaos tests firing 100 concurrent load spikes. Propagates OpenTelemetry context across Kafka boundaries for distributed tracing in Jaeger, with circuit breakers and dead-letter queues holding p95 latency under 500 ms under Locust load testing.

### [Investment Portfolio Ledger & Reconciliation Engine](https://github.com/SynsmyrF2001/Investment-Portfolio-Ledger-Engine)
`Python` · `PostgreSQL` · `DuckDB` · `FastAPI` · `React`

Double-entry financial ledger where state correctness is enforced strictly at the database layer via PostgreSQL triggers rejecting unbalanced transactions (`debits ≠ credits`). Eliminates floating-point drift using exact decimal storage (`Numeric(18,6)`). Built a tolerance-based reconciliation engine (0.01% quantity, $0.01 absolute) across position and cash matchers to suppress false breaks, with immutable audit logging for every break resolution to satisfy SOC 2 CC6.1 compliance. Splits OLTP writes in Postgres from columnar analytics in DuckDB.

### [Autonomous Financial Research Agent](https://github.com/SynsmyrF2001/financial-research-agent)
`Python` · `AWS Bedrock` · `Redis` · `PostgreSQL` · `OpenTelemetry`

ReAct pattern and function calling implemented from first principles—JSON tool schemas, a Python execution engine, and `tool_result` blocks letting the model chain calls across market APIs without hardcoded control flow. Features two-tier memory (Redis 20-turn window + Postgres memos), a tool result cache, and SSE streaming, with every tool call instrumented as an OpenTelemetry child span.

---

## Technical Focus

* **Systems & Networking:** Windows Server, Active Directory (AD DS), Group Policy (GPO), DNS/DHCP, LDAP, TCP/IP, VLANs, QoS, UniFi SDN, Linux, macOS
* **Infrastructure & Automation:** Docker, PowerShell scripting, Bash, GitHub Actions (CI/CD), AWS (EC2, S3, Bedrock), Nginx
* **Observability & Reliability:** OpenTelemetry, Prometheus, Grafana, Jaeger, Chaos Testing, Locust Load Testing, Circuit Breakers, Dead-Letter Queues (DLQ)
* **Distributed Systems & Data:** Apache Kafka, Saga Orchestration, Transactional Outbox, Idempotent Consumers, PostgreSQL, DuckDB, Redis, MongoDB, pgvector
* **Languages:** Python, Go, PowerShell, Bash, SQL, Java, C/C++, JavaScript/TypeScript

---

## Contact

[LinkedIn](https://linkedin.com/in/synsmyrforgue) · [GitHub](https://github.com/SynsmyrF2001) · synsmyr.smf@gmail.com
