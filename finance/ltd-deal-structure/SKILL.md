# LTD Deal Structure

Design lifetime deal offers that generate cash without destroying long-term business economics.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for margins, CAC, and cash position
2. Read `.claude/product-marketing-context.md` for positioning and current pricing

## Decision Tree: Should You Do an LTD?

```
Is an LTD right for your business?
├── Need upfront cash for development? → Consider LTD
│   ├── Product is MVP/early? → LTD as validation + funding
│   └── Product is mature? → Probably not worth the dilution
├── Need market validation/feedback? → Consider LTD
├── COGS per user is high and ongoing? → Avoid LTD (unsustainable)
├── Already have strong subscription revenue? → Avoid LTD (cannibalization)
└── Competitors doing LTDs on AppSumo? → Evaluate defensively
```

## LTD Economics

### Pricing Framework

```
LTD Price = Annual Subscription Price × Multiplier

Conservative: 2-3x annual (sustainable if churn is low)
Standard: 3-5x annual (AppSumo sweet spot: $49-$99)
Aggressive: 1-2x annual (cash grab, margin risk)

Break-even calculation:
  If annual plan = $120/year ($10/month)
  LTD at $299 = break-even at 2.5 years
  LTD at $199 = break-even at 1.7 years
  LTD at $99 = break-even at 10 months (risky)

Rule: LTD price should fund the customer for 3+ years of service delivery
```

### Revenue Recognition for LTDs

```
LTD revenue MUST be deferred and recognized over estimated customer lifetime:
  - Conservative estimate: 3 years (36 months)
  - Standard estimate: 5 years (60 months)
  
  $299 LTD with 3-year estimate:
    Monthly recognized revenue: $299 / 36 = $8.31/month
    Deferred revenue at purchase: $290.69
```

### The LTD Flywheel

```
Cash injection → Fund development → Better product → Higher subscription price
     ↑                                                        |
     └── LTD buyers become advocates, reviews, case studies ←─┘
```

## Deal Structure Options

| Structure | Mechanics | Best For |
|-----------|-----------|----------|
| **Simple LTD** | One-time payment, lifetime access to current tier | Simple products |
| **Stacked LTD** | Buy multiple codes for higher tiers (1 code = basic, 3 codes = pro) | Tiered products |
| **LTD + Annual upsell** | Lifetime core access, annual fee for premium features | Products with high COGS features |
| **Limited LTD** | Lifetime access but with usage caps (e.g., 1000 credits/month) | Usage-based products |
| **Sunset LTD** | Lifetime access to v1, pay for v2 | Products planning major rewrites |

## Platform Comparison

| Platform | Commission | Audience | Best For |
|----------|-----------|----------|----------|
| **AppSumo** | 60-70% (first deal) | 1M+ deal seekers | Maximum volume, brand awareness |
| **PitchGround** | 50-60% | Similar to AppSumo | Alternative if AppSumo rejects |
| **Self-hosted** | 0% | Your audience | Existing user base, higher margin |
| **Product Hunt** | 0% | Tech early adopters | Launch day LTD special |

## Cap Strategy

| Element | Recommendation |
|---------|---------------|
| **Total units** | Cap at 2-5% of TAM to avoid subscription cannibalization |
| **Time window** | 2-4 weeks maximum (urgency drives conversion) |
| **Tier limits** | Different caps per tier (more basic, fewer pro) |
| **Exclusions** | Exclude enterprise features, dedicated support, API access |

## Anti-Patterns to Avoid

- **F13: Recognizing LTD revenue immediately** — Must defer and amortize.
- **F3: Over-engineering LTD structure** — Keep it simple: one price, clear value, obvious limitations.
- **M14: LTD cannibalization** — If existing subscribers can buy LTD and cancel subscription, you're losing money.
- **F15: Unsustainable COGS** — If each user costs $5/month to serve, a $99 LTD funds only 20 months.

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Economic viability** | Break-even analysis with COGS modeling | Basic price vs cost comparison | No cost analysis |
| **Cap strategy** | Unit caps with cannibalization modeling | Caps set but not modeled | No caps |
| **Revenue recognition** | Proper deferral schedule documented | Acknowledged but not calculated | Recognized at purchase |
| **Upsell path** | Clear path from LTD to subscription for premium features | Some upsell considered | No upsell strategy |
| **Platform selection** | Commission vs volume trade-off analyzed | Platform chosen without analysis | Default to AppSumo |
| **Communication** | Clear terms, limitations, and expectations set | Basic terms | Ambiguous promises |
| **Exit strategy** | Plan for eventually ending LTD program | Timeline set | No exit plan |

**28+ = Launch-ready | 21-27 = Needs financial validation | <21 = Risk of unsustainable commitment**

## Cross-Skill References

- **Upstream:** `pricing-model` (subscription pricing), `unit-economics` (per-user costs)
- **Downstream:** `revenue-recognition` (LTD deferral), `launch-strategy` (LTD launch plan)
- **Parallel:** `copywriting` (LTD landing page), `email-sequence` (LTD announcement)
- **Council:** Submit to `council-finance` for sustainability review
