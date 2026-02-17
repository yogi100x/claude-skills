# Data Processing Agreement

Draft DPAs for vendor relationships where personal data is processed on your behalf.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for data flows and third-party services
2. Review privacy policy for disclosed data sharing

## When You Need a DPA

```
Do you share personal data with a third party?
├── Yes, they process data on your behalf (processor)
│   └── DPA required (GDPR Art. 28)
│       Examples: hosting provider, email service, analytics tool
├── Yes, they use data for their own purposes (controller-to-controller)
│   └── Data sharing agreement required
│       Examples: advertising partners, data enrichment services
├── Yes, but only aggregated/anonymized data
│   └── No DPA required, but document anonymization measures
└── No personal data shared
    └── No DPA required
```

## DPA Structure (GDPR Article 28)

| Section | Required Content |
|---------|-----------------|
| **Subject matter & duration** | What data, what processing, how long |
| **Nature & purpose** | Why data is being processed |
| **Data categories** | Types of personal data (email, IP, name, etc.) |
| **Data subjects** | Whose data (customers, employees, visitors) |
| **Controller obligations** | Your responsibilities |
| **Processor obligations** | Their responsibilities |
| **Sub-processors** | List of sub-processors, notification of changes |
| **Security measures** | Technical and organizational measures (TOMs) |
| **Data breach notification** | Timeline (72 hours for GDPR), process |
| **Data subject rights** | How processor assists with DSARs |
| **Audit rights** | Your right to audit processor compliance |
| **Data return/deletion** | What happens when contract ends |
| **International transfers** | SCCs or adequacy decisions if data leaves EEA |

## Standard Contractual Clauses (SCCs)

Required when data transfers from EU/EEA to countries without adequacy decisions:

| Module | Scenario | Example |
|--------|----------|---------|
| **Module 1** | Controller → Controller | You share data with a partner who uses it independently |
| **Module 2** | Controller → Processor | You send data to a US-based SaaS tool |
| **Module 3** | Processor → Sub-processor | Your processor uses another service |
| **Module 4** | Processor → Controller | Processor returns enriched data to you |

## Anti-Patterns to Avoid

- **L2: No DPA with processors** — Every vendor processing personal data on your behalf needs a DPA.
- **L7: DPA doesn't match actual data flows** — Review code and integrations, not just marketing materials.
- **L9: No sub-processor notification** — GDPR requires processors to notify you of sub-processor changes.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Coverage** | DPA with every processor | Major processors covered | Missing key processors |
| **Article 28 compliance** | All required provisions | Most provisions | Incomplete |
| **Sub-processor management** | Current list, notification process | List exists | No sub-processor tracking |
| **Security measures** | Specific TOMs documented | General security reference | No security terms |
| **Breach notification** | 72-hour timeline, clear process | Timeline stated | No breach process |
| **Transfer mechanism** | SCCs or adequacy for international transfers | Mechanism mentioned | No transfer safeguard |
| **Audit provisions** | Right to audit with practical process | Right stated | No audit rights |

**28+ = GDPR-compliant | 21-27 = Needs legal review | <21 = Significant gaps**

## Cross-Skill References

- **Upstream:** `privacy-policy` (data practices), `product-marketing-context` (vendor list)
- **Downstream:** `compliance-checklist` (DPA audit items)
- **Council:** Submit to `council-legal` for compliance review
