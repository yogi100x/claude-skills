---
name: background-job-design
version: 2.0.0
description: "When the user needs to design background job systems for async processing. Also use when the user mentions 'background jobs,' 'async processing,' 'job queue,' 'worker,' 'cron jobs,' or 'task queue.' This skill covers background job architecture."
---

# Background Job Design

You are an expert in background job system design. Your goal is to design reliable, observable async processing systems.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Current job infrastructure (Trigger.dev, Bull, SQS, etc.)
  ├─ Job types and volumes
  ├─ Latency requirements
  └─ Failure handling needs
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Job Architecture

```
START: What type of background work?

├─ FIRE AND FORGET (email, notification, logging)
│  ├─ Simple queue with basic retry
│  ├─ No result needed by caller
│  └─ Key: At-least-once delivery, idempotent handlers

├─ REQUEST-RESPONSE (grading, processing, generation)
│  ├─ Job with status tracking and result storage
│  ├─ Progress updates via WebSocket/polling
│  └─ Key: Status endpoint, timeout handling

├─ SCHEDULED (daily reports, cleanup, sync)
│  ├─ Cron-based scheduling
│  ├─ Distributed lock to prevent duplicates
│  └─ Key: Idempotent, monitoring for missed runs

├─ PIPELINE (multi-step processing)
│  ├─ Step functions / workflow engine
│  ├─ Each step idempotent and retryable
│  └─ Key: State management, partial failure handling

└─ FAN-OUT (parallel processing)
   ├─ Parent job spawns N child jobs
   ├─ Aggregation when all children complete
   └─ Key: Concurrency limits, partial results
```

---

## Job Design Principles

| Principle | Implementation |
|-----------|---------------|
| **Idempotent** | Same input → same result, safe to retry |
| **Observable** | Status, progress, duration, error tracking |
| **Bounded** | Timeout on every job, max retries |
| **Isolated** | One job failure doesn't affect others |
| **Prioritized** | Critical jobs processed before background |

### Job Lifecycle

```
Created → Queued → Running → Completed/Failed
                      ↓
                  Retrying (with backoff)
                      ↓
                  Dead Letter Queue (max retries exceeded)
```

### Retry Strategy

| Attempt | Delay | Total Wait |
|---------|-------|-----------|
| 1 | 10 seconds | 10s |
| 2 | 1 minute | 1m 10s |
| 3 | 10 minutes | 11m 10s |
| 4 | 1 hour | 1h 11m |
| 5 | Dead letter queue | — |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T3 | Synchronous everything | User waits for slow operations |
| T5 | No idempotency | Duplicate processing on retry |
| T23 | No timeout | Zombie jobs consuming resources |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Idempotency** | Not idempotent | Most jobs idempotent | All jobs provably idempotent |
| **Observability** | No tracking | Status and logs | Progress, duration, metrics dashboard |
| **Retry strategy** | No retry | Fixed retry | Exponential backoff with DLQ |
| **Concurrency** | Unlimited | Global limit | Per-job-type limits with priority |
| **Error handling** | Silent failure | Logged errors | Alerts + DLQ + manual retry UI |
| **Testing** | Not tested | Unit tests | Integration tests with real queue |
| **Documentation** | No docs | Job list | Full docs with flow diagrams |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | system-architecture | Architecture determines job infrastructure |
| **Parallel** | monitoring-setup | Monitor job health |
| **Parallel** | error-handling | Job error handling strategy |
| **Review** | council-review (tech) | Validates job design |

---

## Output Checklist

- [ ] Job types classified (fire-and-forget, request-response, scheduled, pipeline)
- [ ] Each job is idempotent (safe to retry)
- [ ] Retry strategy with exponential backoff
- [ ] Concurrency limits set per job type
- [ ] Timeout on every job
- [ ] Dead letter queue for failed jobs
- [ ] Monitoring dashboard for job health
