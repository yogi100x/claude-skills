---
name: code-review-checklist
version: 2.0.0
description: "When the user needs a code review checklist or wants to improve code review practices. Also use when the user mentions 'code review,' 'PR review,' 'review checklist,' 'code quality,' or 'review process.' This skill covers code review best practices."
---

# Code Review Checklist

You are an expert in code review practices. Your goal is to help teams conduct effective, efficient code reviews that catch real issues without becoming bottlenecks.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Team size and review process
  ├─ Code standards and conventions
  ├─ Common issue patterns
  └─ CI/CD checks available
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Review Focus

```
START: What type of change?

├─ NEW FEATURE
│  ├─ Architecture: Does it fit the existing patterns?
│  ├─ Tests: Are critical paths tested?
│  ├─ Security: Any new attack surfaces?
│  └─ Key: Design before implementation details

├─ BUG FIX
│  ├─ Root cause: Is the actual cause fixed (not symptom)?
│  ├─ Test: Is there a test that would have caught this?
│  ├─ Scope: Does the fix have unintended side effects?
│  └─ Key: Regression test included

├─ REFACTORING
│  ├─ Behavior: Is behavior preserved? (tests pass)
│  ├─ Scope: Is it focused (not mixed with features)?
│  └─ Key: No behavior changes, only structural

├─ DEPENDENCY UPDATE
│  ├─ Breaking changes: Are API changes handled?
│  ├─ Security: Is this a security update?
│  └─ Key: Changelog reviewed, tests pass

└─ CONFIGURATION
   ├─ Secrets: No hardcoded secrets?
   ├─ Environment: Works in all environments?
   └─ Key: Tested in staging
```

---

## Review Checklist

### Always Check (Every PR)

| Category | Checks |
|----------|--------|
| **Correctness** | Does it do what it claims? Edge cases handled? |
| **Security** | Input validation, auth checks, no secrets in code |
| **Testing** | New tests for new behavior, existing tests pass |
| **Naming** | Clear, consistent, follows conventions |
| **Error handling** | Errors caught, user-friendly messages, logged |
| **Performance** | No N+1 queries, unnecessary re-renders, missing indexes |

### Sometimes Check (Large PRs, New Patterns)

| Category | Checks |
|----------|--------|
| **Architecture** | Fits existing patterns, appropriate abstraction level |
| **Types** | TypeScript types correct, no `any` |
| **Accessibility** | ARIA labels, keyboard navigation, color contrast |
| **Documentation** | Comments for non-obvious logic, README updates |

### Review Etiquette

| Do | Don't |
|----|-------|
| Ask questions, don't make demands | "This is wrong" — instead "Why this approach over X?" |
| Distinguish nitpicks from blockers | Block on style preferences |
| Approve with minor suggestions | Hold approval for non-blocking feedback |
| Review within 24 hours | Let PRs sit for days |
| Focus on the code, not the person | Make it personal |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T32 | Rubber-stamp reviews | Bugs and security issues missed |
| T33 | Blocking on style | Slow velocity, team frustration |
| T34 | Review too late | Expensive rework |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Thoroughness** | Rubber stamp | Standard checklist | Contextual review per change type |
| **Speed** | Days to review | Within 24 hours | Within 4 hours |
| **Feedback quality** | Vague comments | Specific suggestions | Actionable with alternatives |
| **Security focus** | Not checked | Basic review | Systematic security review |
| **Consistency** | Reviewer-dependent | Checklist used | Automated + human review |
| **Knowledge sharing** | No context | Comments explain why | Reviews teach and improve team |
| **Automation** | All manual | Linting in CI | Automated checks + focused human review |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Parallel** | testing-strategy | Tests validate PR correctness |
| **Parallel** | documentation | Doc updates reviewed with code |
| **Review** | council-review (tech) | Meta-review of review process |

---

## Output Checklist

- [ ] Review checklist defined and accessible to team
- [ ] Review expectations set (turnaround time, blocking criteria)
- [ ] Automated checks handle style/formatting
- [ ] Human review focuses on logic, security, architecture
- [ ] Review feedback is constructive and actionable
- [ ] Process periodically reviewed and improved
