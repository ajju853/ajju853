## Hi, I'm Ajim Patel 👋

### Backend Engineer | Distributed Systems | Event-Driven Architecture

I design and build production-grade distributed systems. My focus is on **reliability patterns** — transactional outbox, dead letter queues, idempotent consumers, and saga orchestration — not just CRUD APIs.

---

## 🚀 What I'm Building

* **Event-driven microservices** with Kafka as the central event bus, supporting 1M+ orders/day
* **Resilient consumer pipelines** with exponential backoff retry, DLQ routing, and at-least-once semantics
* **Idempotent event processing** via consumer-side deduplication tables
* **Transactional Outbox pattern** ensuring atomic database writes + Kafka publishes (no lost events)
* **Observable systems** with health checks, structured JSON logging, and Prometheus/Grafana dashboards

---

## 💻 Backend Architecture Patterns

**Messaging & Eventing**

* Kafka (topics, consumer groups, partitioning, offset management)
* Event schema design with versioning
* Dead Letter Queue architecture
* Exactly-once semantics via idempotent producers

**Reliability**

* Transactional Outbox pattern
* Exponential backoff with jitter
* Consumer-side idempotency (`processed_events` table)
* Saga orchestration for distributed transactions

**Data**

* PostgreSQL — schema design, indexing, connection pooling, pagination
* Redis — inventory caching, rate limiting, hot data
* CQRS — separate write/read models for analytics and audit

**Infrastructure**

* Docker Compose for local dev (Kafka + ZK + Postgres + Redis + 5 services)
* Kubernetes — StatefulSets, Deployments, HPA, ConfigMaps, Secrets, Ingress
* GitHub Actions — test → build → push → deploy pipeline

---

## 🔥 Flagship Project

### Kafka Order Management System

Architecture:

```
Frontend (Next.js)
      │ REST
Order Service ──► Kafka ──► Inventory Service (Redis)
                      │
                      ├──────────► Notification Service
                      ├──────────► Analytics Service (PostgreSQL)
                      └──────────► Audit Service (event sourcing)
```

**Key design decisions:**
- **Transactional Outbox** → order + event saved in single DB transaction; background publisher guarantees Kafka delivery
- **DLQ** → failed events routed to `order-dlq` with full error context; 30-day retention for replay
- **Idempotency** → each consumer checks `processed_events` table before processing; safe under replays
- **Retry** → 3 attempts with 5s → 30s → 120s exponential backoff
- **Horizontal scaling** → 2-10 pods via Kubernetes HPA (CPU/memory based)

**Stack:** Node.js, TypeScript, Kafka, PostgreSQL, Redis, Docker, Kubernetes, Next.js

---

## 📫 Connect

* LinkedIn: [linkedin.com/in/ajim-patel-b359192ab](http://www.linkedin.com/in/ajim-patel-b359192ab)
* Email: [ajimp340@gmail.com](mailto:ajimp340@gmail.com)

---

### "System design isn't about choosing the right technology. It's about handling the failure before it happens."
