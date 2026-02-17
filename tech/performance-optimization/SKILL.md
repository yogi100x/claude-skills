---
name: performance-optimization
version: 2.0.0
description: "When the user needs to optimize application performance, reduce latency, or improve throughput. Also use when the user mentions 'performance,' 'optimization,' 'slow page,' 'latency,' 'Core Web Vitals,' or 'load time.' This skill covers web application performance."
---

# Performance Optimization

You are an expert in web application performance optimization. Your goal is to systematically identify and fix performance bottlenecks.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Application architecture
  ├─ Current performance metrics
  ├─ Performance targets/SLAs
  └─ User-reported issues
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Optimization Target

```
START: Where is the bottleneck?

├─ FRONTEND (slow page load, poor CWV)
│  ├─ Bundle size analysis (next/bundle-analyzer)
│  ├─ Image optimization (next/image, WebP, AVIF)
│  ├─ Code splitting and lazy loading
│  └─ Measure: LCP, FID/INP, CLS

├─ BACKEND (slow API responses)
│  ├─ Database query optimization (EXPLAIN ANALYZE)
│  ├─ Caching strategy (Redis, CDN, in-memory)
│  ├─ N+1 query detection
│  └─ Measure: p50, p95, p99 response time

├─ DATABASE (slow queries, connection issues)
│  ├─ Index optimization
│  ├─ Query rewriting
│  ├─ Connection pooling
│  └─ Measure: Query time, connection count

└─ INFRASTRUCTURE (capacity, scaling)
   ├─ Horizontal scaling
   ├─ CDN for static assets
   ├─ Edge computing for global users
   └─ Measure: CPU/memory utilization, throughput
```

---

## Optimization Priorities

Always measure first, then optimize in this order:

| Priority | Action | Typical Impact |
|----------|--------|---------------|
| 1. **Eliminate** | Remove unnecessary work | Highest |
| 2. **Cache** | Don't repeat expensive work | High |
| 3. **Defer** | Move work off critical path | Medium |
| 4. **Parallelize** | Do work concurrently | Medium |
| 5. **Optimize** | Make work faster | Low-Medium |

### Common Quick Wins

| Area | Fix | Impact |
|------|-----|--------|
| Images | Next/Image, lazy loading, proper sizing | LCP -50% |
| JavaScript | Code splitting, tree shaking, dynamic imports | TTI -30% |
| Database | Add missing index | Query time -90% |
| API | Add Redis cache for hot data | Response time -80% |
| Fonts | Display: swap, preload, self-host | CLS improvement |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T2 | No caching strategy | Repeated expensive operations |
| T8 | Missing indexes | Full table scans |
| T18 | Premature optimization | Wasted effort on non-bottlenecks |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Measurement** | No metrics | Basic timing | Full performance budget with monitoring |
| **Frontend** | No optimization | Images + code split | CWV green, optimal bundle |
| **Backend** | No profiling | Identified slow endpoints | All endpoints within SLA |
| **Database** | No query analysis | Major queries optimized | Query plan review, all indexed |
| **Caching** | No caching | Some caching | Multi-level cache strategy |
| **Testing** | No load testing | Manual testing | Automated load testing in CI |
| **Monitoring** | No tracking | Alerting on degradation | Performance budgets with regression alerts |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | monitoring-setup | Monitoring identifies bottlenecks |
| **Parallel** | database-schema | Schema affects query performance |
| **Review** | council-review (tech) | Validates optimization approach |

---

## Output Checklist

- [ ] Performance baseline measured before optimization
- [ ] Bottleneck identified with profiling data
- [ ] Optimization approach chosen (eliminate > cache > defer > parallelize > optimize)
- [ ] Change implemented with minimal side effects
- [ ] Performance improvement measured after change
- [ ] Regression protection in place (performance budget/alerts)
