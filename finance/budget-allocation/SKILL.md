# Budget Allocation

Allocate marketing, R&D, and operational budgets based on growth stage, channel economics, and strategic priorities.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for total budget, margins, runway
2. Read `.claude/product-marketing-context.md` for growth targets and channels

## Decision Tree: Budget Framework

```
What's your primary constraint?
├── Cash-constrained (runway < 18 months)
│   └── Efficiency-first: Only fund channels with proven CAC payback < 6 months
│       → 70% proven channels, 20% promising experiments, 10% brand
├── Growth-constrained (need to accelerate)
│   └── Growth-first: Invest ahead of revenue in high-potential channels
│       → 50% scaling winners, 30% new channels, 20% brand/content
├── Profit-constrained (need to improve margins)
│   └── ROI-first: Cut underperforming spend, double down on best channels
│       → 80% top 3 channels by ROI, 15% optimization, 5% testing
└── Entering new market
    └── Market-first: Heavy upfront investment with longer payback tolerance
        → 40% awareness, 30% demand gen, 20% enablement, 10% measurement
```

## Marketing Budget by Stage

| Stage | S&M as % Revenue | Content/SEO | Paid Acquisition | Brand | Experimental |
|-------|-------------------|-------------|-----------------|-------|-------------|
| Pre-PMF | 20-40% | 30% | 20% | 10% | 40% |
| Early Growth | 40-80% | 25% | 40% | 15% | 20% |
| Scaling | 30-50% | 30% | 35% | 25% | 10% |
| Mature | 15-25% | 35% | 30% | 30% | 5% |

## Channel Budget Allocation

### The 70/20/10 Rule

| Bucket | % of Budget | Criteria | Review Cycle |
|--------|-------------|----------|-------------|
| **Proven (70%)** | 70% | CAC < target, payback < 12mo, scalable | Monthly optimization |
| **Promising (20%)** | 20% | Early data positive, needs more volume | Bi-weekly check, monthly go/no-go |
| **Experimental (10%)** | 10% | Unproven, high potential, learning budget | Weekly check, kill fast if no signal |

### Channel Graduation

```
Experimental → Promising: Shows positive signal in 2-4 weeks (leads or engagement)
Promising → Proven: Achieves target CAC over 2+ months with sufficient volume
Proven → Scaled: Maintains CAC as spend increases 2-3x

Demotion triggers:
- CAC increases >30% for 2 consecutive months
- Volume plateaus despite spend increase
- Channel quality (conversion to paid) drops below threshold
```

## R&D Budget Framework

| Category | Pre-PMF | Growth | Scale |
|----------|---------|--------|-------|
| **New features** | 60% | 40% | 25% |
| **Technical debt / infra** | 10% | 25% | 30% |
| **Bug fixes / maintenance** | 15% | 20% | 25% |
| **Innovation / R&D** | 15% | 15% | 20% |

## Anti-Patterns to Avoid

- **F2: Ignoring unit economics** — Allocating budget without channel-level CAC tracking.
- **M2: Scaling before PMF** — Pouring money into acquisition before retention is healthy.
- **M4: Ignoring CAC:LTV** — Equal budget allocation across channels regardless of economics.
- **F5: Top-down only** — "We'll spend $X on marketing" without bottom-up channel plans.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Channel economics** | Per-channel CAC, payback, and ROI data | Top channels measured | No per-channel data |
| **Stage alignment** | Budget matches business stage and constraints | Roughly appropriate | Mismatched to stage |
| **Review cadence** | Monthly rebalancing with kill criteria | Quarterly review | Annual set-and-forget |
| **Scenario planning** | Budget under 3 scenarios (base/bull/bear) | Single budget | No contingency |
| **Measurement plan** | Attribution model + leading indicators per channel | Basic conversion tracking | No measurement |
| **Flexibility** | 10-20% reserve for opportunistic spending | Some flexibility | 100% committed |
| **Documentation** | Assumptions, rationale, and decision criteria documented | Spreadsheet exists | Verbal agreement |

**28+ = Board-ready | 21-27 = Needs detail | <21 = Insufficient rigor**

## Cross-Skill References

- **Upstream:** `unit-economics` (channel CAC), `financial-model` (total budget), `pricing-model` (revenue targets)
- **Downstream:** `paid-ads` (ad budget), `content-strategy` (content budget)
- **Council:** Submit to `council-finance` for budget validation
