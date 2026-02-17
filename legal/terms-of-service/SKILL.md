# Terms of Service

Draft enforceable terms of service that protect the business while maintaining user trust.

## Context Sync Protocol

1. Read `.claude/product-marketing-context.md` for product description, pricing model
2. Read `.claude/finance-context.md` for billing terms, refund policy

## Decision Tree: TOS Type

```
What's your business model?
├── SaaS (subscription)
│   └── Subscription TOS: billing cycles, cancellation, feature access
├── Marketplace
│   └── Platform TOS: buyer terms, seller terms, dispute resolution, fees
├── API / Developer platform
│   └── API TOS: rate limits, usage restrictions, SLA, data ownership
├── Free tool / Freemium
│   └── Free TOS: acceptable use, limitations, upgrade terms
└── Enterprise
    └── MSA + Order Form: negotiable terms, SLA, indemnification
```

## TOS Structure

| Section | Purpose | Key Provisions |
|---------|---------|----------------|
| **Acceptance** | How users agree | Clickwrap > browsewrap. Age restrictions. |
| **Service description** | What you provide | Features, limitations, availability |
| **User obligations** | What users must/must not do | Acceptable use, account security |
| **Billing & payment** | How payment works | Pricing, billing cycle, taxes, refunds |
| **Intellectual property** | Who owns what | Your IP, user content, licenses |
| **Data & privacy** | Link to privacy policy | Data ownership, processing rights |
| **Termination** | How either party can end | Cancellation, suspension, data export |
| **Disclaimers** | Limitations on promises | "As-is" provision, warranty disclaimers |
| **Liability limits** | Cap on damages | Typically capped at fees paid in 12 months |
| **Dispute resolution** | How conflicts are resolved | Arbitration vs litigation, governing law |
| **Changes** | How TOS can be updated | Notice period, material change definition |

## Acceptable Use Policy (Embed or Reference)

| Category | Prohibited Activities |
|----------|----------------------|
| **Illegal** | Fraud, money laundering, illegal content |
| **Harmful** | Harassment, spam, malware distribution |
| **Abusive** | Scraping, reverse engineering, circumventing limits |
| **Deceptive** | Impersonation, fake accounts, misleading content |

## Anti-Patterns to Avoid

- **L1: Copy-paste TOS** — Generic templates miss your specific product terms.
- **L4: Browsewrap-only acceptance** — Clickwrap (checkbox) is more enforceable than browsewrap (footer link).
- **L6: Overreaching IP claims** — Claiming ownership of user content destroys trust.
- **L8: No dispute resolution clause** — Default to expensive litigation. Include arbitration or mediation.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Enforceability** | Clickwrap, clear acceptance mechanism | Browsewrap with notice | No acceptance mechanism |
| **Completeness** | All sections for your business model | Major sections present | Missing key sections |
| **Clarity** | Plain language, organized, scannable | Readable | Impenetrable legalese |
| **Balance** | Fair to both parties, reasonable limits | Slightly one-sided | Extremely one-sided |
| **IP clarity** | Clear ownership for company IP and user content | Mostly clear | Ambiguous |
| **Billing terms** | Pricing, refunds, cancellation clearly stated | Basic billing terms | Vague or missing |
| **Update mechanism** | Notice period, material change definition | Some notice provision | Can change without notice |

**28+ = Enforceable and fair | 21-27 = Needs legal review | <21 = Enforceability risk**

## Cross-Skill References

- **Upstream:** `pricing-model` (billing terms), `product-marketing-context` (product description)
- **Downstream:** `acceptable-use-policy` (detailed use restrictions), `dispute-resolution` (conflict process)
- **Council:** Submit to `council-legal` for enforceability review
