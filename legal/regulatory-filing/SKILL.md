# Regulatory Filing

Navigate and complete regulatory filings required for software businesses across jurisdictions.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for entity structure and jurisdictions
2. Read `.claude/product-marketing-context.md` for markets served

## Decision Tree: Filing Requirements

```
What filings do you need?
├── Business formation
│   └── Articles of incorporation, EIN, state registrations
├── Data protection
│   ├── UK → ICO registration (annual, £40-£2,900)
│   ├── EU → DPO appointment notification (if required)
│   └── US states → Data broker registration (if applicable)
├── Tax filings
│   ├── Federal → Annual return (1120 for C-Corp, 1065 for LLC)
│   ├── State → Franchise tax, income tax where nexus exists
│   └── Sales tax → Registration + periodic returns per state
├── Securities (if raising funds)
│   ├── Regulation D → Form D filing (within 15 days of first sale)
│   ├── Blue sky → State securities filings
│   └── Stock option plans → 83(b) elections, Section 409A
└── Industry-specific
    └── Check sector requirements (fintech, healthtech, edtech)
```

## Common Filing Calendar

| Filing | Jurisdiction | Deadline | Penalty for Late |
|--------|-------------|----------|-----------------|
| **Annual report** | State of incorporation | Varies by state | $50-$500+ |
| **Franchise tax** | Delaware | March 1 | $200+ penalty |
| **Federal tax return** | IRS | April 15 (or extension) | 5% per month |
| **Sales tax returns** | Per state | Monthly/Quarterly | Varies |
| **Form D (securities)** | SEC | 15 days after first sale | Bad faith indicator |
| **ICO registration** | UK | Annual | £4,000+ fine |
| **GDPR records** | EU | Ongoing (maintain) | Up to €20M fine |

## Anti-Patterns to Avoid

- **L5: Missing filing deadlines** — Calendar all deadlines. Most have automatic penalties.
- **L11: Operating without required registrations** — Foreign qualification, sales tax, data protection.
- **L1: DIY complex filings** — Securities, international tax, and some regulatory filings need professional help.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Inventory** | All required filings identified per jurisdiction | Major filings known | Ad-hoc awareness |
| **Calendar** | All deadlines calendared with reminders | Key deadlines tracked | No calendar |
| **Accuracy** | Filings reviewed by professional | Self-prepared, reviewed | No review |
| **Record-keeping** | All filings organized and accessible | Most filings on file | Missing records |
| **Compliance monitoring** | New regulatory requirements tracked | Annual review | Reactive only |
| **Professional support** | CPA/attorney for complex filings | Occasional help | No professional support |
| **Multi-jurisdiction** | All operating jurisdictions covered | Home jurisdiction only | Missing registrations |

**28+ = Fully compliant | 21-27 = Gaps to address | <21 = Missing critical filings**

## Cross-Skill References

- **Upstream:** `tax-strategy` (tax filings), `compliance-checklist` (regulatory items)
- **Downstream:** `cap-table` (securities filings)
- **Council:** Submit to `council-legal` + `council-finance` for compliance review
