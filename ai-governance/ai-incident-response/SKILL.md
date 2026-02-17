# AI Incident Response

Handle AI-specific incidents including harmful outputs, bias discovery, model failures, and adversarial attacks.

## Context Sync Protocol

1. Read AI monitoring dashboards for current alerts
2. Read model cards for affected systems

## Decision Tree: AI Incident Type

```
What happened?
├── Harmful output generated
│   └── Severity: Who saw it? Can it cause harm?
│       → Immediate: Block output, log incident, review prompt/guardrails
├── Bias discovered in production
│   └── Severity: Who is affected? How long has it been occurring?
│       → Assess scope, implement temporary mitigation, plan remediation
├── Model performance degradation
│   └── Severity: SLA breach? User-visible impact?
│       → Fallback to previous version or non-AI path
├── Prompt injection / Adversarial attack
│   └── Severity: Data exfiltration? System compromise?
│       → Block attacker, patch vulnerability, assess damage
├── Data leak via model
│   └── Severity: PII exposed? Training data memorization?
│       → Treat as data breach (see incident-response-plan)
└── Cost spike / Abuse
    └── Severity: Budget impact?
        → Rate limit, block abusers, investigate root cause
```

## Response Protocol

### Phase 1: Contain (0-1 hours)

| Action | Owner |
|--------|-------|
| Disable affected AI feature (if critical) or add guardrail | Engineering |
| Preserve logs and evidence | Security |
| Assess blast radius (users affected, duration, severity) | Incident Commander |
| Notify stakeholders | Incident Commander |

### Phase 2: Investigate (1-24 hours)

| Action | Owner |
|--------|-------|
| Root cause analysis (prompt, model, data, or system) | Engineering |
| User impact assessment | Product |
| Regulatory notification assessment | Legal |
| Communication plan for affected users | Product + Comms |

### Phase 3: Remediate (1-7 days)

| Action | Owner |
|--------|-------|
| Deploy fix (prompt update, model rollback, guardrail addition) | Engineering |
| Verify fix doesn't introduce new issues | QA |
| Notify affected users if required | Comms |
| Update model card and documentation | Engineering |

### Phase 4: Learn (Within 2 weeks)

| Action | Owner |
|--------|-------|
| Blameless post-mortem | Incident Commander |
| Update monitoring to detect similar incidents | Engineering |
| Update AI incident playbook | AI Ethics Officer |
| Share learnings (internal or public) | AI Ethics Officer |

## Anti-Patterns to Avoid

- **A3: Ignoring AI incidents** — AI failures are different from software bugs. Dedicated response needed.
- **A5: No rollback capability** — Always maintain ability to revert to previous model/prompt version.
- **A9: Blaming the model** — Root cause is usually data, prompt design, or missing guardrails, not "the AI."

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Response speed** | Contain within 1 hour for critical incidents | Within 4 hours | No defined timeline |
| **Playbook** | Documented runbook for each incident type | General incident process | No playbook |
| **Rollback** | One-click rollback for model/prompt | Manual rollback possible | No rollback |
| **Communication** | User notification plan with templates | Ad-hoc communication | No communication plan |
| **Root cause** | Systematic RCA with 5-whys | Basic investigation | No RCA |
| **Prevention** | Monitoring updated, guardrails improved | Some improvements | No prevention |
| **Post-mortem** | Blameless post-mortem with tracked action items | Post-mortem happens | No post-mortem |

**28+ = Incident-ready | 21-27 = Needs playbook detail | <21 = Unprepared**

## Cross-Skill References

- **Upstream:** `ai-monitoring-setup` (alert triggering), `incident-response-plan` (general IR framework)
- **Downstream:** `model-card` (updated with incident learnings)
- **Council:** Submit to `council-ai` for post-mortem review
