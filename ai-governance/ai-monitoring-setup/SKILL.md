# AI Monitoring Setup

Design monitoring systems for AI features in production to detect drift, bias, failures, and abuse.

## Context Sync Protocol

1. Read model cards for baseline metrics and thresholds
2. Read `.claude/product-marketing-context.md` for SLA requirements

## Decision Tree: Monitoring Scope

```
What needs monitoring?
├── Model performance
│   └── Accuracy, latency, error rate, cost per inference
├── Fairness / Bias drift
│   └── Disaggregated metrics over time by protected groups
├── Safety
│   └── Harmful outputs, prompt injection attempts, policy violations
├── Usage patterns
│   └── Volume, user segments, feature adoption, abuse patterns
└── Data drift
    └── Input distribution shift from training data
```

## Monitoring Dashboard

### Tier 1: Real-Time Alerts

| Metric | Threshold | Alert |
|--------|-----------|-------|
| Error rate | >5% (5-min window) | PagerDuty |
| Latency p99 | >5s | Slack |
| Safety violation | Any | Immediate review |
| Cost spike | >2x daily average | Slack |

### Tier 2: Daily Monitoring

| Metric | Check | Action if Anomalous |
|--------|-------|---------------------|
| Accuracy (if measurable) | Compared to baseline | Investigate data drift |
| Output quality (sample review) | 20 random outputs daily | Prompt tuning |
| User satisfaction (thumbs up/down) | Trend analysis | Feature review |
| Token usage / Cost | Budget tracking | Optimization |

### Tier 3: Weekly/Monthly

| Metric | Check | Action |
|--------|-------|--------|
| Bias metrics | Disaggregated by group | Bias testing if drift detected |
| Input distribution | Compare to training distribution | Retrain or update prompts |
| Override rate | Human override frequency | Model improvement if high |
| Abuse patterns | Prompt injection attempts, policy circumvention | Security hardening |

## Anti-Patterns to Avoid

- **A5: No production monitoring** — Deploy and forget guarantees drift and degradation.
- **A10: Aggregate metrics only** — Disaggregate by user segment, model version, input type.
- **A12: No cost monitoring** — AI costs can spike unexpectedly. Set budget alerts.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Coverage** | All AI features monitored across performance, safety, fairness | Key features monitored | Ad-hoc monitoring |
| **Alerting** | Tiered alerts with appropriate urgency | Basic alerts | No alerts |
| **Dashboards** | Real-time dashboards accessible to stakeholders | Some dashboards | No dashboards |
| **Drift detection** | Automated data and concept drift detection | Manual periodic checks | No drift monitoring |
| **Cost tracking** | Per-feature cost with budget alerts | Total cost tracked | No cost monitoring |
| **Incident response** | Clear runbook for AI-specific incidents | Some response process | No runbook |
| **Feedback loop** | Monitoring insights feed model improvement | Occasional improvements | No feedback loop |

**28+ = Production-grade | 21-27 = Needs automation | <21 = Flying blind**

## Cross-Skill References

- **Upstream:** `model-card` (baseline metrics), `prompt-engineering` (prompt versions)
- **Downstream:** `ai-incident-response` (triggered by alerts), `bias-testing` (triggered by drift)
- **Parallel:** `monitoring-setup` (infrastructure monitoring)
- **Council:** Submit to `council-ai` for monitoring completeness review
