---
name: error-handling
version: 2.0.0
description: "When the user needs to design error handling strategies for applications. Also use when the user mentions 'error handling,' 'exception handling,' 'error boundaries,' 'retry strategy,' 'graceful degradation,' or 'error reporting.' This skill covers application error handling."
---

# Error Handling

You are an expert in application error handling design. Your goal is to create error handling systems that are informative, recoverable, and don't leak sensitive information.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Application architecture
  ├─ Error tracking tools (Sentry, etc.)
  ├─ User-facing error requirements
  └─ Recovery requirements
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Error Handling Strategy

```
START: Where does the error occur?

├─ CLIENT-SIDE (React/browser)
│  ├─ Error boundaries for component failures
│  ├─ try/catch for async operations
│  ├─ User-friendly error messages
│  └─ Report to error tracking (Sentry)

├─ API LAYER (request handling)
│  ├─ Structured error responses (code, message, details)
│  ├─ Input validation errors → 400 with field-level details
│  ├─ Auth errors → 401/403 (no information leakage)
│  └─ Server errors → 500 with correlation ID

├─ BACKGROUND JOBS
│  ├─ Retry with exponential backoff
│  ├─ Dead letter queue for persistent failures
│  ├─ Alert on repeated failures
│  └─ Idempotent retry (no duplicate side effects)

└─ EXTERNAL SERVICES (APIs, databases)
   ├─ Circuit breaker pattern
   ├─ Timeout on every call
   ├─ Fallback/graceful degradation
   └─ Retry with jitter for transient errors
```

---

## Error Response Format

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input",
    "details": [
      { "field": "email", "message": "Invalid email format" }
    ],
    "correlation_id": "req_abc123"
  }
}
```

### Error Categories

| Category | HTTP Status | Retry? | User Action |
|----------|------------|--------|-------------|
| **Validation** | 400 | No | Fix input and retry |
| **Authentication** | 401 | No | Login again |
| **Authorization** | 403 | No | Contact admin |
| **Not Found** | 404 | No | Check URL |
| **Rate Limited** | 429 | Yes (after delay) | Wait and retry |
| **Server Error** | 500 | Yes | Automatic retry or report |
| **Service Unavailable** | 503 | Yes (with backoff) | Wait and retry |

### Resilience Patterns

| Pattern | When to Use | Implementation |
|---------|-------------|----------------|
| **Retry** | Transient failures | Exponential backoff with jitter |
| **Circuit breaker** | Persistent failures | Open after N failures, half-open to test |
| **Timeout** | Slow dependencies | Absolute timeout on every external call |
| **Fallback** | Non-critical features | Graceful degradation with cached/default data |
| **Bulkhead** | Isolation | Separate thread pools per dependency |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T24 | Swallowing errors | Silent failures, debugging nightmare |
| T25 | Leaking stack traces | Security vulnerability |
| T26 | No correlation IDs | Can't trace errors across services |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **User messages** | Technical errors shown | Friendly messages | Contextual + actionable messages |
| **API responses** | Inconsistent format | Structured errors | Typed errors with correlation IDs |
| **Logging** | No error logging | Logged to console | Structured logs with context to error tracker |
| **Recovery** | Manual restart | Basic retry | Automatic recovery with fallbacks |
| **Monitoring** | No tracking | Error count alerts | Error budget tracking with trending |
| **Security** | Stack traces exposed | Generic messages | Sanitized with safe error codes |
| **Testing** | Happy path only | Some error cases | Comprehensive error scenario testing |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Parallel** | monitoring-setup | Errors feed monitoring |
| **Parallel** | background-job-design | Job retry/failure handling |
| **Review** | council-review (tech) | Validates error handling |

---

## Output Checklist

- [ ] Error response format standardized across all endpoints
- [ ] Client-side error boundaries in place
- [ ] Correlation IDs for tracing across services
- [ ] Retry strategy for transient failures
- [ ] Circuit breakers for external dependencies
- [ ] No sensitive information in error responses
- [ ] Error tracking configured (Sentry or equivalent)
