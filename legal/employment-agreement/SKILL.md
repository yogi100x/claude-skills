# Employment Agreement

Draft employment and contractor agreements that protect the company and comply with labor laws.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for company context and team structure

## Decision Tree: Agreement Type

```
What's the relationship?
├── Full-time employee
│   ├── US (at-will state) → Offer letter + Employee handbook + IP assignment
│   ├── US (just-cause state) → Employment agreement + handbook
│   ├── EU → Full employment contract (required by law)
│   └── Remote/International → EOR (Employer of Record) service
├── Part-time employee
│   └── Same as full-time but with hours/benefits specification
├── Independent contractor
│   ├── US → Independent Contractor Agreement (watch misclassification)
│   ├── International → Contractor agreement + tax compliance
│   └── Agency contractor → Agency MSA covers individual
└── Advisor
    └── Advisor agreement + equity terms + IP assignment
```

## Employment Agreement Structure

| Section | US (At-Will) | EU | Key Provisions |
|---------|-------------|-----|----------------|
| **Position & duties** | Required | Required | Title, reporting, responsibilities |
| **Compensation** | Required | Required | Salary, bonus, equity, benefits |
| **At-will / Term** | At-will statement | Fixed or indefinite term | Notice periods (EU: statutory) |
| **Benefits** | Summary + handbook ref | Detailed (statutory + company) | PTO, health, pension |
| **IP assignment** | Separate agreement typical | In contract | Work-for-hire, invention assignment |
| **Confidentiality** | Separate NDA or in contract | In contract | Scope, duration, exceptions |
| **Non-compete** | If enforceable in state | Varies by country | Scope, duration, geographic limit |
| **Non-solicit** | Recommended | Common | Customers and employees |
| **Termination** | At-will (minimal) | Notice period + process | Severance, garden leave |
| **Governing law** | State law | Country law | Jurisdiction |

## Contractor vs Employee (Misclassification Risk)

| Factor | Employee | Contractor |
|--------|----------|------------|
| **Control** | Company controls how work is done | Contractor controls methods |
| **Schedule** | Set hours | Flexible schedule |
| **Tools** | Company provides | Contractor provides own |
| **Exclusivity** | Usually exclusive | Can work for others |
| **Duration** | Ongoing | Project-based |
| **Integration** | Core business function | Specialized/temporary need |

**Misclassification penalties (US):** Back taxes, benefits, overtime, penalties — potentially $50K+ per worker.

## Equity Compensation Basics

| Type | Tax Treatment (US) | Typical For |
|------|-------------------|-------------|
| **ISO** (Incentive Stock Options) | Favorable (LTCG if held) | Employees only |
| **NSO** (Non-Qualified Stock Options) | Ordinary income at exercise | Anyone |
| **RSU** (Restricted Stock Units) | Ordinary income at vesting | Later-stage companies |
| **Restricted Stock** | 83(b) election available | Early employees/founders |

## Anti-Patterns to Avoid

- **L6: No IP assignment** — Without it, employee may claim ownership of code.
- **L8: Contractor misclassification** — If they work like an employee, they are one. Structure correctly.
- **L9: Non-compete in banned jurisdiction** — California, Minnesota, Oklahoma, North Dakota ban most non-competes.
- **L12: No governing law clause** — Don't leave jurisdiction ambiguous.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Classification accuracy** | Properly classified with documentation | Mostly correct | Misclassification risk |
| **IP protection** | Comprehensive IP assignment + prior inventions disclosure | Basic assignment | No IP terms |
| **Compliance** | Meets all jurisdictional requirements | Major requirements met | Missing statutory requirements |
| **Compensation clarity** | All components documented (salary, equity, benefits, bonus) | Salary and basic benefits | Vague compensation terms |
| **Termination provisions** | Clear process, notice, severance if applicable | Basic termination clause | No termination terms |
| **Confidentiality** | Reasonable scope and duration | Basic NDA | No confidentiality |
| **Restrictive covenants** | Enforceable and reasonable for jurisdiction | Present but may be unenforceable | Overly broad or missing |

**28+ = Legally sound | 21-27 = Needs local counsel review | <21 = Significant legal risk**

## Cross-Skill References

- **Upstream:** `cap-table` (equity grants), `product-marketing-context` (roles)
- **Downstream:** `ip-protection` (IP assignment enforcement), `compliance-checklist` (labor law items)
- **Council:** Submit to `council-legal` for jurisdiction-specific review
