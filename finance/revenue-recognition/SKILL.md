# Revenue Recognition

Apply proper revenue recognition principles for SaaS, subscriptions, and hybrid business models.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for billing model and revenue streams
2. Understand contract terms before recognizing revenue

## Decision Tree: Recognition Method

```
What type of revenue?
├── Monthly subscription
│   └── Recognize monthly as service is delivered
├── Annual subscription (paid upfront)
│   └── Recognize 1/12 per month → deferred revenue liability
├── Usage-based
│   └── Recognize when usage occurs and is measurable
├── One-time setup fee
│   └── Is it distinct from ongoing service?
│       ├── Yes → Recognize at delivery
│       └── No → Amortize over contract term
├── Lifetime deal (LTD)
│   └── Recognize over estimated customer lifetime (3-5 years)
│       → Create deferred revenue schedule
└── Professional services
    └── Recognize as milestones are delivered (% completion)
```

## ASC 606 Five-Step Model

| Step | Question | SaaS Example |
|------|----------|-------------|
| 1. **Identify contract** | Is there an agreement? | Subscription agreement, TOS acceptance |
| 2. **Identify performance obligations** | What are you delivering? | Software access, support, onboarding |
| 3. **Determine transaction price** | What will you receive? | Monthly fee, annual fee, usage charges |
| 4. **Allocate price** | How to split across obligations? | Standalone selling price for each |
| 5. **Recognize revenue** | When is each obligation satisfied? | Over time (subscription) or point in time (setup) |

## Common SaaS Revenue Scenarios

| Scenario | Cash | Deferred Revenue | Recognized Revenue |
|----------|------|------------------|--------------------|
| Monthly sub ($100/mo, paid monthly) | $100/mo | $0 | $100/mo |
| Annual sub ($1,200/yr, paid upfront) | $1,200 day 1 | $1,100 day 1, declining | $100/mo |
| Annual sub ($1,200/yr, paid monthly) | $100/mo | $0 | $100/mo |
| LTD ($500 one-time) | $500 day 1 | $500 day 1, amortize 36-60mo | $8-14/mo |
| Setup fee ($200) + monthly ($100) | $200 + $100/mo | Depends on separability | See rules above |

## Key Metrics Impact

```
Bookings ≠ Revenue ≠ Cash

Bookings: Total contract value signed (e.g., 12 × $100 = $1,200 annual booking)
Revenue: Recognized per accounting rules (e.g., $100/month)
Cash: Actually received (e.g., $1,200 if prepaid, $100/month if monthly)
Deferred Revenue: Cash received but not yet recognized
```

## Anti-Patterns to Avoid

- **F1: Confusing revenue with cash** — The #1 financial mistake for SaaS companies.
- **F13: Recognizing LTD revenue immediately** — Must amortize over estimated customer lifetime.
- **F14: No deferred revenue tracking** — Required for accurate financials and audits.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **ASC 606 compliance** | All 5 steps documented per revenue stream | Key streams covered | No structured approach |
| **Deferred revenue tracking** | Monthly waterfall with aging | Total balance tracked | Not tracked |
| **Revenue stream separation** | Each stream has clear recognition policy | Most streams defined | Ad-hoc recognition |
| **Cash vs revenue clarity** | Three-way reconciliation (bookings/revenue/cash) | Revenue vs cash separated | Conflated |
| **LTD/Annual treatment** | Proper amortization schedules | Approximate schedules | Recognized at payment |
| **Audit readiness** | Documented policies with examples | Internal documentation | No documentation |
| **System integration** | Billing system generates recognition schedules | Manual spreadsheets | No system |

**28+ = Audit-ready | 21-27 = Needs formalization | <21 = Financial reporting risk**

## Cross-Skill References

- **Upstream:** `billing-design` (invoice data), `pricing-model` (contract terms), `ltd-deal-structure` (LTD terms)
- **Downstream:** `financial-model` (P&L accuracy), `kpi-dashboard` (MRR/ARR reporting)
- **Council:** Submit to `council-finance` for compliance review
