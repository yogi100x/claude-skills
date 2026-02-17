# Compliance Checklist

Generate comprehensive compliance checklists based on business model, jurisdictions, and regulations.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for business model and target markets
2. Read `.claude/finance-context.md` for billing and financial compliance needs

## Decision Tree: Compliance Scope

```
What regulations apply?
├── Collect personal data → GDPR, CCPA, state privacy laws
├── Process payments → PCI DSS, PSD2 (EU)
├── Serve EU users → Digital Services Act, ePrivacy
├── Handle health data → HIPAA (US), special GDPR categories
├── Serve financial sector → SOC 2, ISO 27001
├── Use AI/ML → EU AI Act, state AI laws
├── Have employees → Employment law per jurisdiction
└── Operate globally → All of the above + local regulations
```

## Master Compliance Checklist

### Data Protection

- [ ] Privacy policy published and accessible
- [ ] Cookie consent mechanism implemented (opt-in for EU)
- [ ] Data processing agreements with all vendors
- [ ] Data Subject Access Request (DSAR) process documented
- [ ] Data retention policy defined and implemented
- [ ] Data breach notification process documented (72 hours for GDPR)
- [ ] International data transfer mechanisms in place (SCCs)
- [ ] Data Protection Impact Assessment (DPIA) for high-risk processing
- [ ] Records of processing activities maintained
- [ ] DPO appointed (if required by GDPR)

### Security

- [ ] Encryption at rest and in transit
- [ ] Access controls with least-privilege principle
- [ ] Multi-factor authentication for admin access
- [ ] Regular security assessments/penetration testing
- [ ] Incident response plan documented and tested
- [ ] Employee security awareness training
- [ ] Vendor security assessment process
- [ ] Backup and disaster recovery plan

### Business & Legal

- [ ] Terms of service published
- [ ] Acceptable use policy defined
- [ ] IP assignments from all contributors
- [ ] Business insurance (E&O, cyber liability)
- [ ] Corporate entity properly registered
- [ ] Tax registrations in applicable jurisdictions
- [ ] Employment law compliance per jurisdiction
- [ ] Accessibility compliance (WCAG 2.1 AA minimum)

### Financial

- [ ] Sales tax/VAT collection where required
- [ ] Revenue recognition policy documented
- [ ] Anti-money laundering (if applicable)
- [ ] Stripe/payment processor compliance maintained
- [ ] Financial records retention (7 years typical)

## Compliance Calendar

| Frequency | Task |
|-----------|------|
| **Monthly** | Review access logs, update vendor list, check data breach inbox |
| **Quarterly** | Review privacy policy accuracy, update compliance checklist, security scan |
| **Annually** | Full compliance audit, employee training, vendor re-assessment, policy updates |
| **Event-driven** | New market entry, new feature with data impact, acquisition, funding round |

## Anti-Patterns to Avoid

- **L1: Compliance as one-time project** — Compliance is ongoing. Schedule regular reviews.
- **L5: Ignoring new regulations** — Privacy laws are evolving rapidly. Monitor changes.
- **L7: Documentation without implementation** — Policies must match actual practices.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Coverage** | All applicable regulations identified | Major regulations covered | Ad-hoc compliance |
| **Documentation** | All policies written and accessible | Key policies exist | Missing documents |
| **Implementation** | Policies match actual practices | Mostly implemented | Policies not enforced |
| **Monitoring** | Regular audits with calendar | Annual review | No regular review |
| **Training** | All employees trained, documented | Some training | No training |
| **Incident readiness** | Tested incident response plan | Plan exists | No plan |
| **Vendor management** | All vendors assessed and compliant | Key vendors assessed | No vendor assessment |

**28+ = Audit-ready | 21-27 = Gaps to close | <21 = Significant compliance risk**

## Cross-Skill References

- **Upstream:** All legal skills feed into this checklist
- **Downstream:** `incident-response-plan` (security incidents), `ai-impact-assessment` (AI compliance)
- **Council:** Submit to `council-legal` for completeness review
