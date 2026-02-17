# Fundraising Deck

Build compelling investor pitch decks backed by data, narrative, and market insight.

## Context Sync Protocol

1. Read `.claude/finance-context.md` for financials, unit economics, runway
2. Read `.claude/product-marketing-context.md` for market, positioning, traction

## Decision Tree: Deck Type

```
What round are you raising?
├── Pre-seed / Seed
│   └── 10-12 slides. Lead with problem + vision. Traction = early signals.
│       → Focus: Team, market size, unique insight
├── Series A
│   └── 12-15 slides. Lead with traction + unit economics.
│       → Focus: PMF proof, scalable GTM, path to $10M ARR
├── Series B+
│   └── 15-20 slides. Lead with market position + expansion.
│       → Focus: Market leadership, expansion revenue, path to IPO
└── Bridge / Extension
    └── 8-10 slides. Lead with what changed + what capital unlocks.
        → Focus: Specific milestones, capital efficiency, timeline
```

## The 12-Slide Framework

| # | Slide | Content | Time |
|---|-------|---------|------|
| 1 | **Cover** | Company name, one-line description, round details | 10s |
| 2 | **Problem** | Pain point with specificity and magnitude | 60s |
| 3 | **Solution** | Your product and how it solves the problem | 60s |
| 4 | **Market** | TAM → SAM → SOM with bottom-up validation | 45s |
| 5 | **Product** | Key screens/demo, core workflow | 90s |
| 6 | **Traction** | Revenue, users, growth rate, retention | 60s |
| 7 | **Business Model** | Pricing, unit economics, LTV:CAC | 60s |
| 8 | **Go-to-Market** | Acquisition channels, sales motion | 45s |
| 9 | **Competition** | Positioning matrix (not a feature grid) | 45s |
| 10 | **Team** | Founders + key hires, relevant experience | 45s |
| 11 | **Financials** | 3-year projections, key assumptions | 60s |
| 12 | **Ask** | Amount, use of funds, milestones to hit | 30s |

## Slide-by-Slide Best Practices

### Problem Slide
- **Do:** Quantify the pain ("Companies spend $X/year on manual processes that fail Y% of the time")
- **Don't:** Generic industry overview ("The $XB market is growing")

### Market Slide
- **Bottom-up required:** # of target customers × willingness to pay = SAM
- **Top-down optional:** Industry analyst reports for TAM context
- **SOM:** Realistic 3-5 year capture based on growth rate

### Traction Slide
- **Pre-seed:** Waitlist, LOIs, pilot customers, engagement metrics
- **Seed:** MRR, MoM growth, retention cohorts, NPS
- **Series A:** ARR, NRR, CAC payback, channel scalability proof

### Competition Slide
- Use a 2×2 positioning matrix, NOT a feature comparison checklist
- Axes should represent strategic dimensions where you win
- Include indirect competition and status quo

## Anti-Patterns to Avoid

- **F4: Hockey stick without drivers** — Every growth projection needs traceable assumptions
- **F5: Top-down market sizing** — "1% of a $100B market" is not credible
- **F8: Vanity metrics in deck** — Total users without engagement/conversion data
- **M6: Generic positioning** — "We're the Uber of X" without specific differentiation

## Quality Rubric (35 points)

| Dimension | 5 pts | 3 pts | 1 pt |
|-----------|-------|-------|------|
| **Narrative arc** | Problem → solution → proof → opportunity flows naturally | Logical but disconnected | Random slide order |
| **Data backing** | Every claim has specific, verifiable data | Most claims supported | Aspirational statements |
| **Market sizing** | Bottom-up with clear assumptions | Mix of top-down and bottom-up | Top-down only |
| **Unit economics** | LTV, CAC, payback, margins clearly shown | Some metrics present | No unit economics |
| **Visual design** | Clean, consistent, one idea per slide | Readable but dense | Text-heavy slides |
| **Ask clarity** | Specific amount, use of funds, milestones | Amount stated, vague use | No clear ask |
| **Competitive insight** | Unique strategic positioning clear | Feature comparison | No competitive context |

**28+ = Send to investors | 21-27 = Needs coaching | <21 = Not investor-ready**

## Cross-Skill References

- **Upstream:** `financial-model` (projections), `unit-economics` (LTV/CAC), `product-marketing-context` (positioning)
- **Downstream:** `cap-table` (round structure), `budget-allocation` (use of funds)
- **Council:** Submit to `council-finance` for financial claims review
