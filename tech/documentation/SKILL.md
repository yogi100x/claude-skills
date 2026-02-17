---
name: documentation
version: 2.0.0
description: "When the user needs to create technical documentation for APIs, systems, or processes. Also use when the user mentions 'documentation,' 'API docs,' 'README,' 'developer guide,' 'architecture docs,' or 'runbook.' This skill covers technical documentation."
---

# Documentation

You are an expert in technical documentation. Your goal is to create documentation that developers actually read and maintain.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Documentation tools and hosting
  ├─ Target audience
  ├─ Existing documentation
  └─ Documentation gaps
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Documentation Type

```
START: Who is the audience?

├─ NEW DEVELOPERS (onboarding)
│  ├─ Getting Started guide
│  ├─ Architecture overview
│  ├─ Development setup (copy-pasteable commands)
│  └─ Key: Works on first try, no assumed knowledge

├─ API CONSUMERS (external developers)
│  ├─ API reference (auto-generated from spec)
│  ├─ Quick start guide
│  ├─ Code examples in multiple languages
│  └─ Key: Working examples, authentication guide

├─ TEAM (internal reference)
│  ├─ Architecture Decision Records (ADRs)
│  ├─ Runbooks for operations
│  ├─ Incident response playbooks
│  └─ Key: Findable, up-to-date, actionable

└─ USERS (product documentation)
   ├─ How-to guides (task-oriented)
   ├─ Tutorials (learning-oriented)
   ├─ Reference (information-oriented)
   └─ Key: Task-focused, searchable
```

---

## Documentation Framework (Diátaxis)

| Type | Purpose | Structure |
|------|---------|-----------|
| **Tutorial** | Learning | Step-by-step, building something real |
| **How-to** | Problem-solving | Specific task, assumes knowledge |
| **Reference** | Information | Accurate, complete, structured |
| **Explanation** | Understanding | Context, background, concepts |

### README Template

```markdown
# Project Name
One-line description.

## Quick Start
[Copy-pasteable commands to get running]

## Architecture
[High-level diagram and description]

## Development
[Setup, commands, workflow]

## Deployment
[How to deploy]

## Contributing
[How to contribute]
```

### ADR (Architecture Decision Record) Template

```markdown
# ADR-NNN: [Decision Title]
**Status:** Proposed / Accepted / Deprecated
**Date:** YYYY-MM-DD
**Context:** [Why we need to make this decision]
**Decision:** [What we decided]
**Consequences:** [What changes as a result]
```

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T29 | No documentation | Tribal knowledge, onboarding bottleneck |
| T30 | Outdated documentation | Worse than no docs (misleading) |
| T31 | Documentation not near code | Never found, never updated |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Completeness** | Missing key docs | Major topics covered | Comprehensive per Diátaxis |
| **Accuracy** | Outdated | Mostly current | Verified with CI checks |
| **Findability** | Random files | Organized structure | Searchable, linked, indexed |
| **Examples** | No examples | Some examples | Working, copy-pasteable examples |
| **Maintenance** | Never updated | Updated occasionally | Updated on every change, reviewed quarterly |
| **Onboarding** | No getting started | Basic setup | New dev productive in <1 day |
| **API docs** | No docs | Basic endpoint list | Auto-generated with examples |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | api-design | API spec generates reference docs |
| **Parallel** | code-review-checklist | Docs reviewed with code |
| **Review** | council-review (tech) | Validates documentation |

---

## Output Checklist

- [ ] README with quick start (works on first try)
- [ ] Architecture overview with diagram
- [ ] API documentation (auto-generated if possible)
- [ ] Development setup guide
- [ ] Key ADRs documented
- [ ] Runbooks for operational tasks
- [ ] Documentation is near the code it describes
