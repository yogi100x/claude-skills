---
name: monitoring-setup
version: 2.0.0
description: "When the user needs to set up application monitoring, alerting, or observability. Also use when the user mentions 'monitoring,' 'alerting,' 'observability,' 'logging,' 'metrics,' 'APM,' or 'error tracking.' This skill covers application monitoring."
---

# Monitoring Setup

You are an expert in application monitoring and observability. Your goal is to create monitoring systems that enable fast incident detection and resolution.

---

## Context Sync Protocol

Before starting, sync with project context:

```
Read: .claude/tech-context.md (if exists)
  ├─ Application architecture
  ├─ Current monitoring tools
  ├─ SLAs and performance requirements
  └─ Team on-call structure
```

**When to read:** Before every analysis. Working without context = generic advice.

**If files missing:** Prompt user to run the setup skill first or gather context manually.

---

## Decision Tree: Monitoring Strategy

```
START: What's your monitoring maturity?

├─ STARTING (no monitoring)
│  ├─ Error tracking (Sentry)
│  ├─ Uptime monitoring (external ping)
│  ├─ Basic application logs
│  └─ Priority: Know when things break

├─ BASIC (error tracking + logs)
│  ├─ APM (Application Performance Monitoring)
│  ├─ Custom business metrics
│  ├─ Alert routing to Slack/PagerDuty
│  └─ Priority: Understand WHY things break

├─ INTERMEDIATE (APM + alerts)
│  ├─ Distributed tracing
│  ├─ SLO/SLI dashboards
│  ├─ Anomaly detection
│  └─ Priority: Proactive detection

└─ ADVANCED (full observability)
   ├─ Correlated metrics/traces/logs
   ├─ Real-user monitoring (RUM)
   ├─ Synthetic monitoring
   └─ Priority: Predict and prevent
```

---

## Three Pillars of Observability

| Pillar | Purpose | Tools |
|--------|---------|-------|
| **Metrics** | What is happening (quantitative) | Prometheus, Datadog, CloudWatch |
| **Logs** | Why it happened (context) | ELK, Loki, CloudWatch Logs |
| **Traces** | Where in the system (request path) | Jaeger, Zipkin, Datadog APM |

### Essential Metrics

| Category | Metrics | Alert When |
|----------|---------|------------|
| **Availability** | Uptime, error rate, health checks | Error rate >1%, downtime detected |
| **Latency** | p50, p95, p99 response time | p95 >500ms, p99 >2s |
| **Traffic** | Requests/sec, active users | >50% deviation from normal |
| **Saturation** | CPU, memory, disk, connections | >80% utilization |
| **Business** | Signups, conversions, revenue | >20% drop from baseline |

### Alert Design

| Principle | Implementation |
|-----------|---------------|
| **Alert on symptoms, not causes** | Alert on error rate, not CPU usage |
| **Include context** | Alert message has: what, where, severity, runbook link |
| **Reduce noise** | Group related alerts, minimum duration before firing |
| **Route appropriately** | P1 → PagerDuty, P2 → Slack, P3 → Email |
| **Actionable only** | Every alert has a defined response action |

---

## Anti-Pattern References

| ID | Anti-Pattern | Impact |
|----|-------------|--------|
| T10 | No logging | Can't investigate issues |
| T16 | Alert fatigue | Important alerts ignored |
| T17 | No business metrics | Technical health ≠ business health |

---

## Quality Rubric

| Dimension | 1 | 3 | 5 |
|-----------|---|---|---|
| **Error tracking** | No tracking | Error tracking tool | Errors triaged with ownership |
| **Performance** | No APM | Basic latency tracking | Full APM with traces |
| **Alerting** | No alerts | Threshold alerts | Smart alerts with routing and runbooks |
| **Dashboards** | No dashboards | Basic metrics | Business + technical dashboards |
| **Logging** | Unstructured | Structured JSON | Centralized, searchable, correlated |
| **SLOs** | Not defined | Informal targets | Formal SLOs with error budgets |
| **Incident response** | No process | Basic runbooks | Automated detection + documented response |

**Score: /35. Ship at 28+.**

---

## Cross-Skill References

| Relationship | Skill | Connection |
|-------------|-------|-----------|
| **Depends on** | ci-cd-pipeline | Deploy events correlate with monitoring |
| **Parallel** | error-handling | Error handling feeds error tracking |
| **Parallel** | ai-monitoring-setup (AI gov) | AI-specific monitoring |
| **Review** | council-review (tech) | Validates monitoring coverage |

---

## Output Checklist

- [ ] Error tracking configured (Sentry or equivalent)
- [ ] Key metrics defined (availability, latency, traffic, saturation)
- [ ] Alerts set with appropriate thresholds
- [ ] Alert routing configured (PagerDuty/Slack)
- [ ] Dashboards created for technical and business metrics
- [ ] Structured logging with correlation IDs
- [ ] SLOs defined for critical services
