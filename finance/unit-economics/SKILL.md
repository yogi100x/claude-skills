# Unit Economics

Calculate and optimize the fundamental economics of acquiring and serving each customer.

## Context Sync Protocol

Before analysis:
1. Read `.claude/finance-context.md` for existing CAC, LTV, margins
2. Read `.claude/product-marketing-context.md` for pricing and ICP
3. If neither exists, gather channel costs and pricing before calculating

## Decision Tree: Analysis Type

```
What do you need?
├── First-time calculation
│   └── Gather: pricing, churn, COGS, acquisition costs by channel
│       → Calculate: LTV, CAC, payback period per channel
├── Optimization
│   └── Diagnose: Which metric is unhealthy?
│       ├── LTV too low → Fix churn or increase ARPU
│       ├── CAC too high → Optimize channels or improve conversion
│       └── Payback too long → Consider annual pricing or reduce onboarding cost
└── Investor preparation
    └── Calculate: Blended + per-channel + cohort-based metrics
        → Show improvement trajectory over time
```

## Core Formulas

### Customer Lifetime Value (LTV)

```
Simple LTV = ARPU × Gross Margin % × Average Customer Lifetime

Where:
  Average Customer Lifetime = 1 / Monthly Churn Rate
  
Example:
  ARPU = $100/month
  Gross Margin = 80%
  Monthly Churn = 3%
  Lifetime = 1/0.03 = 33.3 months
  LTV = $100 × 0.80 × 33.3 = $2,664
```

**Advanced LTV (with expansion):**
```
LTV = ARPU × Gross Margin % × (1 / (Churn Rate - Expansion Rate))

If expansion > churn (negative net churn):
  LTV calculation needs a time cap (typically 5-7 years)
  LTV = ARPU × Gross Margin % × Σ(1 - Net Churn)^t for t=1 to cap
```

### Customer Acquisition Cost (CAC)

```
Blended CAC = Total S&M Spend / New Customers Acquired

Fully-loaded CAC = (S&M Spend + Sales Salaries + Onboarding Cost) / New Customers

Per-channel CAC:
  Paid CAC = Ad Spend on Channel / Customers from Channel
  Organic CAC = Content Team Cost / Customers from Organic
  Referral CAC = Referral Rewards / Customers from Referrals
```

### Payback Period

```
CAC Payback (months) = CAC / (ARPU × Gross Margin %)

Example:
  CAC = $500
  ARPU = $100/month
  Gross Margin = 80%
  Payback = $500 / ($100 × 0.80) = 6.25 months
```

## Benchmarks

| Metric | Unhealthy | Acceptable | Strong | Elite |
|--------|-----------|------------|--------|-------|
| **LTV:CAC** | <1:1 | 1-3:1 | 3-5:1 | >5:1 |
| **CAC Payback** | >24 mo | 12-24 mo | 6-12 mo | <6 mo |
| **Gross Margin** | <50% | 50-70% | 70-85% | >85% |
| **Net Revenue Retention** | <90% | 90-100% | 100-120% | >120% |
| **Monthly Logo Churn** | >5% | 3-5% | 1-3% | <1% |

## The Unit Economics Health Check

Run this diagnostic on any business:

| Check | Formula | Action if Failing |
|-------|---------|-------------------|
| **Viable?** | LTV > CAC | Fundamental business model problem. Fix before scaling. |
| **Sustainable?** | LTV:CAC > 3:1 | Improve retention, reduce CAC, or increase ARPU. |
| **Scalable?** | Marginal CAC stable as spend increases | Channel is saturating. Diversify acquisition. |
| **Cash-efficient?** | Payback < 18 months | Consider annual pricing, reduce sales cycle. |

## Anti-Patterns to Avoid

- **F2: Ignoring unit economics** — Growing revenue with negative unit economics is buying revenue with investor money.
- **F1: Confusing revenue with cash** — Annual prepay improves cash flow but doesn't change unit economics.
- **M4: Ignoring CAC:LTV ratio** — Scaling marketing spend without tracking per-channel CAC wastes money.
- **M5: Vanity metrics** — Traffic and signups without conversion-to-paid tracking hide real unit economics.

## Cohort Analysis Framework

Track unit economics by acquisition cohort to see trends:

```
Cohort: Jan 2026 (100 customers)
Month 0: 100 customers, $10,000 MRR
Month 3: 88 customers, $9,200 MRR (12% logo churn, 4% revenue recovery via expansion)
Month 6: 79 customers, $8,800 MRR
Month 12: 68 customers, $8,500 MRR (net revenue retention: 85% — needs work)

Cohort: Apr 2026 (120 customers, after onboarding improvements)
Month 0: 120 customers, $13,200 MRR  
Month 3: 112 customers, $13,500 MRR (7% logo churn, expansion offsetting)
Month 6: 106 customers, $14,000 MRR (net revenue retention: 106% — improvement!)
```

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **LTV calculation** | Cohort-based with expansion/contraction | Simple formula with gross margin | Revenue × months only |
| **CAC granularity** | Per-channel, fully loaded | Blended only | Marketing spend / signups |
| **Payback accuracy** | Accounts for onboarding costs and ramp | Simple CAC/ARPU | Not calculated |
| **Trend analysis** | Cohort-over-cohort improvement tracking | Point-in-time snapshot | No historical view |
| **Channel economics** | Per-channel CAC with saturation curves | Top 2-3 channels broken out | Single blended number |
| **Actionability** | Specific levers identified with impact estimates | General recommendations | Numbers without context |
| **Presentation** | Visual dashboard with benchmarks | Clean table | Raw calculations |

**28+ = Investment-ready | 21-27 = Needs refinement | <21 = Insufficient depth**

## Cross-Skill References

- **Upstream:** `pricing-model` (ARPU), `financial-model` (cost structure)
- **Downstream:** `budget-allocation` (channel investment), `fundraising-deck` (investor metrics)
- **Parallel:** `kpi-dashboard` (ongoing tracking)
- **Council:** Submit to `council-finance` for benchmark validation
