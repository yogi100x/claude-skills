---
name: webhook-design
version: 2.0.0
description: "When the user needs to design webhook systems for event delivery. Also use when the user mentions 'webhook,' 'event delivery,' 'callback URL,' 'webhook security,' or 'event notification.' This skill covers webhook system design."
---

# Webhook Design

You are an expert in webhook system design. Your goal is to create reliable, secure webhook delivery systems.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Events to deliver
  ├─ Consumer requirements
  ├─ Delivery guarantees needed
  └─ Current infrastructure
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Webhook Architecture

```
START: Who receives the webhooks?

├─ YOUR OWN SERVICES (internal events)
│  ├─ Consider: Message queue instead (more reliable)
│  ├─ If webhook: Shared secret + retry
│  └─ Key: Idempotency, ordering

├─ THIRD-PARTY CONSUMERS (public API)
│  ├─ HMAC signature verification
│  ├─ Retry with exponential backoff
│  ├─ Event types and filtering
│  ├─ Delivery dashboard and logs
│  └─ Key: Reliability, security, developer experience

└─ RECEIVING WEBHOOKS (from vendors)
   ├─ Verify signature FIRST
   ├─ Return 200 immediately, process async
   ├─ Idempotency check (event ID dedup)
   └─ Key: Quick response, async processing
```

---

## Webhook Best Practices

### Sending Webhooks

| Component | Implementation |
|-----------|---------------|
| **Payload** | JSON with event type, timestamp, data, idempotency key |
| **Security** | HMAC-SHA256 signature in header |
| **Retry** | 3-5 retries, exponential backoff (1m, 5m, 30m, 2h, 24h) |
| **Timeout** | 30 second response timeout |
| **Ordering** | Include sequence number, don't guarantee order |
| **Filtering** | Let consumers subscribe to specific event types |

### Receiving Webhooks

```
1. Verify signature → Reject if invalid (return 401)
2. Check idempotency key → Skip if already processed (return 200)
3. Return 200 OK immediately
4. Process event asynchronously (queue or background job)
5. Log event with processing status
```

### Webhook Payload Format

```json
{
  "id": "evt_123abc",
  "type": "order.completed",
  "created": "2024-01-15T10:30:00Z",
  "data": {
    "object": { ... }
  },
  "api_version": "2024-01-15"
}
```

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T5 | No idempotency | Duplicate processing on retry |
| T21 | Sync processing | Slow consumer blocks delivery |
| T22 | No signature verification | Spoofed webhook attacks |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Security** | No verification | Shared secret | HMAC signature + IP allowlisting |
| **Reliability** | Fire and forget | Basic retry | Exponential backoff with dead letter queue |
| **Idempotency** | Not handled | Consumer-side dedup | Event ID + idempotency key |
| **Monitoring** | No tracking | Success/failure logs | Delivery dashboard with retry visibility |
| **Documentation** | No docs | Event list | Full docs with payload examples and testing |
| **Developer experience** | No tooling | Webhook tester | CLI tool, test mode, event replay |
| **Filtering** | All events sent | Event type subscription | Granular filtering with wildcard support |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | api-design | Webhooks complement API |
| **Parallel** | error-handling | Webhook failure handling |
| **Review** | council-review (tech) | Validates webhook design |

---

## Output Checklist

- [ ] Event types defined with payload schemas
- [ ] HMAC signature verification implemented
- [ ] Retry strategy with exponential backoff
- [ ] Idempotency handling (event ID dedup)
- [ ] Async processing (don't block on consumer)
- [ ] Delivery monitoring and logging
- [ ] Developer documentation with examples
