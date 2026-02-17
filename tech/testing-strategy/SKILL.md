---
name: testing-strategy
version: 2.0.0
description: "When the user needs to design a testing strategy for an application. Also use when the user mentions 'testing strategy,' 'test pyramid,' 'unit tests,' 'integration tests,' 'E2E tests,' or 'test coverage.' This skill covers testing approach design."
---

# Testing Strategy

You are an expert in software testing strategy. Your goal is to design testing approaches that maximize confidence while minimizing maintenance burden.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Application architecture
  ├─ Current test coverage
  ├─ Testing tools and frameworks
  └─ CI/CD pipeline
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Testing Approach

```
START: What are you testing?

├─ BUSINESS LOGIC (pure functions, calculations)
│  ├─ Unit tests (fast, isolated)
│  ├─ Property-based testing for edge cases
│  └─ Coverage target: 90%+ for critical paths

├─ API ENDPOINTS (request/response)
│  ├─ Integration tests with real database
│  ├─ Test auth, validation, happy + error paths
│  └─ Coverage: All endpoints, all error codes

├─ UI COMPONENTS (React, etc.)
│  ├─ Component tests (Testing Library)
│  ├─ Visual regression tests (optional)
│  └─ Focus: User interactions, not implementation

├─ USER FLOWS (end-to-end)
│  ├─ E2E tests (Playwright)
│  ├─ Critical paths only (signup, purchase, core flow)
│  └─ Keep minimal: 10-20 tests max

└─ INFRASTRUCTURE (deployment, scaling)
   ├─ Smoke tests post-deploy
   ├─ Health check endpoints
   └─ Synthetic monitoring
```

---

## Test Pyramid

```
         /  E2E  \          ← Few, slow, high confidence
        / Integration \      ← Medium, test boundaries
       /   Unit Tests   \    ← Many, fast, focused
```

| Layer | Count | Speed | Scope | Tools |
|-------|-------|-------|-------|-------|
| **Unit** | Hundreds | ms each | Single function/module | Vitest, Jest |
| **Integration** | Dozens | seconds each | API + DB, service boundaries | Vitest + test DB |
| **E2E** | 10-20 | minutes each | Full user flows | Playwright |

### What to Test

| Always Test | Sometimes Test | Rarely Test |
|-------------|---------------|-------------|
| Business logic | UI components | CSS styling |
| Auth flows | Error messages | Third-party libraries |
| Data validation | Edge cases | Framework behavior |
| API contracts | Performance | Implementation details |
| Critical user paths | Accessibility | Internal state |

### What NOT to Test

- Framework behavior (React rendering, Next.js routing)
- Third-party library internals
- Implementation details (internal state, private methods)
- Trivial code (simple getters, pass-through functions)
- Generated code (types, migrations)

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T15 | No tests | Bugs in production |
| T27 | Testing implementation details | Brittle tests that break on refactor |
| T28 | Too many E2E tests | Slow CI, flaky tests |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Coverage** | No tests | Critical paths covered | Comprehensive with pyramid balance |
| **Speed** | >10 min suite | 3-10 min | <3 min (unit + integration) |
| **Reliability** | Flaky tests | Mostly stable | Zero flaky tests |
| **Maintenance** | Tests break on refactor | Some coupling | Tests only break on behavior change |
| **CI integration** | Tests not in CI | Tests run on PR | Tests block merge, results visible |
| **Documentation** | No test docs | README | Test patterns documented, examples |
| **Data management** | Shared test data | Fixtures | Factory-based, isolated per test |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Parallel** | ci-cd-pipeline | Tests run in CI |
| **Parallel** | error-handling | Error cases need tests |
| **Review** | council-review (tech) | Validates testing approach |

---

## Output Checklist

- [ ] Test pyramid balance defined (many unit, fewer integration, minimal E2E)
- [ ] Critical paths identified and tested
- [ ] Test tools selected and configured
- [ ] Tests run in CI before merge
- [ ] Test data strategy (factories, fixtures)
- [ ] Flaky test policy (fix or delete)
- [ ] Coverage targets set (realistic, not 100%)
