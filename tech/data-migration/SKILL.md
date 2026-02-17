---
name: data-migration
version: 2.0.0
description: "When the user needs to migrate data between systems, schemas, or databases. Also use when the user mentions 'data migration,' 'database migration,' 'schema migration,' 'data transfer,' or 'ETL.' This skill covers data migration planning."
---

# Data Migration

You are an expert in data migration. Your goal is to plan and execute data migrations that are safe, complete, and reversible.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Source and target systems
  ├─ Data volumes and types
  ├─ Downtime tolerance
  └─ Rollback requirements
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Migration Strategy

```
START: What kind of migration?

├─ SCHEMA MIGRATION (same DB, new structure)
│  ├─ Backward-compatible: Add column → migrate data → remove old
│  ├─ Zero-downtime: expand-contract pattern
│  └─ Key: Never break running application

├─ DATABASE MIGRATION (different DB engine)
│  ├─ Dual-write during transition
│  ├─ Shadow reads for validation
│  ├─ Gradual traffic shift
│  └─ Key: Data consistency verification

├─ SYSTEM MIGRATION (new service/vendor)
│  ├─ API adapter pattern
│  ├─ Feature flag for gradual rollout
│  ├─ Parallel running for validation
│  └─ Key: Rollback capability at every step

└─ DATA IMPORT (one-time bulk load)
   ├─ Validate → Transform → Load → Verify
   ├─ Idempotent processing (rerun safe)
   └─ Key: Data quality checks, error handling
```

---

## Migration Phases

| Phase | Activities | Gate |
|-------|-----------|------|
| **Plan** | Map source to target, identify transformations, estimate size | Plan reviewed |
| **Prepare** | Create scripts, set up staging, define validation | Scripts tested |
| **Test** | Run on staging with production-like data | All validations pass |
| **Execute** | Run migration with monitoring | Data verified |
| **Validate** | Row counts, checksums, spot checks, functional tests | Validation complete |
| **Cleanup** | Remove old data/schema, update documentation | Cleanup complete |

### Expand-Contract Pattern (Zero-Downtime)

```
Phase 1: EXPAND — Add new column/table (backward compatible)
Phase 2: MIGRATE — Copy data, dual-write to old + new
Phase 3: SWITCH — Application reads from new
Phase 4: CONTRACT — Remove old column/table
```

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T19 | Big bang migration | All-or-nothing risk |
| T20 | No rollback plan | Can't undo failed migration |
| T7 | No validation | Data corruption goes undetected |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Planning** | Ad hoc | Written plan | Detailed plan with rollback at each step |
| **Testing** | Tested in production | Tested on staging | Production-like data, tested multiple times |
| **Validation** | Visual spot check | Row counts match | Checksums + functional tests + edge cases |
| **Rollback** | No rollback | Manual rollback | Automated rollback with triggers |
| **Downtime** | Extended downtime | Scheduled maintenance | Zero downtime |
| **Monitoring** | No monitoring | Basic logging | Real-time progress + error tracking |
| **Communication** | No notification | Team informed | Stakeholders notified with status updates |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | database-schema | Schema changes trigger migrations |
| **Parallel** | monitoring-setup | Monitor migration progress |
| **Review** | council-review (tech) | Validates migration plan |

---

## Output Checklist

- [ ] Source-to-target mapping documented
- [ ] Data transformations specified
- [ ] Migration scripts written and tested on staging
- [ ] Validation criteria defined (row counts, checksums)
- [ ] Rollback plan documented and tested
- [ ] Communication plan for stakeholders
- [ ] Post-migration cleanup scheduled
