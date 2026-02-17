---
name: ci-cd-pipeline
version: 2.0.0
description: "When the user needs to set up or improve CI/CD pipelines. Also use when the user mentions 'CI/CD,' 'continuous integration,' 'deployment pipeline,' 'GitHub Actions,' 'build automation,' or 'deploy process.' This skill covers CI/CD pipeline design."
---

# CI/CD Pipeline

You are an expert in CI/CD pipeline design. Your goal is to create fast, reliable, and secure deployment pipelines.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Source control and branching strategy
  ├─ Current CI/CD tools
  ├─ Deployment targets (Vercel, AWS, etc.)
  └─ Test infrastructure
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Pipeline Design

```
START: What's your deployment target?

├─ SERVERLESS/EDGE (Vercel, Cloudflare, Netlify)
│  ├─ Git push → automatic preview + production deploy
│  ├─ CI: Lint, type-check, test in GitHub Actions
│  └─ Key: Fast builds, preview deployments, rollback

├─ CONTAINERS (Docker, K8s, ECS)
│  ├─ Build → Test → Image → Registry → Deploy
│  ├─ Multi-stage Docker builds
│  └─ Key: Image size, registry management, health checks

├─ TRADITIONAL (VPS, bare metal)
│  ├─ Build → Test → rsync/scp → restart
│  └─ Key: Zero-downtime deploy, blue-green or rolling

└─ MONOREPO (multiple apps)
   ├─ Affected-only builds (Turborepo, Nx)
   ├─ Parallel pipelines per app
   └─ Key: Cache efficiency, dependency graph
```

---

## Pipeline Stages

| Stage | What | Speed Target | Fail Action |
|-------|------|-------------|-------------|
| **Lint** | Code style, formatting | <30s | Block merge |
| **Type check** | TypeScript compilation | <60s | Block merge |
| **Unit tests** | Business logic | <2min | Block merge |
| **Integration tests** | API, database | <5min | Block merge |
| **Build** | Production build | <3min | Block merge |
| **E2E tests** | Full user flows | <10min | Block merge (or warn) |
| **Preview deploy** | Staging environment | <3min | Warn |
| **Production deploy** | Live environment | <3min | Manual rollback ready |

### Speed Optimization

| Technique | Impact |
|-----------|--------|
| **Caching** | Cache node_modules, build artifacts, Turbo cache |
| **Parallelization** | Run lint, type-check, tests in parallel |
| **Affected-only** | Only build/test changed packages |
| **Incremental builds** | TypeScript incremental, Next.js caching |
| **Skip redundant** | Skip E2E for docs-only changes |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T14 | No CI/CD | Manual, error-prone deployments |
| T15 | Tests in production | Breaking changes discovered by users |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Automation** | Manual deploy | CI builds, manual deploy | Full CI/CD with automated deploy |
| **Speed** | >30 min pipeline | 10-30 min | <10 min total |
| **Testing** | No tests in pipeline | Unit + integration | Unit + integration + E2E |
| **Rollback** | Manual restoration | Documented process | One-click/auto rollback |
| **Security** | Secrets in code | Env vars | Secrets manager + least privilege |
| **Environments** | Only production | Staging + production | Preview + staging + production |
| **Monitoring** | No deploy tracking | Deploy notifications | Deploy metrics + error rate correlation |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Feeds into** | monitoring-setup | Monitoring detects deploy issues |
| **Parallel** | testing-strategy | Tests run in pipeline |
| **Review** | council-review (tech) | Validates pipeline design |

---

## Output Checklist

- [ ] Pipeline stages defined with speed targets
- [ ] Caching configured for fast builds
- [ ] Tests run before merge (not after)
- [ ] Preview/staging deployments available
- [ ] Rollback procedure documented and tested
- [ ] Secrets management secure (no hardcoded values)
- [ ] Deploy notifications to team
