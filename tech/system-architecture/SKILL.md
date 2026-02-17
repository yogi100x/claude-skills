---
name: system-architecture
version: 2.0.0
description: "When the user needs to design system architecture for a new service or feature. Also use when the user mentions 'system architecture,' 'system design,' 'architecture diagram,' 'service design,' 'microservices,' or 'monolith.' This skill covers system architecture design."
---

# System Architecture

You are an expert in software system architecture. Your goal is to design systems that are reliable, scalable, and maintainable.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Current tech stack and infrastructure
  ├─ Scale requirements (users, requests, data)
  ├─ Team size and capabilities
  └─ Non-functional requirements (latency, availability)
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Architecture Style

```
START: What are you building?

├─ STARTUP/MVP (small team, fast iteration)
│  ├─ Monolith first (modular monolith)
│  ├─ Managed services (Supabase, Vercel, etc.)
│  ├─ Background jobs for async work
│  └─ Key: Speed of iteration > perfect architecture

├─ GROWING PRODUCT (10-50 engineers, scaling)
│  ├─ Modular monolith or service-oriented
│  ├─ Extract services at pain points
│  ├─ Event-driven for cross-domain communication
│  └─ Key: Clear domain boundaries, team autonomy

├─ SCALE (50+ engineers, high traffic)
│  ├─ Microservices with API gateway
│  ├─ Event sourcing for complex domains
│  ├─ CQRS for read/write optimization
│  └─ Key: Independent deployability, observability

└─ REAL-TIME (chat, collaboration, gaming)
   ├─ WebSocket/SSE for live updates
   ├─ Event-driven architecture
   ├─ CRDT for conflict resolution
   └─ Key: Eventual consistency, conflict handling
```

---

## Architecture Components

### Standard Web Application Stack

```
Client → CDN → Load Balancer → App Servers → Database
                    │                │
                    └── Static Assets  └── Cache (Redis)
                                       └── Background Jobs
                                       └── File Storage (S3/R2)
                                       └── Search (if needed)
```

### Key Design Decisions

| Decision | Options | When to Choose |
|----------|---------|---------------|
| **Database** | PostgreSQL, MySQL, MongoDB | Postgres for most; Mongo for document-heavy |
| **Cache** | Redis, Memcached | Redis for versatility, Memcached for simple caching |
| **Queue** | Redis, SQS, RabbitMQ | Redis for simple; SQS for AWS; RabbitMQ for complex routing |
| **File storage** | S3, R2, GCS | R2 for no egress fees; S3 for ecosystem |
| **Search** | PostgreSQL FTS, Elasticsearch, Meilisearch | Postgres FTS first; dedicated search for complex needs |
| **Real-time** | WebSocket, SSE, Polling | WebSocket for bidirectional; SSE for server-push; polling for simplicity |

### Scaling Patterns

| Pattern | What It Solves | Implementation |
|---------|---------------|----------------|
| **Horizontal scaling** | More concurrent users | Stateless app servers behind load balancer |
| **Read replicas** | Database read bottleneck | Route reads to replicas, writes to primary |
| **Caching** | Repeated expensive queries | Cache-aside with Redis/Memcached |
| **CDN** | Static asset delivery, global latency | CloudFront, Cloudflare |
| **Background jobs** | Long-running operations | Trigger.dev, Bull, SQS workers |
| **Connection pooling** | Database connection limits | PgBouncer, Supavisor |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T1 | Premature microservices | Complexity without benefits |
| T2 | No caching strategy | Database bottleneck |
| T3 | Synchronous everything | Slow responses, cascading failures |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Simplicity** | Over-engineered | Appropriate complexity | Simplest design that works |
| **Scalability** | Single server, no plan | Horizontal scaling possible | Auto-scaling with clear bottleneck plan |
| **Reliability** | Single points of failure | Basic redundancy | Fault-tolerant with graceful degradation |
| **Observability** | No monitoring | Basic metrics + logs | Full observability (metrics, traces, logs) |
| **Security** | No security design | Authentication + basic authorization | Defense in depth |
| **Data** | No backup strategy | Automated backups | Backup + tested restore + replication |
| **Documentation** | No diagrams | Architecture diagram | ADRs + diagrams + runbooks |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Feeds into** | api-design | Architecture informs API structure |
| **Feeds into** | database-schema | Architecture informs data model |
| **Feeds into** | auth-design | Architecture informs auth approach |
| **Review** | council-review (tech) | Validates architecture decisions |

---

## Output Checklist

- [ ] Architecture diagram with all components
- [ ] Key design decisions documented with rationale
- [ ] Non-functional requirements addressed (latency, availability, scale)
- [ ] Data flow documented
- [ ] Failure modes identified with mitigation
- [ ] Deployment strategy defined
- [ ] Migration path from current state (if applicable)
