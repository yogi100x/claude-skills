---
name: api-design
version: 2.0.0
description: "When the user needs to design REST, GraphQL, or gRPC APIs. Also use when the user mentions 'API design,' 'REST API,' 'endpoint design,' 'API versioning,' 'API documentation,' or 'OpenAPI spec.' This skill covers API design best practices."
---

# API Design

You are an expert in API design. Your goal is to create APIs that are intuitive, consistent, and maintainable.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ API consumers (web, mobile, third-party)
  ├─ Authentication requirements
  ├─ Current API conventions
  └─ Performance requirements
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: API Style

```
START: Who consumes the API?

├─ WEB/MOBILE APP (first-party) → REST or tRPC
│  ├─ Simple CRUD? → REST with JSON
│  ├─ Complex queries? → GraphQL or REST with query params
│  └─ TypeScript full-stack? → tRPC for end-to-end type safety

├─ THIRD-PARTY DEVELOPERS → REST with OpenAPI
│  ├─ Public API? → REST, versioned, well-documented
│  ├─ Webhooks for events
│  └─ Rate limiting, API keys, OAuth2

├─ SERVICE-TO-SERVICE → gRPC or REST
│  ├─ High performance? → gRPC with protobuf
│  ├─ Simple integration? → REST
│  └─ Event-driven? → Message queue instead

└─ REAL-TIME → WebSocket or SSE
   ├─ Bidirectional? → WebSocket
   ├─ Server push only? → SSE
   └─ Both REST + real-time? → REST for CRUD, WebSocket for updates
```

---

## REST API Conventions

### URL Structure
```
GET    /api/v1/resources          → List (with pagination)
GET    /api/v1/resources/:id      → Get single
POST   /api/v1/resources          → Create
PATCH  /api/v1/resources/:id      → Partial update
DELETE /api/v1/resources/:id      → Delete

GET    /api/v1/resources/:id/sub  → Nested resources
POST   /api/v1/resources/:id/actions/verb → Actions
```

### Response Format
```json
{
  "data": { ... },
  "meta": { "page": 1, "total": 100 },
  "error": null
}
```

### Status Codes

| Code | Meaning | When |
|------|---------|------|
| 200 | OK | Successful GET, PATCH |
| 201 | Created | Successful POST |
| 204 | No Content | Successful DELETE |
| 400 | Bad Request | Validation error |
| 401 | Unauthorized | Not authenticated |
| 403 | Forbidden | Not authorized |
| 404 | Not Found | Resource doesn't exist |
| 409 | Conflict | Duplicate, version conflict |
| 422 | Unprocessable | Semantically invalid |
| 429 | Too Many Requests | Rate limited |
| 500 | Internal Error | Server bug |

### Pagination

```
GET /api/v1/resources?page=1&per_page=20
GET /api/v1/resources?cursor=abc123&limit=20  (cursor-based, preferred)
```

### Filtering & Sorting
```
GET /api/v1/resources?status=active&sort=-created_at
GET /api/v1/resources?filter[status]=active&filter[type]=premium
```

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T4 | No API versioning | Breaking changes break clients |
| T5 | No idempotency | Duplicate requests cause duplicate actions |
| T6 | Inconsistent naming | Confusing for API consumers |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Consistency** | Mixed conventions | Mostly consistent | Fully consistent naming, responses, errors |
| **Documentation** | No docs | Basic docs | OpenAPI spec with examples |
| **Error handling** | Generic 500s | Status codes + messages | Structured errors with codes, hints |
| **Versioning** | No versioning | URL versioning | Versioned with deprecation policy |
| **Security** | No auth | API keys | OAuth2 + rate limiting + CORS |
| **Performance** | No pagination | Basic pagination | Cursor pagination + field selection |
| **Idempotency** | Not considered | On some endpoints | Idempotency keys on all mutations |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | system-architecture | Architecture informs API design |
| **Feeds into** | webhook-design | API events trigger webhooks |
| **Feeds into** | documentation | API docs are primary documentation |
| **Review** | council-review (tech) | Validates API design |

---

## Output Checklist

- [ ] API style chosen with rationale
- [ ] Endpoints follow consistent naming convention
- [ ] Authentication and authorization designed
- [ ] Error responses are structured and informative
- [ ] Pagination implemented for list endpoints
- [ ] Versioning strategy defined
- [ ] Rate limiting configured
- [ ] OpenAPI spec generated (if REST)
