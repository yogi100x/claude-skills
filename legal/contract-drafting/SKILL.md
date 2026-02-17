# Contract Drafting

Draft and review commercial contracts for software companies including vendor agreements, partnerships, and customer contracts.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for business model and partnerships
2. Read `.claude/finance-context.md` for pricing and payment terms

## Decision Tree: Contract Type

```
What's the relationship?
├── Selling to customers
│   ├── Self-serve → TOS + Privacy Policy (no individual contracts)
│   ├── SMB → Lightweight order form + standard terms
│   └── Enterprise → MSA + SOW + Order Form + SLA + DPA
├── Buying from vendors
│   ├── SaaS tool → Review vendor TOS, negotiate enterprise terms
│   ├── Contractor → Independent contractor agreement
│   └── Agency → Services agreement with deliverables and IP assignment
├── Partnerships
│   ├── Integration → API partnership agreement + data sharing terms
│   ├── Reseller → Reseller/referral agreement + commission terms
│   └── Co-marketing → Joint marketing agreement
└── Employment
    └── See: employment-agreement skill
```

## Enterprise Contract Stack

| Document | Purpose | Negotiable? |
|----------|---------|-------------|
| **MSA** (Master Service Agreement) | Overarching legal terms | Heavily |
| **SOW** (Statement of Work) | Specific deliverables and timeline | Yes |
| **Order Form** | Pricing, quantities, term | Yes |
| **SLA** (Service Level Agreement) | Uptime, response time commitments | Somewhat |
| **DPA** (Data Processing Agreement) | Data protection terms | Template-based |
| **NDA** | Confidentiality during evaluation | Standard |

## Key Contract Provisions

| Provision | What to Include | Watch Out For |
|-----------|----------------|---------------|
| **Term & Renewal** | Start date, duration, auto-renewal terms | Auto-renewal without notice period |
| **Payment** | Pricing, net terms (30/60/90), late fees | Net-90 for startups (cash flow risk) |
| **IP ownership** | Who owns what's created | Work-for-hire vs licensed |
| **Confidentiality** | Scope, duration (2-5 years), exclusions | Overly broad definitions |
| **Liability cap** | Typically 12 months of fees paid | Uncapped indemnification |
| **Indemnification** | Who covers what claims | Mutual vs one-sided |
| **Termination** | For cause, for convenience, notice period | No termination for convenience |
| **Governing law** | Jurisdiction for disputes | Unfavorable jurisdiction |

## Anti-Patterns to Avoid

- **L1: Template without customization** — Every contract must reflect the specific deal.
- **L9: Unlimited liability** — Always cap liability. Exceptions only for IP infringement, confidentiality breach.
- **L10: No termination for convenience** — Both parties should be able to exit with notice.
- **L11: Verbal agreements** — If it's not written, it doesn't exist.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Completeness** | All key provisions covered | Major provisions present | Missing critical terms |
| **Balance** | Fair risk allocation for both parties | Slightly favoring one party | Heavily one-sided |
| **Clarity** | Unambiguous language, defined terms | Mostly clear | Ambiguous provisions |
| **IP protection** | Clear ownership and licensing terms | Basic IP provisions | No IP terms |
| **Liability management** | Appropriate caps and carve-outs | Caps exist | Uncapped or missing |
| **Exit provisions** | Clear termination rights and process | Basic termination | No exit mechanism |
| **Enforceability** | Proper execution, governing law, dispute resolution | Most elements present | Missing execution terms |

**28+ = Ready to sign | 21-27 = Needs legal review | <21 = Significant risk**

## Cross-Skill References

- **Upstream:** `pricing-model` (pricing terms), `product-marketing-context` (scope of services)
- **Downstream:** `data-processing-agreement` (if data sharing involved), `ip-protection` (IP terms)
- **Council:** Submit to `council-legal` for review before execution
