# KPI Dashboard

Design and maintain executive dashboards that track the metrics that matter for business health and growth.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for key financial metrics and targets
2. Read `.claude/product-marketing-context.md` for growth and product metrics

## Decision Tree: Dashboard Scope

```
Who is the audience?
├── Founders / CEO
│   └── Strategic: ARR, growth rate, runway, NPS, key conversion rates
├── Board / Investors
│   └── Governance: ARR, burn multiple, NRR, LTV:CAC, headcount efficiency
├── Marketing team
│   └── Growth: Traffic, signups, activation, channel CAC, pipeline
├── Product team
│   └── Engagement: DAU/MAU, feature adoption, retention cohorts, NPS
└── Finance team
    └── Financial: MRR, deferred revenue, cash flow, budget vs actual
```

## SaaS KPI Framework

### Tier 1: Must-Track (Weekly)

| KPI | Formula | Benchmark |
|-----|---------|-----------|
| **MRR / ARR** | Sum of active subscription revenue | Growth >10% MoM (early), >5% (growth) |
| **Net Revenue Retention** | (End MRR - New MRR) / Start MRR | >100% (good), >120% (great) |
| **Burn Rate** | Monthly cash decrease | Declining over time |
| **Runway** | Cash / Monthly Burn | >12 months |

### Tier 2: Growth Metrics (Monthly)

| KPI | Formula | Benchmark |
|-----|---------|-----------|
| **CAC** | S&M Spend / New Customers | Improving over time |
| **LTV:CAC** | LTV / CAC | >3:1 |
| **CAC Payback** | CAC / (ARPU × Gross Margin %) | <18 months |
| **Gross Margin** | (Revenue - COGS) / Revenue | >70% |
| **Burn Multiple** | Net Burn / Net New ARR | <2x (good), <1x (great) |

### Tier 3: Product Health (Monthly)

| KPI | Formula | Benchmark |
|-----|---------|-----------|
| **Activation Rate** | Users completing key action / Total signups | >25% |
| **Monthly Churn** | Lost customers / Starting customers | <3% (SMB), <1% (enterprise) |
| **DAU/MAU** | Daily active / Monthly active | >20% (good), >40% (great) |
| **NPS** | % Promoters - % Detractors | >30 (good), >50 (great) |

## Dashboard Design Principles

1. **One page, one story** — Each dashboard should answer one question
2. **Comparison context** — Every number needs context (vs last month, vs target, vs benchmark)
3. **Trend over snapshot** — Line charts > single numbers. Show at least 6 months.
4. **Anomaly highlighting** — Red/yellow/green indicators for off-track metrics
5. **Drill-down capability** — Summary → detail for investigation

## Anti-Patterns to Avoid

- **M5: Vanity metrics** — Traffic without conversion, users without activation, revenue without retention.
- **F4: No targets** — Numbers without targets are just trivia.
- **F8: Too many metrics** — If everything is important, nothing is. Max 10 KPIs per dashboard.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Metric selection** | Metrics aligned to stage and strategy | Common SaaS metrics | Random or vanity metrics |
| **Data accuracy** | Automated, reconciled, trusted source of truth | Mostly automated | Manual, error-prone |
| **Context** | Targets, benchmarks, and trends on every metric | Some context | Numbers in isolation |
| **Update cadence** | Real-time or daily for operational, weekly for strategic | Weekly | Monthly or ad-hoc |
| **Actionability** | Each metric has an owner and action plan | Some ownership | No accountability |
| **Audience fit** | Dashboard designed for specific audience | One-size-fits-all | Over-detailed for audience |
| **Visual design** | Clean, scannable, progressive disclosure | Readable | Cluttered or confusing |

**28+ = Decision-driving | 21-27 = Informational but not actionable | <21 = Misleading or ignored**

## Cross-Skill References

- **Upstream:** All finance skills feed metrics into the dashboard
- **Downstream:** `budget-allocation` (informed by dashboard trends), `fundraising-deck` (investor metrics)
- **Parallel:** `analytics-tracking` (data collection infrastructure)
- **Council:** Submit to `council-finance` for metric selection review
