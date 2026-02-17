# Tax Strategy

Navigate tax obligations, optimize tax position, and ensure compliance for software businesses.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for entity structure and revenue
2. Note: This skill provides frameworks, not tax advice. Always consult a CPA/tax advisor.

## Decision Tree: Tax Priority

```
What's your business stage?
├── Pre-revenue / Side project
│   └── Minimal: Track expenses, choose entity type wisely
├── Early revenue (<$500K)
│   └── Foundation: R&D credits, estimated payments, expense tracking
├── Growth ($500K-$5M)
│   └── Optimization: Entity restructuring, state nexus, international considerations
└── Scale ($5M+)
    └── Strategic: Transfer pricing, multi-entity, tax-efficient equity compensation
```

## Entity Selection Tax Impact

| Entity | Self-Employment Tax | Double Taxation | Pass-Through | Best For |
|--------|-------------------|-----------------|-------------|----------|
| **Sole Prop / LLC** | Yes (15.3%) | No | Yes | Solo founders, simplicity |
| **S-Corp** | On salary only | No | Yes | $80K+ profit, salary optimization |
| **C-Corp** | No | Yes (21% + dividends) | No | VC-backed, equity compensation |
| **LLC taxed as S-Corp** | On salary only | No | Yes | Flexibility + tax optimization |

## Key Tax Strategies for Software Companies

### R&D Tax Credits
- Federal credit: Up to 20% of qualified R&D expenses
- Qualified expenses: Developer salaries, cloud compute for development, contractor costs
- Startups (<$5M revenue, <5 years): Can offset payroll taxes up to $250K/year
- Documentation required: Time tracking, project descriptions, technical uncertainty

### Section 174 (R&D Amortization)
- As of 2022: R&D expenses must be capitalized and amortized over 5 years (domestic) or 15 years (foreign)
- Impact: Can create taxable income even when cash flow negative
- Planning: Model tax liability including 174 impact before year-end

### Sales Tax / SaaS Tax
| Jurisdiction | SaaS Taxable? | Nexus Trigger |
|-------------|---------------|---------------|
| Most US states | Varies by state | Economic nexus ($100K revenue or 200 transactions) |
| EU | Yes (VAT) | Any B2C sale |
| Canada | Yes (GST/HST) | $30K CAD threshold |

## Anti-Patterns to Avoid

- **F1: No estimated tax payments** — IRS penalties for underpayment are avoidable.
- **F9: Entity chosen for legal reasons only** — Tax implications of entity type are significant.
- **L5: Ignoring sales tax obligations** — Many states now tax SaaS. Ignorance isn't a defense.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Entity optimization** | Structure reviewed for tax efficiency | Entity chosen but not optimized | No consideration |
| **R&D credits** | Claimed with documentation | Aware but not claiming | Not considered |
| **Compliance** | All obligations identified and met | Major items covered | Reactive only |
| **Planning** | Year-round tax planning with projections | Year-end planning | April scramble |
| **Professional support** | CPA/tax advisor engaged with clear brief | Occasional consultation | DIY only |
| **Documentation** | Expenses tracked with categories and receipts | Bank statements only | Poor records |
| **Multi-jurisdiction** | Sales tax and international obligations mapped | Aware of major obligations | US federal only |

**28+ = Well-managed | 21-27 = Needs professional review | <21 = Compliance risk**

## Cross-Skill References

- **Upstream:** `financial-model` (revenue projections), `cap-table` (equity compensation)
- **Downstream:** `compliance-checklist` (tax filing deadlines)
- **Council:** Submit to `council-finance` + `council-legal` for compliance review
