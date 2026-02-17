# Incident Response Plan

Create and maintain security and data breach incident response plans.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for data types and user base
2. Check existing compliance documentation for regulatory requirements

## Decision Tree: Incident Classification

```
What happened?
├── Data breach (personal data exposed)
│   ├── EU users affected → GDPR: notify DPA within 72 hours
│   ├── California users → CCPA: notify affected individuals
│   └── Other US states → Check state breach notification laws
├── Security incident (no data confirmed exposed)
│   └── Investigate scope, contain threat, document findings
├── Service outage
│   └── Follow SLA obligations, communicate via status page
├── Ransomware / Malware
│   └── Isolate, assess, law enforcement if needed
└── Insider threat
    └── Preserve evidence, restrict access, HR + legal involvement
```

## Incident Response Phases

### Phase 1: Detection & Triage (0-1 hours)

| Step | Action | Owner |
|------|--------|-------|
| 1 | Detect anomaly (alert, report, discovery) | Security/Engineering |
| 2 | Classify severity (P1-P4) | Incident Commander |
| 3 | Assemble response team | Incident Commander |
| 4 | Establish communication channel | Incident Commander |

### Phase 2: Containment (1-4 hours)

| Step | Action | Owner |
|------|--------|-------|
| 5 | Contain the threat (isolate systems, revoke access) | Engineering |
| 6 | Preserve evidence (logs, snapshots) | Security |
| 7 | Assess scope (what data, how many users) | Security |
| 8 | Determine notification obligations | Legal |

### Phase 3: Notification (Within 72 hours for GDPR)

| Audience | When | What to Include |
|----------|------|----------------|
| **DPA (GDPR)** | Within 72 hours | Nature of breach, data types, number affected, measures taken |
| **Affected users** | "Without undue delay" | What happened, what data, what you're doing, what they should do |
| **Law enforcement** | If criminal activity suspected | Preserve evidence first |
| **Partners/vendors** | If their data affected | Scope and remediation plan |

### Phase 4: Recovery & Post-Mortem

| Step | Action | Timeline |
|------|--------|----------|
| 9 | Eradicate root cause | ASAP |
| 10 | Restore services | Per SLA |
| 11 | Conduct post-mortem (blameless) | Within 1 week |
| 12 | Update preventive measures | Within 2 weeks |
| 13 | Update incident response plan | Within 1 month |

## Severity Classification

| Level | Description | Response Time | Example |
|-------|------------|---------------|---------|
| **P1 Critical** | Active data breach, service compromise | Immediate, all-hands | Database exfiltration |
| **P2 High** | Potential breach, significant vulnerability | <1 hour | Unpatched critical CVE |
| **P3 Medium** | Contained incident, limited impact | <4 hours | Single account compromise |
| **P4 Low** | Minor security event, no data impact | Next business day | Failed login attempts |

## Anti-Patterns to Avoid

- **L3: No incident response plan** — Having no plan guarantees a chaotic response.
- **L5: Missing notification deadline** — GDPR 72-hour deadline is strict. Late notification = additional penalties.
- **L7: Destroying evidence** — Preserve logs and artifacts before remediation.
- **T14: No post-mortem** — Without learning from incidents, you'll repeat them.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Plan completeness** | All phases covered with roles assigned | Key phases covered | No documented plan |
| **Communication plan** | Templates for all audiences ready | Some templates | Ad-hoc communication |
| **Notification compliance** | All regulatory timelines mapped | Major regulations covered | No timeline awareness |
| **Team readiness** | Annual tabletop exercises | Team identified | No designated team |
| **Evidence preservation** | Forensic procedures documented | Basic log retention | No evidence procedures |
| **Post-mortem process** | Blameless format, tracked action items | Post-mortem happens | No post-mortem |
| **Continuous improvement** | Plan updated after every incident and annually | Occasional updates | Static document |

**28+ = Incident-ready | 21-27 = Plan needs testing | <21 = Unprepared**

## Cross-Skill References

- **Upstream:** `compliance-checklist` (regulatory requirements), `security-hardening` (preventive measures)
- **Downstream:** `ai-incident-response` (AI-specific incidents), `monitoring-setup` (detection capability)
- **Council:** Submit to `council-legal` for notification compliance review
