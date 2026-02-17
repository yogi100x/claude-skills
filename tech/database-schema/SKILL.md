---
name: database-schema
version: 2.0.0
description: "When the user needs to design database schemas, tables, or data models. Also use when the user mentions 'database schema,' 'data model,' 'table design,' 'migration,' 'normalization,' or 'entity relationship.' This skill covers database schema design."
---

# Database Schema Design

You are an expert in database schema design. Your goal is to create schemas that are normalized, performant, and evolvable.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Database engine (PostgreSQL, MySQL, etc.)
  ├─ ORM or query builder
  ├─ Access patterns (read-heavy, write-heavy)
  └─ Scale expectations
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Schema Approach

```
START: What's the primary access pattern?

├─ TRANSACTIONAL (CRUD, business logic)
│  ├─ Normalized schema (3NF)
│  ├─ Foreign keys with referential integrity
│  ├─ Indexes on query patterns
│  └─ Key: Consistency over read speed

├─ READ-HEAVY (dashboards, reporting)
│  ├─ Denormalize for common queries
│  ├─ Materialized views for aggregations
│  ├─ Indexes optimized for read patterns
│  └─ Key: Read speed over write complexity

├─ FLEXIBLE SCHEMA (varying attributes)
│  ├─ JSONB columns for variable data
│  ├─ EAV pattern for truly dynamic attributes
│  └─ Key: Query-ability of flexible data

└─ TIME-SERIES (events, logs, metrics)
   ├─ Partitioned by time
   ├─ Append-only with retention policy
   └─ Key: Write throughput, range queries
```

---

## Schema Design Principles

| Principle | Implementation |
|-----------|---------------|
| **Normalize first** | 3NF baseline, denormalize with evidence |
| **Explicit relationships** | Foreign keys with ON DELETE/UPDATE actions |
| **Appropriate types** | Use UUID for IDs, timestamptz for dates, JSONB for flexible data |
| **Index strategy** | Index based on actual query patterns, not guesses |
| **Soft deletes** | `deleted_at` timestamp, filter in application |
| **Audit columns** | `created_at`, `updated_at` on every table |
| **Enum vs lookup table** | Postgres ENUM for <10 stable values; lookup table for dynamic |

### Common Patterns

| Pattern | When to Use | Implementation |
|---------|-------------|----------------|
| **UUID primary keys** | Distributed systems, API exposure | `gen_random_uuid()` |
| **Polymorphic relations** | Multiple types share a table | `type` column + JSONB or separate tables |
| **Temporal tables** | Track changes over time | `valid_from`/`valid_to` columns |
| **Row-level security** | Multi-tenant, per-user access | RLS policies on tenant_id/user_id |
| **JSONB columns** | Semi-structured data, metadata | Indexed with GIN for queries |

### Migration Best Practices

| Rule | Reason |
|------|--------|
| Migrations are forward-only | Never modify past migrations |
| One concern per migration | Easier to debug and rollback |
| Backward-compatible changes | Deploy migration before code that uses it |
| Test with production-like data | Small datasets hide performance issues |
| Include rollback plan | Document how to undo each migration |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T7 | No foreign keys | Data integrity violations |
| T8 | Missing indexes | Slow queries at scale |
| T9 | VARCHAR for everything | Type safety lost, storage waste |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Normalization** | Flat tables | Partially normalized | 3NF with intentional denormalization |
| **Integrity** | No constraints | Some foreign keys | FK + check constraints + triggers |
| **Indexing** | No indexes | Primary key only | Query-pattern-driven indexes |
| **Types** | VARCHAR everything | Appropriate types | Optimized types with constraints |
| **Migrations** | Ad hoc DDL | Sequential migrations | Tested, backward-compatible, documented |
| **Security** | No RLS | Basic RLS | Comprehensive RLS per entity |
| **Documentation** | No ERD | Basic ERD | ERD + data dictionary + access patterns |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | system-architecture | Architecture determines data model |
| **Feeds into** | data-migration | Schema changes require migrations |
| **Parallel** | auth-design | Auth informs RLS and ownership |
| **Review** | council-review (tech) | Validates schema design |

---

## Output Checklist

- [ ] Entity-relationship diagram created
- [ ] Tables normalized to 3NF (denormalization justified)
- [ ] Foreign keys with appropriate ON DELETE actions
- [ ] Indexes aligned with query patterns
- [ ] Audit columns on all tables (created_at, updated_at)
- [ ] RLS policies designed (if multi-tenant)
- [ ] Migration plan with rollback strategy
